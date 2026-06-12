---
title: "getting totem to play an isp file"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by Dapman01 on 2007-10-23
How do I get totem to play an iso that I ripped from a dvd
(I'm using 7.10 if it matters)

---

### Post by Dapman01 on 2007-10-24
so I mounted the iso image and got it to read and got the sound working perficty, but the video is all jarbled.  it's like pink anyway to fix that

---

### Post by Dapman01 on 2007-10-24
file:///home/patrick/Desktop/Screenshot.png
there's a screenshot

---

### Post by mommebu on 2007-11-21
While in earlier versions of ubuntu totem-xine was able to play iso files it seems to fail now if you load the image from the menu, however from terminal it worked for me using:
totem-xine dvd://absolute/path/to/your/iso/file.iso &
This is without mounting the image.

Strange that the newer version lost the feature from the menu though...

---

