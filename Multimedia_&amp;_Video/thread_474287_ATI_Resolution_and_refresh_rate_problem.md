---
title: "ATI Resolution and refresh rate problem"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by criscross79 on 2007-06-14
Hi there,

I am a very experienced windows user, but I am brand new to Ubuntu and Linux and I now know what it feels like to be one of the technologically challenged people who I got frustrated at when I used to work on a help desk :D

Anyway,  the problem I am having is that my screen resolution originally listed list only 640x480, 800x600, and 1024x768. The refresh rate is set to a lousy 60hz (ouch, my eyes)

I found the ATI driver under the Restricted Drivers Manager and added that. Now I have 960x720, and 864x 648 resolution added to the list, but the refresh rate is still 60hz.

besides installing the ATI driver through the Restricted Driver Manager,  I have tried doing the different install suggestions that I've found on here with no luck,  Maybe I'm doing it wrong.

I am using a a raedon X700 video card with a 21" CRT monitor

Any suggestions?

Thanks

Chris

---

### Post by Ek0nomik on 2007-06-15
Maybe this will bring you some luck for resolutions:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

In regards to refresh rate, you will probably need to edit your xorg.conf file.  I would look at the manual (online or in real life, whichever you prefer) for your monitor.  This way you can find out the vertical and horizontal rates, and plug them into your xorg.conf file.

Make sure to backup your file though!

*Backup*

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

*Edit*

```
gksudo gedit /etc/X11/xorg.conf
```

---

