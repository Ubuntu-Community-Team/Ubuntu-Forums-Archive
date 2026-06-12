---
title: "[SOLVED] Looking for Photo Album Scrapbook Photo Layout type program"
date: 2008-05-28
forum: Multimedia Software
---

### Post by mocha on 2008-05-28
I'm having such a difficult time finding a tool to make pages of photos like for a photo album.  I want to take some photos and put them on a US Letter sized page and then put some text at the top of the page.  In a way I guess you could call it a montage of photos.  I was hoping to find some prog to make this easy.  I know how to do it manually in Gimp but it's very time consuming having to copy/paste, scale, new layer, etc etc...  Maybe nothing like this exists, but I figured it's worth asking.  Thanks.

---

### Post by kaboodle_fish on 2008-05-28
Try photoprint which is in the repos 

I think that is what you are looking for

edit: Here you go: [http://packages.ubuntu.com/hardy/photoprint](http://packages.ubuntu.com/hardy/photoprint)

---

### Post by theophiles on 2008-05-28
You could try Scribus. It is the best open-source desktop publishing program (which it sounds like you want) about which I know and is in the repositories.

---

### Post by mocha on 2008-05-28
> **theophiles said:**
> You could try Scribus. It is the best open-source desktop publishing program (which it sounds like you want) about which I know and is in the repositories.

Scribus does look like the solution.  I started browsing their wiki and it seems like some folks made some scripts to do what I wanted.

---

### Post by mocha on 2008-05-29
In case anyone finds this post in the future; I ended up using Scribus and a script on their wiki:

[http://wiki.scribus.net/index.php/Automatic_import_of_images:_Versions_not_requiring_Tkinter]("http://wiki.scribus.net/index.php/Automatic_import_of_images:_Versions_not_requiring_Tkinter")

This is a fairly slick method to quickly make "photo album" pages of photos with text at the top if you like.  I modified the scripts to use US Letter size paper in Landscape format.  You can change the scripts to whatever papersize and layout you like, just search the text for PAPER_LETTER and LANDSCAPE next to it and change those to whatever you want (A4, PORTRAIT, etc).  The first script imports 4 or 6 images and the other script imports 8 images.  Run the scripts within Scribus, menu "Script - Execute Script.."

Scribus doesn't print anything on my printer.  There's a number of bugs filed for this on their bug tracker [http://bugs.scribus.net]("http://bugs.scribus.net") also see [https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442]("https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442")

Exporting the file as a PNG (menu "File" - "Export" - "Save as Image..") and then printing in GIMP works fine though.

---

