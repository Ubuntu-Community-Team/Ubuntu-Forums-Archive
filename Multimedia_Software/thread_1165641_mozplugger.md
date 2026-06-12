---
title: "mozplugger"
date: 2009-05-20
forum: Multimedia Software
---

### Post by celem on 2009-05-20
Has anyone been successful with installing mozplugger for firefox? I have the plugin installed but it does not display the patent office TIFFs. I used to have this working for 8.04 on a different machine.

---

### Post by celem on 2009-05-22
Solved by:
1. Install mozplugger
2. install imagemagick
3. sudo gedit /etc/mozpluggerrc and change as follows:
...
image/tiff:tiff,tif:TIFF image
	**exits: display -window $window -backdrop "$file"**
image/x-tiff:tiff,tif:TIFF image
	exits: display -window $window -backdrop "$file"
...

Now works like a charm!!

---

