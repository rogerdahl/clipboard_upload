Clipboard Upload
================

Upload files or data from your computer to your website with a single click
by using the clipboard.


Usage
-----

Examples
~~~~~~~~

To share a couple of files with someone:

* Select the files in a file manager and *Copy*.
* Run clipboard_upload.py.
* *Paste* the HTTP links now in the clipboard into an email or instant message.

To upload an image:

* *Copy* some image data to the clipboard, for instance by pressing the Print
  Screen key.
* Run clipboard_upload.py
* *Paste* the HTTP link now in the clipboard. It will point to a generated image
  file on the web server (.png by default).

To upload some text:

* In a text editor, select the text and *Copy*.
* Run clipboard_upload.py
* *Paste* the HTTP link now in the clipboard. It will point to a .txt file on
  the web server.


Install
-------

This script works only on Windows.

* Download the clipboard_upload.py file and store it somewhere convenient.
* Create a shortcut to the .py file by dragging it onto the Windows start button.
* Download and install Python from http://www.python.org/getit/.
* Download and install Python Image Library (PIL) from
  http://www.pythonware.com/products/pil/.
* Download and install PyCrypto. It's easiest to install from the precompiled
  binaries at http://www.voidspace.org.uk/python/modules.shtml#pycrypto.
* Download and install Paramiko from http://www.lag.net/paramiko/.
* Download and install PyWin32 from
  http://sourceforge.net/projects/pywin32/files/.
* Create a folder on your web server that is accessible through the web.
* Create a user that has permissions to store files in that folder (or use an
  existing user, but note that the script is required to hold the password for
  this user in clear text).
* Open the clipboard_upload.py file in a text editor and edit the configuration
  settings. Notes on the settings are in the file.


Tips
----

Common ways of getting image data into the clipboard are:

* Print Screen: Get a screenshot of the entire screen.
* Alt + Print Screen: Get a screenshot of the program that currently has focus.
* Windows 7 Snipping Tool: Get a screenshot of any area of the screen.
* Right click an image in Firefox and select *Copy Image*.

Implementation
--------------

Strategy
~~~~~~~~

* Use the clipboard as a staging area for uploading to a web server. After the
  upload, replace the contents in the clipboard with links to the uploaded data.

* Upload regular files by copying them to the clipboard in a file manager. For
  regular files, create files on the web server with names matching the ones in
  the clipboard (overwriting any existing files with those names)

* Upload image and text data by dynamically creating files on the web server
  with randomly generated names that will not overlap.

* Use SFTP to upload the data.

* Upload to a folder on the web server that is available through HTTP.


Todo
----

* Support HTML fragments.
* Support 3rd party file hosting services.
