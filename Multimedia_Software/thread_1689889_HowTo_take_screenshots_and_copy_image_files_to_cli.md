---
title: "HowTo: take screenshots and copy image files to clipboard from the command line"
date: 2011-02-17
forum: Multimedia Software
---

### Post by cheshirekow on 2011-02-17
Here is a quick tutorial and a pair of scripts to help you take screenshots (of any region on the screen) and have those go straight to your clipboard. As an intermediate step, I solve the problem of copying an image file to the gnome-clipboard so that it can be pasted in another program.

First, install imagemagick python, and pygtk

```
sudo apt-get install imagemagick python pygtk
```

Now save the following script somewhere as imgclip.py. This is a simple python script which takes an image file and puts it in the gnome-clipboard.

```
#! /usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk
import os
import sys

def copy_image(f):
    assert os.path.exists(f), "file does not exist"
    image = gtk.gdk.pixbuf_new_from_file(f)

    clipboard = gtk.clipboard_get()
    clipboard.set_image(image)
    clipboard.store()


copy_image(sys.argv[1]);
```

To use it:

[HTML]python /path/to/imgclip.py filename.png[/HTML]

Now save the following script somewhere as screenshot.sh

```
#!/bin/bash

#directory to put the screenshot file in
#note that files in /tmp/ are deleted automatically on boot
directory='/tmp/'

#prefix for filename to be created
prefix='screenshot';

#timestamp appended to filename
timestamp=`date '+%d-%m-%y-%N'`;

#extension to save the image as
extension='.png';

#path to the imgclip script (also posted in this howto)
imgclip='/your/path/to/imgclip.py';

#the filename to save the screenshot as
file="$directory$prefix-$timestamp$extension";

#call imagemagick utility to take the screenshot... 
#this will turn the cursor into a cross and you can select an 
#area of the screen which is turned into an image
import $file

#call imgclip script to copy that image to the clipboard
python $imgclip $file

```

Change the appropriate variables to meet your needs. In particular, you must set the path to imgclip.py. Now just make sure that you have run permissions for screenshot.sh by running the following

```
chmod +x /your/path/to/screenshot.sh
```

and then run the script from the shell

```
/your/path/to/screenshot.sh
```

I've bound this script to the super+S hotkey and the super+alt+button1 mouse click event in compiz for quick use.

---

### Post by jquintanaw on 2011-05-19
use only this script 
#! /usr/bin/python
import pygtk
pygtk.require('2.0')
import gtk
import os
import sys

def copy_image(f):
    print f
    assert os.path.exists(f), "file does not exist"
    image = gtk.gdk.pixbuf_new_from_file(f)
    clipboard = gtk.clipboard_get()
    clipboard.set_image(image)
    clipboard.store()

path='/media/Datos/tmp/'

filelist = os.listdir(path)
filelist = filter(lambda x: not os.path.isdir(path+x), filelist)
print filelist
imagen = max(filelist, key=lambda x: os.stat(path+x).st_mtime)
copy_image(path+imagen)


-----------------------------------

please set your path directory 
and set the script with chmod +x

afterdate include in compizconfig in lauch application your script and path 
[IMG]file:///tmp/moz-screenshot.png[/IMG][ATTACH]192681[/ATTACH]

---

### Post by oller.mauser on 2012-10-27
When I use Imagemagick I always get black borders around the screenshot, which i dont want. 
- is there a fix for that?

Alternatively I tried jquintanaw's sollution. Copy-Pasted the script, changed the path and included in Compiz. But I didnt work. I tried to launch the script from terminal and got the following Error:

  File "/home/simplicius/imgclip1.py", line 9
    print f
        ^
IndentationError: expected an indented block

- what is wrong here?

p.s. tried indenting print f. That brought me a new Error:

Traceback (most recent call last):
  File "/home/simplicius/imgclip1.py", line 10, in <module>
    assert os.path.exists(f), "file does not exist"
NameError: name 'f' is not defined

---

### Post by nothingspecial on 2012-10-27
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Closed.

---

