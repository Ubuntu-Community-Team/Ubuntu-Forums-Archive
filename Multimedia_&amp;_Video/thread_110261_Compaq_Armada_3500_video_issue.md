---
title: "Compaq Armada 3500 video issue"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by plexroth on 2005-12-30
Hi folks. I'm a grateful newbie to Ubuntu and an 18-month user of the Gentoo.  I was extremely tickled with how easily Ubuntu Breezy installed on my allegedly obsolete Compaq Armada 3500. However, I have a slight issue w/ the monitor. The desktop does not cover the entire screen. There is a 1.5 inch black border around the desktop.

My question is this: how do I set up xorg and/or the driver to use the entire screen?

here are the specs: 

(lspci reveals) - 0000:00:08.0 VGA compatible controller: Chips and Technologies F69000 HiQVideo (rev 64)

and the xorg setup is: 

Section "Device"
        Identifier      "Chips and Technologies F69000 HiQVideo"
        Driver          "chips"
        BusID           "PCI:0:8:0"


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-65
        VertRefresh     43-85

I look forward to hearing your solutions! 

Ubuntu is a beautiful thing.

---

### Post by qb4ever on 2006-01-03
open xorg.conf with your favorite editor and change the bolded text to the resolution  you would normally set it at:

Section "Screen"

Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "**1024x768"**
EndSubSection
EndSection

---

### Post by MonkeyBoy on 2006-05-03
I am probably posting a bit late to help but will try anyway.

I had exactly the same problem and found a couple of solutions-

It seems that Ubuntu will try to recommend 24bit colour during the install but this is too much for the Armadas little lcd screen.  If you type  ```
sudo dpkg-reconfigure xserver-xorg
``` you can go through the same setup screens you had during the install.  Just keep hitting enter until you get to screen resolution choices.  Make sure you have 1024*768 selected then go on to where it asks about colour resolution.  Select 16bit and then finish.  You may need to reboot.

If this doesn't work you could try an even lower colour resolution or hold down function and tap T which, on an Armada 3500, should stretch your screen but looks a bit nasty.

---

