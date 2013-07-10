# Riker README

## 1.0  	Understanding Riker

### 1.1		What is Riker?

Riker is a static site generating CMS.

Through the Riker web interface, a user can create, edit and delete pages. Pages are saved as text files in a source directory. Riker will build a static version of the website using the files in the source directory.

Riker avoids using a database, instead saving data directly to the file system. As a result, a user can create, edit and delete content through the file system without needing to use the web interface. This also allows the entire website to be versioned using a version control system like Git.

### 1.2		How does Riker work?

There are three important concepts that underlie Riker: definitions, layouts and content files.

#### 1.2.1	What is a definition?

A definition is a file that defines a type of page that a user can create. A Riker administrator (that is, a person with direct access to the file system where Riker is stored) is free to create any definition that they like.  A definition contains a small amount of metadata at the beginning (the name of the definition and its version) and then lists the content items that exist within this definition.

For example, consider a definition for an event page. In this case, the Event might have three content items: the start time, the end time and a location. In the Event definition file, the user will list each content item, setting out its name, its type and whether the item is 'single' or 'multiple'. If a content item is set to be 'multiple', it means that a page can have multiple items of this type of content. An example of a content item that will often be set to 'multiple' is an image.

The current list of data types is as follows: block, datetime, email, image, map, price, text.

#### 1.2.2	What is a layout?

A layout is a file that tells Riker how to display the data in a page. Layouts are primarily written in HTML but can use embedded Ruby to include data or to perform operations such as loops.

Layouts include references to the data defined in the definition. When Riker builds a particular page, it extracts the data from the relevant content file and inserts it into the correct location in the layout. The output is then saved as HTML. A layout does not need to use all of the data contained in a content file.

Because they are closely related, a layout must specify the definition that it relies upon.

#### 1.2.3	What is a content file?

A content file is a text file containing the user-generated content for a page. If the user uses the web interface, Riker will allow the user to edit the piece of data using appropriate controls (eg. date pickers, image pickers, etc). If a content item has been listed as a 'multiple' in the definition, Riker will provide an interface to easily allow the user to add additional items.

While the web interface may be preferred for editing content served on a remote computer, a user is always free to change the content by directly editing the content file. Changes to a content file will not be reflected in the website until it is rebuilt.

A content file must specify the definition and the layout that it uses.
