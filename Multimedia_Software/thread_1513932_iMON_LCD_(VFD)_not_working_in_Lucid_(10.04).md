---
title: "iMON LCD (VFD) not working in Lucid (10.04)"
date: 2010-06-20
forum: Multimedia Software
---

### Post by hbchrist1 on 2010-06-20
I have an Antec Fusion Black media centre PC, which included a VFD display. lsusb shows the id as 
```
ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

It has previously worked on Ubuntu 8.04. However, after I installed 10.04, it does not work. (I did a fresh install of the system, removing the old ubuntu and starting again from scratch.)

I followed the instructions in [_this guide for Karmic 9.10_]("https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10"), to install lirc and lcdproc. 

I found a thread explaining that there was a timing bug which leads to corrupted text on the imon in the ubuntu 10.04 beta. This is not my problem: my problem is the total and utter absence of text. 

The screen is completely lit up, just like it was after I first connected it, before installing any software. There are no error messages: both of the following commands yield only [OK] messages. 

```
sudo /etc/init.d/LCDd restart
sudo /etc/init.d/lirc restart
```

The volume knob does not seem to work either. When I enter 
```
sudo irw
```
and turn the knob, nothing happens. 

Any help, pointers or ideas would be very gratefully received.

---

### Post by Bl4deRunner on 2010-06-20
You'll find help here:
[http://ubuntuforums.org/showthread.php?t=1391881](http://ubuntuforums.org/showthread.php?t=1391881)

Everything works, except the volume knob on the front of my Antec Veris Fusion.
Well, the know DOES work, as I can tell when I test it with IRW, but somehow it's not mapped yet to ubuntu's soundmixer.

I'm about to find that out. My guess is that it's in the LIRC config, so I'm trying to understand what's going on here:

[http://ubuntuforums.org/showthread.php?t=1468228](http://ubuntuforums.org/showthread.php?t=1468228)

---

### Post by hbchrist1 on 2010-06-26
Thanks for the pointer to that excellent thread. As it turns out, I have an LCD display, not a VFD #-o .

---

### Post by Spr0k3t on 2010-06-26
I saw the 15c2:ffdc and was just about to point out the imonlcd driver would be best.  To give you some extra information, [this is a great resource]("http://www.mythtv.org/wiki/Imon") to go through.  Keep in mind, most of the instructions on how to set up the LCD is out of date.

---

