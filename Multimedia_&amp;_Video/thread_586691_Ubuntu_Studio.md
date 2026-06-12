---
title: "Ubuntu Studio"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by tom.m.berry on 2007-10-22
hello,
 
i've just installed gutsy and want to add studio to it, how would i go about doing so?

---

### Post by frefactory on 2007-10-22
Hi there,

Make sure you have the repositories for Ubuntu Studio enabled in your software-sources (you know, menu : SYSTEM - ADMINISTRATION - SOFTWARE SOURCES).

Then open a terminal window and do as follows : 

**sudo apt-get install ubuntustudio-desktop ubuntustudio-graphics ubuntustudio-video ubuntustudio-audio**

and you're all set.

---

### Post by tom.m.berry on 2007-10-23
thank you very much, now as soon as i can figure out why jack isn't producing any sound (which i'm sure i'll find out quicker if i can stop messing around with the cube and the super e). :)

---

### Post by Drunky on 2007-10-25
A couple of guides for Jack:

Ubuntu specific:
[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

via 64Studio:
[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

and finally an old article from Linux Format magazine:
[http://www.linuxformat.co.uk/wiki/index.php/Audio_production_-_JACK](http://www.linuxformat.co.uk/wiki/index.php/Audio_production_-_JACK)

I hope this helps.

---

