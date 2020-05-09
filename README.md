# dpsprep

A tool to convert djvu files to pdf, keeping OCR text and bookmarks

## How To Run

Required packages:

+ Install ruby (this is for Ubuntu 19.1, find one for your OS): https://gorails.com/setup/ubuntu/19.10#ruby-rbenv
+ sudo apt install libmagickwand-dev
+ gem install iconv
+ gem install pdfbeads
+ sudo apt install pdftk-java
+ sudo apt install djvulib
+ sudo apt install djvu2hocr

To run the script, create a python virtual env and install requirements.txt:

+ sudo apt install python2-minimal
+ virtualenv -p /usr/bin/python2.7 venv
+ source ./venv/bin/activate
+ pip install -r requirements.txt
+ python dpsprep.py SOURCE_FILE_PATH DEST_FILE_NAME  
(e.g. python dpsprep.py tmp/Suomen_Mestari_3.djvu Suomen_Mestari_3.pdf) 

## OLD ORIGINAL README FROM https://github.com/kcroker/dpsprep

dpsprep
----------------------------------------------------------

Copyright(c) 2015 Kevin Arthur Schiff Croker
GPL v3

This tool implements a suite of procedures to create a DJVU to PDF converter which preserves OCR text and bookmarks.  
I wrote this with the specific intent of converting ebooks in the DJVU format into PDFs for use with the fantastic (but pricey) 
Sony Digital Paper System.

djvu technology is strikingly superior for many ebook applications, yet the Sony Digital Paper System (rev 1.3 US)
only supports PDF technology: this is because its primary design purpose is not as an ereader.  The device, however, 
is quite nearly the **perfect** ereader.

Unfortunately, all presently available djvu to pdf tools seem to just dump flattened enormous TIFF images.  This is ridiculous.  
Since PDF really can't do that much better on the way it stores image data, a 5-6x bloat cannot be avoided.  However, none of the 
existing tools preserve:

* the OCR'd text content
* Table of Contents or Internal links

This is kind of silly, but until Sony's Digital Paper, there was no need to move functional DJVU files to PDFs. 
In order to make workable PDFs from djvu files for use on the Digital Paper System, I have implemented in one location the following 
procedures detailed here:

By automating the procedure of user zetah for extracting the text and getting it in the correct locations:
http://askubuntu.com/questions/46233/converting-djvu-to-pdf (OCR text transfer)

By implementing the procedure of user pyrocrasty for extracting the outline, and putting it into the PDF generated above:
http://superuser.com/questions/801893/converting-djvu-to-pdf-and-preserving-table-of-contents-how-is-it-possible (bookmark transfer)

NOTE 1: this script requires many installed toolsuites: see the above links for the requisite packages
NOTE 1.5: you will need the sexpdata Python module.  It is provided in Ubuntu under the package python-pyparsing
NOTE 2: pdfbeads is a Ruby package.  "gem install" on an Ubuntu system will require further packages: libmagickcore-dev libmagickwand-dev