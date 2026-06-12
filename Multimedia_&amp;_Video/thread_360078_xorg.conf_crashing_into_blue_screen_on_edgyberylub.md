---
title: "xorg.conf crashing into blue screen on edgy/beryl/ubuntu kernal 2.6.17-11-generic"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by afd on 2007-02-12
Ok, so I'm a noob and am having mad difficulty with ubuntu edgy.
I'm gonna start with what I bought (all through + references for compliance from ubuntuforums.org :D)  -

Intel Dual core 6300 @1.86ghz
ABIT IL9
250GB SATA HDD, 8mb
1GHZ DDR2 800Mhz, PC2-6400
Leadtek Winfast Geforce7600GS 256Mb DDR2 PCI-E
22" Video7 V7L22WD (1680x1050) 5ms, 700:1

I'm running Edgy 6.10 on the latest kernal update (I think I'm on 2.6.17.11-generic), I'm also trying beryl and have been alright with it until the last kernal update through the gui prompt on the desktop.

My current problem is I have to keep deleting the xorg.conf file (which I have tried replacing with backups) as my boots end up in a MS style blue screen and after reporting the details of the error (involving xorg.conf not starting/X not starting).  Deleting this file using 

sudo rm /etc/X11/xorg.conf

lets me back into the gui desktop next boot but my monitor resolution is only capable of 1680x1050 and it's trying (and won't allow me to change it) to run at 1600x1200!  the refresh rate in the screen res gui is also stuck at 66hz and changes to either of these cause a log out and ubuntu user/pass screen to come up ](*,)  outside of ths lot I'm having a few config problems too including dvd & mp3 playback (but only sometimes!)

would really like to stick with ubuntu and believe the future is most definately open source, but need to find my feet a bit.

Please help!

afd

---

### Post by eapache on 2007-02-13
Can you print the x error you get? Knowing where it fouls up would help...

---

### Post by afd on 2007-02-13
OK, so when it fails to boot properly after playing with drivers and not succeeding the blue screen spits:

FATAL: Error running install command for nvidia
(EE) NVIDIA : failed to load NVIDIA kernal module!
(EE) NVIDIA (0) ***Aborting***
(EE) Screen(s) found, but none have usable sonfiguration

It seemed to screw up after the last kernal update I got.

---

### Post by dcstar on 2007-02-13
> **afd said:**
> OK, so when it fails to boot properly after playing with drivers and not succeeding the blue screen spits:

FATAL: Error running install command for nvidia
(EE) NVIDIA : failed to load NVIDIA kernal module!
(EE) NVIDIA (0) ***Aborting***
(EE) Screen(s) found, but none have usable sonfiguration

It seemed to screw up after the last kernal update I got.

There seem to be many posts in the forum referring to nvidia problems after this kernel upgrade, you may want to look at some of them for possible solutions.

---

### Post by afd on 2007-02-14
Ok, so I've read through some nvidia driver threads and have tried the envy route only to be confronted with another blue screen (same error message I think).

So got onto the easy ubuntu wagon and that didn't work either.  I tick all the approriate boxes and I get this error (after a bit of what seems like it's working away):

"you have chosen to install items that might be illegal in your country.
Click cancel to review these items or
Click 'OK' to install
Please review the following items:

Codes:blahblahblah
libdivcss:blahblahblah
Flash:blahblahblah
Java:blahblahblah
RAR:blahblahblah
Fonts:blahblahblah
Nvidia Legacy: blahblahblah

CANCEL            OK"

and whichever I press it just acts like it's done when it hasn't really done anything.

as I said before I don't have an xorg.conf file just to get the computer to boot gnome and get into ubuntu's desktop... weird!

any advice?

---

