---
title: "How to save a web image from command line?"
date: 2010-06-09
forum: Multimedia Software
---

### Post by tarahmarie on 2010-06-09
Hi!

I thought this was a DE problem, but it's really an image saving problem.

[http://fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=](http://fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=)

That URL dynamically generates an image of the night side of the world.  How do I save it as a jpg somewhere on my puter using a script?  I can wget, but it gets saved as a .evif, which is totally useless.  I can right-click on the image in a browser and use the context menu to save it as a jpg, but I want this process automated.  How can I DL this image and save it as a jpg? GIMP's CL options don't include the capacity to save/convert this image, though it's possible from teh GUI. ImageMagick won't read this dynamic URL. What do I do?

---

### Post by DaithiF on 2010-06-09
Hi,
```
$ wget -O - "http://fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynim
g=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd=" | convert - earth.jpg
```

---

### Post by tarahmarie on 2010-06-09
My solution:

#!/bin/bash
wget -A earth.jpg "www.fourmilab.ch/cgi-bin/Earth?img=learth.evif&imgsize=600&dynimg=y&opt=-n&lat=&lon=&alt=&tle=&date=0&utc=&jd="
mv /home/tarahmarie/Earth\?img\=learth.evif\&imgsize\=600\&dynimg\=y\&opt\=-n\&lat\=\&lon\=\&alt\=\&tle\=\&date\=0\&utc\=\&jd\= /home/tarahmarie/Pictures/Wallpaper/Dynamic/earth.jpg

---

### Post by Jinger on 2010-06-09
I give you an advice. If you want to download all pictures that there are on a web site you can use this command:

```
wget -r --level=2 -A gif,jpg http://www.example.com/

```

Where "www.example.com" must be changed with the link and you have to exchange "level=X" with a number like two. 

 
See you later

---

