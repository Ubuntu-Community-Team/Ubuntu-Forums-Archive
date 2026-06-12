---
title: "Tv-out totally messed up my system"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by jellystones on 2007-12-26
So yesterday I had two friends (huge Windows fans) over and I've always been preaching to them how ready for mainstream Ubuntu is.

We were going to watch a movie so I hooked up an s-video cable to my laptop and pressed FN+F8 (which enables tv-out on my dell 640m laptop). 

I then went to disable my lcd screen, and as I was clicking OK the computer totally froze (to my friends delight) and restarting the computer I get failure messages


[http://img241.imageshack.us/img241/5236/26122007015wx8.jpg](http://img241.imageshack.us/img241/5236/26122007015wx8.jpg)

This must be some configuration file issue that I need to change, but I have no idea where to begin looking.

---

### Post by Nimda1000 on 2007-12-26
Did you change it back again?  Try hitting Control-Alt-Backspace? that worked for me in a similar situation, I think what you are seeing is not your primary display output.

---

### Post by jellystones on 2007-12-26
> **Nimda1000 said:**
> Did you change it back again?  Try hitting Control-Alt-Backspace? that worked for me in a similar situation, I think what you are seeing is not your primary display output.

Yes I got it working again, I did some digging around in xorg.conf and found this command:

sudo dpkg-reconfigure -phigh xserver-xorg

after running this, It restored my xorg.conf file to a working one.

---

