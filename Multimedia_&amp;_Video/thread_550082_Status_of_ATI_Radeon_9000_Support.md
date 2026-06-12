---
title: "Status of ATI Radeon 9000 Support?"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by Roscoe on 2007-09-13
I'm considering installing 7.04 on my laptop that includes a Radon 9000. I see that the latest proprietary ATI driver does not support the 9000.

Does 7.04 include an open source driver for the 9000?

Does it support 3D?  Can I play Quake 1/2/3? Can I run Compiz?

Thanks a lot

---

### Post by Matt Yun on 2007-09-13
I am using an ATI Radeon Mobility 9000 (R250) as well.  The open-source "ati" driver works better than the fglrx binary.  OpenArena (ie. gpl'd Quake3) and other 3D games play fine.  However, forget Compiz/Fusion; while you can run it, it slows the system down significantly.

---

### Post by qamelian on 2007-09-13
> **Matt Yun said:**
> I am using an ATI Radeon Mobility 9000 (R250) as well.  The open-source "ati" driver works better than the fglrx binary.  OpenArena (ie. gpl'd Quake3) and other 3D games play fine.  However, forget Compiz/Fusion; while you can run it, it slows the system down significantly.

That's funny. I run Compiz-Fusion on my laptop with the ATI Radeon Mobility 9000 and the open-source driver and find it significantly faster than running with Compiz-fusion turned off. Dragging a windows across the screen, for example, is visibly jerky without Compiz, but very smooth and speedy with Compiz turned on.

---

### Post by w4ett on 2007-09-13
The RV250 based chipsets work quite well with the xorg-driver-ati...you should see a 800-900 Fps rating in glxgears......My 9200 (RV280) runs compiz well.and has full 3D capability.

---

### Post by whatever on 2007-09-13
> **Roscoe said:**
> Does 7.04 include an open source driver for the 9000?

Does it support 3D?  Can I play Quake 1/2/3? Can I run Compiz?
"yes" is the answer to all these questions :)

---

### Post by Caydel on 2007-09-13
Hello.

I am trying to get Feisty running on an older Toshiba Satellite A70. For some reason, it is detecting the card (a Radeon Mobility 9000IGP) as a 9100:

```

brian@linux:~$ lspci grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] 
```

While 3D *is* working, it really feels like it isn't giving it all it's got. glx-gears gives ~700 FPS, and games will not get up to a playable framerate even at the lowest settings - so far I've tried OpenArena and Urban Terror.

Currently, I am using the open source 'ati' driver, because I've heard it gives better performance than the proprietary ATI drivers.

I am sure there has be be more performance gained from this card. How can I troubleshoot what is slowing it down, making it detect as the wrong card? How can I eek better performance out of it?

I've heard that the MESA3D drivers work well with this card. Can someone confirm?

Thanks in advance for any help!

---

### Post by w4ett on 2007-09-13
> **Caydel said:**
> Hello.

I am trying to get Feisty running on an older Toshiba Satellite A70. For some reason, it is detecting the card (a Radeon Mobility 9000IGP) as a 9100:

```

brian@linux:~$ lspci grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] 
```

While 3D *is* working, it really feels like it isn't giving it all it's got. glx-gears gives ~700 FPS, and games will not get up to a playable framerate even at the lowest settings - so far I've tried OpenArena and Urban Terror.

Currently, I am using the open source 'ati' driver, because I've heard it gives better performance than the proprietary ATI drivers.

I am sure there has be be more performance gained from this card. How can I troubleshoot what is slowing it down, making it detect as the wrong card? How can I eek better performance out of it?

I've heard that the MESA3D drivers work well with this card. Can someone confirm?

Thanks in advance for any help!

The ID mismatch is not really a problem....the 9000/9100 card share the same GPU the RV250...

The open source xorg-driver-ati is the correct driver for your chipset due to the fact that AMD/ATI have chosen not to support the legacy cards (those under the 9500).....

The performance you are seeing with 700 fps is perfectly normal with that chipset and driver.  Unless ATI  includes their earlier cards in the upcoming driver release or releases new drivers compatible with xorg7.2/7.3 for the legacy cards, you will have to be content with these performance figures.

---

### Post by Caydel on 2007-09-13
Thank you for your reply. So, in short, this 3D card is useless under Linux?

The poster above claimed that he could run OpenArena and other similar programs just fine... I would love to get that kind of performance.

Any thoughts on the MESA driver? I am calling it a night soon, but I will dig up the thread where they discussed using it for this card.

---

### Post by w4ett on 2007-09-14
> **Caydel said:**
> Thank you for your reply. So, in short, this 3D card is useless under Linux?

The poster above claimed that he could run OpenArena and other similar programs just fine... I would love to get that kind of performance.

Any thoughts on the MESA driver? I am calling it a night soon, but I will dig up the thread where they discussed using it for this card.

Well....I use the 9200 card (not supported by fglrx either, btw) and have good luck with it.....I get 800+ fps out of it and have full use of compiz  and also Google Earth......I'm not a gamer and it fills my requirements...so as you can see I'm not the best to advise on the game useability.  

Also considering these chipsets are getting a bit long in the tooth, if you want gaming capability, the only sensible choice in linux would be a Nvidia card/chipset, or to buy a card compatible with the newest ATI drivers that were released just a few days ago, and that is also compatible with your motherboard.

---

### Post by Caydel on 2007-09-14
Hmm....

It's a laptop, unfortunately, so upgrading the video card is a bit of an issue.

Anyone else think this is a lost cause? I can understand if it is, but would still love to hear better news!

Brian

---

### Post by Caydel on 2007-09-15
Anyone else have any ideas?

---

### Post by shil on 2007-10-10
i'm using the ati open source drivers (for the ati radeon 9000) and it starts ok and has a nice performance but white borders start to appear, next are the windows and eventually the background goes all white.

if you have a working configuration for the Compiz-Fusion please post it here so i can compare the flags (can't post my own right now) 

thanks

edit: just tried it on gnome and it's working great, so it's just a kde related problem

---

### Post by cogitordi on 2007-10-21
> **shil said:**
> edit: just tried it on gnome and it's working great, so it's just a kde related problem

I have a Radeon 9000 in a T40 Thinkpad and would like to get Compiz working in Gutsy Gibbon. Would you share tips for your success?

---

### Post by w4ett on 2007-10-21
> **cogitordi said:**
> I have a Radeon 9000 in a T40 Thinkpad and would like to get Compiz working in Gutsy Gibbon. Would you share tips for your success?

I used this tutorial for Compiz Fusion installation (ignoring the references to the Nvidia driver install):

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by cogitordi on 2007-10-21
> **w4ett said:**
> I used this tutorial for Compiz Fusion installation 
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

I tried your suggestion and when I try compiz --replace I see
"No whitelisted driver found"

Which driver are you using?

I have 
xorg-driver-fglrx (7.1.0-8.37.6+2.6.22.4-14.9)

---

### Post by w4ett on 2007-10-21
> **cogitordi said:**
> I tried your suggestion and when I try compiz --replace I see
"No whitelisted driver found"

Which driver are you using?

I have 
xorg-driver-fglrx (7.1.0-8.37.6+2.6.22.4-14.9)

I am using the open source xorg-driver-ati on a ATI 9200 SE card

---

### Post by umlungu64 on 2007-10-23
Hello to everybody!

I do have a TP R51 with a ATI 9000 as well. Since a few days I've been trying to get compiz-fusion running on Gutsy. The Monitor I've got is 1400x1050, and I'm quiet sure there is the problem. With stock standard Gutsy I could not get the compiz turned on. The installation with Envy does not help, since, if I understand this correctly, the 8.28.8 ATI driver will not run with the xorg from Gutsy. I've also tried Xgl, but that always brought me back to the Loginscreen. I also tried the "radeon" driver instead of the original "ati" in xorg.conf, but without success. I changed the colour depth from 32 to 24 and to 16, also no luck. ;o( But yesterday I did change the screen size to 1024x768, which is very ugly, but it worked. Since I'm no computer guru, and do most of my adjustments on my favourite Edgy (this is my working OS) through the good help from the forums, I'll stick to the normal graphic-stuff. So at the moment I'll stick to Edgy!
But the funny thing is, I've got the wobbly windows on this machine with the OS "SAM2007", which is also a nice OS, but it's just not Ubuntu. Sorry, that I could not give any help, but maybe some point of direction where the problem could be.
Since this is also one of my first posts in this forum, I would like to thank all the ones, which help people like me, to get Linux running for the personal use. I'm now three years MS free, and very happy!

Regards Heinz

---

### Post by Michael Longval on 2007-10-28
(...Currently listening to Edith Piaf ...)

Compiz + 7.10 + ATI Radeon 9000 working! (at last)

Ok... I'll try to get this right the first time.

System: IBM ThinkPad T41, Radeon 9000 (r250) @ 1400 x 1050, 1 Gig RAM

OS: **Ubuntu 7.10 (Gutsy Gibbon)**

I pulled my hair out for a day trying to get the proprietary ATI drivers (fglrx) to work.  

Simply put: (at the time of this post) the drivers from ATI **DO NOT WORK WITH THE RADEON 9000**.

My suggestion if you have a Radeon 9000 based card is **DO NOT INSTALL** the fglrx driver.  
Otherwise you will get stuck in a rut because of the OpenGL libraries (libMESA) (they are hard to remove..?)

Ok.  So after pulling my hair out for a day (I said that already)... I REINSTALLED Gutsy.

With a fresh install, it was more or less easy.

I changed xorg.conf (after reading many many posts) to this:

==== Relevant sections of xorg.conf ====

```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```
==== End Relevant sections of xorg.conf ====

The driver is set to "ati" and the AIGLX option is set to "true" and Depth is 24.

In THEORY that should do it. (wouldn't life be great if it was that simple)

But running compiz in a terminal window gets me: (btw do NOT run compiz as root)

doc@T41:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity

Very discouraging.... but the bad part is NOT the "Checking for Xgl: not present" as I first thought, this is normal it seems.  

The bad part is "Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed."

This it turns out is a bug in the file /usr/bin/compiz

Then after reading this thread: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

I tried running compiz with SKIP_CHECKS=yes 

It works, compiz runs but the screen is all garbled on the right hand side (about a quarter of the screen).
  
FINALLY the answer became: 

1: change the Default Depth in xorg.conf to 16 (big thanks to Glenn Slotte on lauchpad.net [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519/comments/16](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519/comments/16))

2: run compiz with SKIP_CHECKS=yes (ie:  $ SKIP_CHECKS=yes compiz )

3: you might want to install package Emerald + the compiz control programs (...forgot the package names...) before you run compiz


So here is the final WORKING xorg.conf file:

==== Relevant parts of xorg.conf ====

```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    16              
        SubSection      "Display"
                Depth   16
                Modes   "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


```==== End relevant sections ====

I hope this helps those who are trying to get compiz to work with their r250 (radeon 9000) based systems.  I must say that I am really impressed with the Ubuntu Community here in the forums and at launchpad.net ... I was able to troll around and find a lot of usefull info that helped me finally fix my system.

Keep it comin' guys!

Michael Longval
------------------------------------
Ubuntu 7.10 on ThinkPad T41
PowerBook 15" MacOSX 10.4.9

---

### Post by lognok on 2007-10-31
Mr. Michael Longval, thank you very much for your guide. I'm now running my desktop on your settings and desktop effects are working surprisingly very nicely.

A big thank you.

---

### Post by lognok on 2007-10-31
By the way, how do I make it run 'SKIP_CHECKS=yes compiz' on every start-up?, tried to put it in sessions, but it didn't work.

Or maybe better, how to make an icon that could launch it instead?, then I could launch it whenever I wanted incase an application didn't like to run in compiz.

---

### Post by Michael Longval on 2007-10-31
> **lognok said:**
> By the way, how do I make it run 'SKIP_CHECKS=yes compiz' on every start-up?, tried to put it in sessions, but it didn't work.

Or maybe better, how to make an icon that could launch it instead?, then I could launch it whenever I wanted incase an application didn't like to run in compiz.

I added a launcher to the panel at the top of the screen. The launcher runs a small script that I called "compizgo"

Contents of compizgo:
```

#!/bin/sh

SKIP_CHECKS=yes compiz --replace 

```

Save the file in your "home" directory or in the "bin" directory of your "home".
Make sure you do a "chmod +x compizgo"  to make the file executable.

Then right click on the top menubar (panel) and add an "Application Launcher" that points to the script.  

That should do it.

Michael

---

### Post by ljpp on 2007-11-01
Excellent! I can confirm that Michael Longval's solution does work on IBM T41 (RV-250). This should make it to the official updates as well!

It also works on IBM Thinkpad X23 (Radeon Mobility M6). I can enable the effects and they work smooth. However there is an issue with window titles -- window titlebar turns white if I maximize a window to fullscreen. Same even with Emerald.

---

### Post by lognok on 2007-11-01
Thanks for your post on the launcher Michael Longval, it works great. To supplement it I also made a metacity launcher to get back again.

By the way I'm on an IBM R51 1829-EHG.

Thanks again :)

---

### Post by umlungu64 on 2007-11-06
Hello to all!

Thanks to Michael, my R51 with a ATI9000 is now also running compiz-fusion. Very well done! I've not tried the launcher, but I will as soon as I get Gutsy on my working machine.
Lognok, could you give me the command for switching back to metacity please?

Thanks again to all of you!

Heinz

---

### Post by turte on 2007-11-07
> **lognok said:**
> By the way, how do I make it run 'SKIP_CHECKS=yes compiz' on every start-up?, tried to put it in sessions, but it didn't work.

Or maybe better, how to make an icon that could launch it instead?, then I could launch it whenever I wanted incase an application didn't like to run in compiz.

Try putting a line SKIP_CHECKS=yes to file ~/.config/compiz/compiz-manager. The file probably does not exist, so just create it and add the row. You should then be able to enable/disable Compiz directly from the settings. Works for me.

I noticed this while browsing the wiki at  [http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

---

### Post by lognok on 2007-11-07
@umlungu64
The command I run to get back to Metacity is this: 'metacity --replace'

You can run it from the terminal or make a launcher as I did, just:
right click on panel -> add to panel -> custom application launcher:
   Type: Application
   Name: Metacity
   Command: metacity --replace
   Comment: Bla, bla, bla....
Choose an icon for your launcher and click 'OK'.

Don't know if this is the right way to do it, but it works on my machine.

---

### Post by umlungu64 on 2007-11-08
To Lognok

Many thanks to you. I'll try your command as soon as I've install the new Gutsy on my R51. Can't wait to show my friends, that Linux is not just a very good system for daily use, even if you are not a hacker ;), I can show them now some eye-candys as well!
Thanks for your support!

Heinz

---

### Post by salvadorveiga on 2007-11-08
> **w4ett said:**
> Well....I use the 9200 card (not supported by fglrx either, btw) and have good luck with it.....I get 800+ fps out of it and have full use of compiz  and also Google Earth......I'm not a gamer and it fills my requirements...so as you can see I'm not the best to advise on the game useability.  

Also considering these chipsets are getting a bit long in the tooth, if you want gaming capability, the only sensible choice in linux would be a Nvidia card/chipset, or to buy a card compatible with the newest ATI drivers that were released just a few days ago, and that is also compatible with your motherboard.


im sorry I use the same card... what's the command to check the FPS of my card ? thanks

---

### Post by w4ett on 2007-11-08
> **salvadorveiga said:**
> im sorry I use the same card... what's the command to check the FPS of my card ? thanks

In the terminal:

```
glxgears
```

---

### Post by salvadorveiga on 2007-11-08
thanks ;) 700 FPS like you had... I'm glad I use AIGLX with the open driver... xgl is too damn slow... I tried the other day and is super slow

---

### Post by w4ett on 2007-11-10
Yeah..the open source driver and AIGLX are the way to got with our "old" hardware

---

### Post by bit_racer on 2007-11-10
hello

btw, have you been able to use the dual head feature in the radeon 9000 mobile?
I have the 3d effects and all, but still have not been able to get the OS to detect the external VGA monitor....

---

### Post by umlungu64 on 2007-11-13
Hello together!

I also don't have the dual-head working on my R51 (ATI9000). But I found a link ([http://ubuntuforums.org/showthread.php?t=580967](http://ubuntuforums.org/showthread.php?t=580967)), which talks about this problem. I've not tried it yet.
I also experienced problems when playing videos when I follow this tutorial from Michael. But it may well be, that’s the lack of my knowledge, rather then this HowTo. I have now gutsy installed twice, and select it when I boot. Compiz is just to show off! ;) I work normally with the straight Ubuntu.
I also have some strange outputs from glxgears, (ca. 250 fps with stockstandard Gutsy; ca. 800 fps with this HowTo, but compiz switched of; and ca. 1200 fps with compiz running) but I have check this again, since it does not make any sence to me. Or does it to you??

I’ll keep you informed!

Heinz

---

### Post by umlungu64 on 2007-11-13
> **umlungu64 said:**
> Hello together!

I also don't have the dual-head working on my R51 (ATI9000). But I found a link ([http://ubuntuforums.org/showthread.php?t=580967](http://ubuntuforums.org/showthread.php?t=580967)), which talks about this problem. I've not tried it yet.
I also experienced problems when playing videos when I follow this tutorial from Michael. But it may well be, that’s the lack of my knowledge, rather then this HowTo. I have now gutsy installed twice, and select it when I boot. Compiz is just to show off! ;) I work normally with the straight Ubuntu.
I also have some strange outputs from glxgears, (ca. 250 fps with stockstandard Gutsy; ca. 800 fps with this HowTo, but compiz switched of; and ca. 1200 fps with compiz running) but I have check this again, since it does not make any sence to me. Or does it to you??



I’ll keep you informed!

Heinz

I've got to correct my statement above. The output of glxgears is on standard Gutsy 900fps and with Michaels HowTo 1580 with or without compiz.
I've also tried some videos again, but no luck. I still get a blank window on the video-player, but sound is working.

Heinz

---

### Post by Michael Longval on 2007-11-14
Hello,

I just tried GLXGEARS to see what I got. (IBM T41 Radeon 9000 + Ubuntu 7.10 + Compiz)

mike@T41:~$ glxgears 
6973 frames in 5.0 seconds = 1394.418 FPS
6932 frames in 5.0 seconds = 1386.392 FPS

So 1200 FPS sounds reasonable to me.

Michael

---

### Post by umlungu64 on 2007-11-15
Hi Micheal!
It look's like my ATI9000 performs a bit better. :)
But do you know why the video playback doesn't want to work on my Thinkpad?
Has it got to do with the addings in the xorg.conf?

Also, a bit off topic: Can I do a login, where I can choose if I want the xorg.conf (standard) or the xorg.conf (modified)? For exapmle have two users with a different xorg.conf?


Heinz

---

### Post by phen on 2007-11-15
hello!

compiz now works for my thinkpad x31 with **ati radeon m6 ly**. thank you!

when maximizing a window to fullscreen, the window border gets white. does anybody know how to fix this?

my glxgears is only 300fps :-(

---

### Post by bit_racer on 2007-11-15
Hello!

At last I was able to set up the dual-head display on my laptop using a radeon 9000 mobile on ubuntu Gusty. 

First I have to say that gusty, at least with this videocard is incompatible with videorama.
So the only thing we have is xrandr....but the funny thing is that with xrandr is even easier, I didnt even had to mess with my xorg file, well maybe a little....:P, I had to change in the xorg file the device driver from 'ati' to 'radeon'.

Well what I did was...

At first I had a problem because xrand could not detect my external vga monitor, what I did to solve this problem was type in terminal

```
 xrandr --addmode VGA-0 1024x768

```
 
this will add a vga monitor with 1024x768 resolution to xrandr, if your external monitor uses another resolution you could change it.

then I wrote in terminal

```
xrandr --output VGA-0 --mode 1024x768

```

and waalaa! :P I had dual output!
but the image in the vga monitor was incomplete because it seems that the radeon 9000 mobile can only output 1024x768 when using it in dual head mode, even in windows with the official drivers when I used dual head the resolution automaticatly lowers from 1280x800 to 1024x768(maybe there could be a way to solve this limitation, but I only need 1024x768 output)

so now we have to lower the laptop resolution...

```
 xrandr --output LVDS --mode 1024x768
```
now we have the image as we wanted it with dual output

you could play with other commands and configurations that better suits your :), but I hope this gives you the idea...:)
for more information check this blog, this is where I got most of this information
[http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

I hope this helps :)

P.S. sorry about my grammar,I rarely speak english :/

---

### Post by FloBo2000 on 2007-11-19
Hi there.

I changed my xorg.conf according to the one by Michael Longval and tried to start compiz with SKIP_CHECKS=yes.
Unfortunately it doesn't start as expected. I get the following error messages: 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

As I'm completely new to Linux, I really have no clue at all, how I have to handle this error... my Laptop is an IBM T41 with Radeon 9000, and the only thing I couldn't get working is this :(

Hope you can help me...

Kind Regards, FloBo

---

### Post by sbhattacharjee on 2007-11-19
> **Michael Longval said:**
> I added a launcher to the panel at the top of the screen. The launcher runs a small script that I called "compizgo"

Contents of compizgo:
```

#!/bin/sh

SKIP_CHECKS=yes compiz --replace 

```

Save the file in your "home" directory or in the "bin" directory of your "home".
Make sure you do a "chmod +x compizgo"  to make the file executable.

Then right click on the top menubar (panel) and add an "Application Launcher" that points to the script.  

That should do it.

Michael

This works great. As noted earlier, I also changed my xorg.conf to have 16 bits display instead of 24. The only lingering problem is, there seems to be a problem with scrolling. When I scroll I see a cpu spike. This is particularly noticeable on firefox, but is present in all windows with scrolling.

Some people suggested to uninstall xgl, but I dont have xgl and made sure of that. Somewhere else people suggested this is a compiz issue.

Anyone seeing this same problem?

My Specs
Dell D600
ATI 9000 (RV250)
External Monitor 1280x1024
LVDS - 1024x768
driver "ati"

---

### Post by FloBo2000 on 2007-11-22
Anyone?!
I just wanna see my nice T41 with effects enabled :cry:

---

### Post by cybrough on 2007-11-22
I just installed 7.04 (7.10 will not boot) on my Kohjinsha sa1 UMPC.  it is based on AMD Geode. it uses cs5345 audio board with a Realtek ALC655 rev0 chip.

It will play system sounds but no sounds any application.  The error I get is that the audio device is busy.  I've tried killing any sound processes except the one I want to run.  I noticed that when I try to play system sound when some other application that uses audio, the system sounds will not play. 

The list below is when I try to play using aplay:


Playing raw data 'AboveGround.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
aplay: set_params:965: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  U8
SUBFORMAT:  STD
SAMPLE_BITS: 8
FRAME_BITS: 8
CHANNELS: 1
RATE: 8000
PERIOD_TIME: 125000
PERIOD_SIZE: 1000
PERIOD_BYTES: 1000
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 4000
BUFFER_BYTES: 4000
TICK_TIME: 4000

Any help is appreciated.

Carl

---

### Post by neodevelop on 2007-11-24
Hi this forum!!!
This time is a little contribution, I have a Inspiron600m, Centrino 1.5GHz, Ati Radeon 32 MB, and well I have problems with compiz...
First in the fresh installation without network connection(to updates) the compiz-fusion work correctly...
After in another fresh installation, this time with network connected the compiz doesn't work, strange uh!!!
Well, I follow this tutorial to make the effects appear:
[http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)
After this I have the effects in my desktop, but, oh my god, I update the system, and again the effects dissapears :(
Well I have to uninstall all the compiz and emerald with dependencies, after I try installing xserver-xgl by the message that appear me at the momento of put compiz in the console, but not work because the X cannot be started, only show me a black screen and returns me to the login screen...
Well I have to enter in Gnome Fail Safe and uninstall the xserver-xgl...
After read this post but only change in my xorg. conf the Depth to 16, and add two modules, I put my file, or the most important part:
[php]
Section "Device"
    Identifier    "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Option          "AIGLX" "true"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
[/php]And finally work, because appears me the error "Desktop effects could not be enabled" at each time that I try all the options before...
But finally with this work the compiz correctly...
This maybe help someone...
Thks a lot..
Sincerely
neodevelop

---

### Post by swoop_ubu on 2007-11-24
mates,

maybe this will be redundant, but I still would like to wrapup how I managed to solve "Desktop Effects" on my DELL Latitude D600.

1)
I edited the xorg.conf file so it in the "Dislpay" section said:
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes        "1400x1050"
    EndSubSection
EndSection
REMEBER: You have to have there both the "...Depth 16" lines!!

2)
I created ~/.config/compiz/compiz-manager file with "SKIP_CHECKS=yes" content

3)
reboot

4)
Visual Effects: Extra

That is it. Compiz servers... :)

cheers
ubu

---

### Post by Yellow Pasque on 2007-11-24
From what I can tell, the card won't be supported through fglrx anymore, just like in the Windows world.

Your best hope is the open-source drivers, which are slowly but srely making progress as AMD/ATI continues to release more specs to developers.

---

### Post by phen on 2007-11-25
hello all!

there was something mentioned in another thread:

use 
```
Option "AGPSize" "32"
```
in the device section, to increase the texture size.

it might be possible to run compiz without skipping the checks. for me I had to use depth 16 but now i am able to run without skip_checks. 

the white-border problem is solved, too.

---

### Post by swoop_ubu on 2007-11-27
> **swoop_ubu said:**
> mates,

maybe this will be redundant, but I still would like to wrapup how I managed to solve "Desktop Effects" on my DELL Latitude D600.

1)
I edited the xorg.conf file so it in the "Dislpay" section said:
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes        "1400x1050"
    EndSubSection
EndSection
REMEBER: You have to have there both the "...Depth 16" lines!!

2)
I created ~/.config/compiz/compiz-manager file with "SKIP_CHECKS=yes" content

3)
reboot

4)
Visual Effects: Extra

That is it. Compiz servers... :)


well well,

another problem appeared. when I play video i see only green screen.
I have no idea if it is caused by the 16 bpp setting or it is compiz' fault.
I had to switch back to 24 bpp and disable Visual Effects...

does anyone have an idea?

cheers
ubu

---

### Post by phen on 2007-11-27
you can try to change your video output setting to something NON xv

you have to see totems preferences. sorry i cant explain it exactly, as i am at work..

it helped me with the same problem!

---

### Post by Cjpettit on 2007-12-02
Hello, I'm running Dell D600 with Mobility Radeon 9000 the xorg-video-ati driver and I've changed my depth to 16. however, I notice that you are all receiving way higher fps than I am:

caleb@caleb-laptop:~$ glxgears
765 frames in 5.0 seconds = 152.854 FPS
743 frames in 5.0 seconds = 148.081 FPS
736 frames in 5.0 seconds = 147.008 FPS
738 frames in 5.0 seconds = 147.461 FPS


What can I do to help raise this up?

---

### Post by fedsharp on 2007-12-03
Hello,
I was successful in setting 24 bit colour depth and passing the texture test,
here are the relevant sections, in bold is the statement that solved the 16 bit issue,
the other xorg.conf sections are very similar to the ones so far illustrated so
I did not report them:

 ########### xorg.conf ################
[FONT="Courier New"]
Section "Screen"
Identifier      "Default Screen"
 [INDENT]      Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
        [INDENT]  Depth   24
              **Virtual 1920    1440**
               Modes           "1400x1050@60"[/INDENT] 
EndSubSection[/INDENT] 
EndSection

Section "Device"[INDENT]
        Identifier      "Failsafe Device"
        Boardname       "ATI Radeon (fglrx)"
        Busid           "PCI:1:0:0"
        Driver          "radeon"
        Option "GARTSize" "64"
        Option "XAANoOffscreenPixmaps" "true"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
[/INDENT]EndSection
[/FONT]

here is the output after running compiz

[FONT="Courier New"]
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
[/FONT]

With the above settings compiz and X work on the entire screen.

Details on my system are:

[FONT="Arial Narrow"]
DELL Latitude D600 with Ubuntu Gutsy 7.10
laptop display resolution: 1400x1050
Graphic card: ATI Radeon 9000 (rv250)

the open-source video driver is from package:
xserver-xor-video-ati

libGL and DRI are from packages:
libgl1-mesa-dri
libgl1-mesa-glx
(if you installed fglrx you have to remove and reinstall libgl1-mesa-.... )

 [/FONT]

---

### Post by phen on 2007-12-03
does 24 bit look better than 16? is it worth a try if compiz is allready running fine but in 16bit?

and another question: I am still trying to improve my graphics performance (glxgears:400fps). is it possible that your settings improve performance? thank you

bye

---

### Post by fedsharp on 2007-12-03
A 24bit colour depth screen looks better than a 16bit one, it is quite visible for me,
in fact when I was stuck to 16bit issue I decided not to use compiz and to run
metacity in 24bit. Using 24bit the Desktop effects seem a little slower but acceptable for me.
So, I do not think my settings may improve the performance of the acceleration.

Running glxgears, in the default windowed mode, I get about 877fps. In 16bit I remember to get
twice that value.

I do not know if you can get better performance using some option of the DRI module.
I give you a web link reporting some possible option, like XAA (I tried them but I did not notice any
improvement on my system):
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)

Anyhow, I am not able to play videos when compiz is running, either if I am using a 16bit screen
or if I am using a  24bit screen. I will try in the next days to solve such problem.

---

### Post by fedsharp on 2007-12-03
at the above link do not forget to take a look at the driconf utility and at the related
wiki web page, they well illustrate how to configure the DRI options, I am reading too.

---

### Post by phen on 2007-12-03
is anybody here able to load the dri and glx modules like explained in the driwiki? when I edit my xorg.conf for it, X  won't start after reboot.

But I have Effects enabled. unfortunately with only 400fps...

my card is an old radeon7000

---

### Post by Michael Longval on 2007-12-04
Great! Now after applying the modifications suggested by Fedsharp I'm getting Compiz on a 24 bit screen.  

Here are the parts I've changed in my xorg.conf file (in Bold)
```

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	[B]Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"[/B]
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9000"
	Monitor		"Generic Monitor"
	**DefaultDepth	24**		
	SubSection	"Display"
		[B]Depth	24
		Virtual 1920 1440[/B]
		Modes	"1400x1050"
	EndSubSection
EndSection

```

After this I'm still getting about 750 fps in glxgears.

Overall very satisfied.  Thanks Fedsharp.

Michael Longval

> **fedsharp said:**
> Hello,
I was successful in setting 24 bit colour depth and passing the texture test,
here are the relevant sections, in bold is the statement that solved the 16 bit issue,
the other xorg.conf sections are very similar to the ones so far illustrated so
I did not report them:

 ########### xorg.conf ################
[FONT="Courier New"]
Section "Screen"
Identifier      "Default Screen"
 [INDENT]      Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
        [INDENT]  Depth   24
              **Virtual 1920    1440**
               Modes           "1400x1050@60"[/INDENT] 
EndSubSection[/INDENT] 
EndSection

Section "Device"[INDENT]
        Identifier      "Failsafe Device"
        Boardname       "ATI Radeon (fglrx)"
        Busid           "PCI:1:0:0"
        Driver          "radeon"
        Option "GARTSize" "64"
        Option "XAANoOffscreenPixmaps" "true"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
[/INDENT]EndSection
[/FONT]

here is the output after running compiz

[FONT="Courier New"]
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
[/FONT]

With the above settings compiz and X work on the entire screen.

Details on my system are:

[FONT="Arial Narrow"]
DELL Latitude D600 with Ubuntu Gutsy 7.10
laptop display resolution: 1400x1050
Graphic card: ATI Radeon 9000 (rv250)

the open-source video driver is from package:
xserver-xor-video-ati

libGL and DRI are from packages:
libgl1-mesa-dri
libgl1-mesa-glx
(if you installed fglrx you have to remove and reinstall libgl1-mesa-.... )

 [/FONT]

---

### Post by Iwantu_ubuntu on 2007-12-05
Great work guys!  Compiz not working on T40 had been a great source of disappointment until now!  I can firm that the Fedsharp modifications have also worked on IBM Thinkpad T40, with ATI Radeon 9000.  Video play back also seems to be working.  In addition, compiz seems to be working upon logon and I haven't had to use the launchers mentioned in the earlier posts here.

On a separate note...how does one substitute the Windows (Super Key) on laptops that don't have it? The older IBM thinkpads don't have the Windows Key...I can't use some of the compiz effects as a result.

```
 

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9000"
	Monitor		"Generic Monitor"
	DefaultDepth	24		
	SubSection	"Display"
		Depth	24
		Virtual 1920 1440
		Modes	"1400x1050"
	EndSubSection
EndSection


```

---

### Post by fedsharp on 2007-12-05
About the "Super" key:
You could try to re-map the keyboard shortcuts bound to the desktop effects,
taking care of not to introduce conflicts.
Two useful utilities doing that come with two packages:

gnome-compiz-manager

and

compizconfig-settings-manager

After installation they are both found in "System -> Preferences" menu.

I used the utility coming with the first package, called"GL Desktop", to set
the Expose-like effect ("Windows viewport" here) to run when I move the mouse
pointer at the  bottom right corner of the screen. That is more handy than the
ALT-Shift-cursor_up keys combination.

The second utility is richer and allows to enable and configure a lot of effects.

About the acceleration:
It seems I am not able to use EXA 2D acceleration, although I read that the chipset rv250
supports it and it may also improve the DRI performance. When I use 
Option "AccelMethod" "EXA" in xorg.conf's device section, as soon as compiz starts
the X server crashes because the session logs out.

---

### Post by phen on 2007-12-05
ATI Radeon 7000 Mobility M6 (Thinkpad X31): not successful with 24bit! Compiz-fusion runs at 16bit depth here, but 24 didn't work with the fedsharps steps.

---

### Post by StevoG7 on 2007-12-09
For those of you wanting to run the "SKIP_CHECKS=yes compiz --replace" script at startup, follow the previous instructions on creating the compizgo file, and make sure to save it in the bin directory.  If you have made it executable under properties, you should be able to add a session with command "compizgo" which will then initiate on startup.  I have done this and compiz starts up on my machine when i log in, no launcher necesarry :)

---

### Post by umlungu64 on 2007-12-11
Hello To everybody!

It's been a few days now, since I last checked this page, but now I'm glad to see, that everything will work also with 24bit and video-watching. I've not tried it out, but as soon as I get some time, I'll be changing my xorg.conf.
Has anybody tried this solution with dualhead? There is a link to a post which gives a howto, but I've not tried it. If I could have the copy of that xorg.conf, it would help to ease my fear of changing things in the system.
I don't want to fiddle to much with my R51 Thinkpad, since I need it for work. ;o)
Many thanks to all the helpful people, who have the nerves to keep the "normal" users like myself going, also with the fancy stuff of Linux.

Regards Heinz

I've got a ATI 9000 and a Screen with 1400x1050pix. My Os is of course ubuntu gutsy, with standard kernel! My external screen needs a resolution of 1024x768 or even 1280x1024 if possible.

---

### Post by megamania on 2007-12-18
I'm wondering if I'm the only one experiencing this weird problem:

I have an Ati Radeon Sapphire 9000 graphics card with a Sony SDM HX73 monitor

Since I clean-installed Gutsy (last september), the screen blanks from time to time, and after one second or two the image comes back.

I'm pretty sure it's a sync problem, but I've been unable to solve it so far. I noticed, however, that it is much more frequent with compiz enabled.

I'm using the default ati drivers (open source, I'd say) which have worked perfectly until Gutsy came out.

Do you have any ideas? I can post my xorg.conf if needed.

---

### Post by umlungu64 on 2007-12-19
Hello megamania

I'm not too sure if this is a software problem. Have you tried all the connections if one of them is loose? Even if the graphic card is properly plug in?

Regards Heinz

---

### Post by swoop_ubu on 2007-12-19
mates,

this might sound silly, but i cannot help asking. what keeps R900
from displaying in 32-bit colour depth? is 32 MB really not enough
to grasp the video data or is it the additional overhead that stays in the way?

let us know
cheers

---

### Post by megamania on 2007-12-19
> **umlungu64 said:**
> Hello megamania

I'm not too sure if this is a software problem. Have you tried all the connections if one of them is loose? Even if the graphic card is properly plug in?

Regards Heinz
Hi Heinz,
I checked the cables, and I have the same problem on both outputs (DVI & VGA).

I unplugged the card, cleaned the contacts, plugged it in again... same problem.

I never had a single problem since ubuntu 4.10, and Beryl on 6.04 worked flawlessly.

With compiz enabled the situation is unbearable (blanks every 10-20 seconds, but sometimes much more often), if I disable it it's acceptable (blanks every minute, or even more seldom).

Also, I installed Windows and it does not blank at all - so it's linux, I'd say.

Any ideas?

---

### Post by lognok on 2007-12-20
@swoop_ubu

I don't think 32mb i enough. If you calculate it you'll see:
16x1400x1050=23.52mb
24x1400x1050=35.28mb

32bit mode?, as far as I know it's only 8bit per primary color R+G+B=24bit. And 32 doesn't divide by 3, but if you had a panel capable of 10bit per primary color then you could display 30bit color depth if you had more than 44.1mb of video ram for a 1400x1050 panel.

Haven't heard of 10bit laptop panels yet, but I sure would like one :)


Now that swoop_ubu brought it up, how come I can stil run 24bit color depth on my screen?, I followed the guide in this post and got it working and it's great, but what does the hack do?

---

### Post by rupierto on 2007-12-29
I had a Radeon 9000 card (Sapphire) and a Samsung CRT monitor.
Always had problems trying to get the best from them with Linux OS (I tried all the major distributions and finally choose the best: Ubuntu).

My problem: effects works fine but after I try Planet Penguin Racer I discover I had very low FPS (9.6 - 8.0).

Anyone had similar problem?

Here is the relevant part from my xorg.conf

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Boardname	"ATI Radeon"
	Busid		"PCI:2:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 957p"
	Horizsync	30-96
	Vertrefresh	50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes	"1024x768@85"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by swoop_ubu on 2007-12-30
> **Michael Longval said:**
> Great! Now after applying the modifications suggested by Fedsharp I'm getting Compiz on a 24 bit screen.  

Here are the parts I've changed in my xorg.conf file (in Bold)
```

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	[B]Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"[/B]
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9000"
	Monitor		"Generic Monitor"
	**DefaultDepth	24**		
	SubSection	"Display"
		[B]Depth	24
		Virtual 1920 1440[/B]
		Modes	"1400x1050"
	EndSubSection
EndSection

```

After this I'm still getting about 750 fps in glxgears.

Overall very satisfied.  Thanks Fedsharp.

Michael Longval

Well, well, well...
I changed my xorg.conf above mentioned way and, indeed, compiz started
in 24bit mode. however *none* of my video players (totem, mplayer, vlc) were
able to play movies. those just started and exited instantly...

anyone knows waht did i forgott / what i miss?
thaks in advance

ubu

---

### Post by NoVista on 2007-12-31
Ugh, I just noticed the same thing.

But I just went back and rechecked my xorg.conf, and sure enough I missed a few lines that needed to be added.
CompizFusion, video playback, and 24 bit are all working perfectly together.

This is on a Dell latitude D600, 32 meg ATI 9000.

---

### Post by swoop_ubu on 2008-01-05
> **NoVista said:**
> Ugh, I just noticed the same thing.

But I just went back and rechecked my xorg.conf, and sure enough I missed a few lines that needed to be added.
CompizFusion, video playback, and 24 bit are all working perfectly together.

This is on a Dell latitude D600, 32 meg ATI 9000.

NoVista,
can you post your xorg.conf file here. I'd appreciate it. thanks.

cheers
ubu

---

### Post by acoustibop on 2008-01-05
> **swoop_ubu said:**
> Well, well, well...
I changed my xorg.conf above mentioned way and, indeed, compiz started
in 24bit mode. however *none* of my video players (totem, mplayer, vlc) were
able to play movies. those just started and exited instantly...

anyone knows waht did i forgott / what i miss?
thaks in advance

ubu

You need to disable Compiz to play videos, swoop_ubu, and to play games effectively.

---

### Post by NoVista on 2008-01-05
I do not disable Compiz to play videos.
Here's the file .. ..

---

### Post by swoop_ubu on 2008-01-28
> **NoVista said:**
> I do not disable Compiz to play videos.
Here's the file .. ..

NoVista,
it doesn't work for me. It is surprising, because I actually utilise DELL Latitude D600
with ATI Radeon Mobility 9000, as you do.

Does nyone else have suggestions? If COmpiz can be used while video playback
works, I would become a definite convert (yes I used XP before ;))

cheers
ubu

---

### Post by ~vel on 2008-01-28
I'm having an issue getting compiz to work on my setup here. I'm using a Radeon 9250 Pro, PCI 256mb. I'm not sure if I'm not using the correct driver or what but it's troublesome and I can't figure it out. Here's my xorg.conf file.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:6:0"
	Driver		"radeon"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"800x600@75"	"800x600@60"	"800x600@72"	"1280x768@60"	"800x600@56"	"1280x720@60"	"1280x800@75"	"1280x768@75"	"1280x800@60"	"1440x900@75"	"1440x900@60"	"1600x1024@60"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:6:0"
	Driver		"radeon"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Estepario on 2008-01-31
i have a dell inspiron 600m and i have  problems my ati randeon 9000.

The problem is it looks that compiz work well, but when a play a video in youtube por example the use of cpu increase over 60% and the temperature over 80°C.
The same happens if a try to play supertuxkart.

if i come back to metacity, then the problem is the same.

any help??

---

### Post by thecapuchin on 2008-02-03
Ok, I found this thread last night and have been thanking the gods above and below for letting me find it at all.  That being said, here is the trouble that I've been having:

I have managed to use Michael Longval's method to get compiz to load (SKIP_CHECKS works fine but.....).  The issue is that the desktop is still all screwed up.  My windows show up just fine, but the desktop background is gone and while the cube shows up and works mostly as it should, the experience isn't what I'd hoped for.  I've attached a screenshot to give you all an idea what I'm seeing and I hope there's some bright person out there who can point me in the right direction.

Thanks all, I love the Ubuntu community.

---

### Post by drdrewdown on 2008-02-04
[QUOTE=Michael Longval;3650745](...Currently listening to Edith Piaf ...)



THANK YOU SO MUCH MICHAEL LONGVAL

when & where can i buy you a beer?

---

### Post by automat on 2008-02-08
I've been running compiz on my ThinkPad T40 w/ Radeon 9000 using an X configuration similar to those listed here.  One thing I've noticed is that the fan runs almost constantly with the system essentially idle--negligible CPU usage with CPU speed scaled to ~37% (in my case, 600 MHz from 1.6 GHz).  This can only mean one thing--compiz is SERIOUSLY taxing the GPU, causing it to run noticeably hot.

Has anyone noticed increased fan speeds or reduced battery life using compiz?  Battery life isn't a huge issue as I run the laptop on AC power most of the time.  Unfortunately, the increased temperature as evidenced by the fan activity does worry me--ThinkPads (T40s in particular) [are known to have issues with GPU failure]("http://forum.thinkpads.com/viewtopic.php?t=33952") (cracking solder points on the main board possibly due to overheating?).  I'd hate to lose a laptop because of overworking the GPU.  At the same time, compiz offers a number of usability enhancements that are hard to do without.  What to do.... egh.

---

### Post by Kdawkins on 2008-03-16
I dont mean to bring back a dead post but because It pertains to my situation I thought I would post here...

I have an IBM T41 with the radeon 9000. Using Michael's post, I am able to get compiz running, but I still have a garbled right side of my screen...

here is my xorg.conf file:
 ```

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"
EndSection

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9000"
	Monitor		"Generic Monitor"
	DefaultDepth	24		
	SubSection	"Display"
		Depth	24
		Virtual 1920 1440
		Modes	"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

what did I do wrong? I really need this working ASAP, I leave for a trip tmmrw and my kids want to play Half Life on wine....

thanks so much,
kevin

---

### Post by fedsharp on 2008-03-17
> **swoop_ubu said:**
> Well, well, well...
I changed my xorg.conf above mentioned way and, indeed, compiz started
in 24bit mode. however *none* of my video players (totem, mplayer, vlc) were
able to play movies. those just started and exited instantly...

anyone knows waht did i forgott / what i miss?
thaks in advance

ubu

Sorry for my delay in answering but I've been off-line for a long period.
I also had the same problem. To fix you have not to use XVideo extension in video players.
Instead in place of it you have to use X11 video output. However this will require more work from CPU.
In VLC under "Preferences -> Video -> Output modules" check "Advanced options" and
choose "X11 video Output".
Mplayer (gui or command line) and Totem have got similar settings.

---

### Post by ljpp on 2008-03-17
> **Kdawkins said:**
> 

here is my xorg.conf file:
 [code]
Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9000"
	Monitor		"Generic Monitor"
	DefaultDepth	**24**		
	SubSection	"Display"
		Depth	**24**
		Virtual 1920 1440
		Modes	"1400x1050"
	EndSubSection
EndSection


Change Depths to 16.

---

### Post by larryfroot on 2008-03-20
Hi...I just wanted to say a **big** thank you to everyone in this thread for the help given. It seemed like the devils own job sometimes, but by following the advice here I managed to turn an old dell latitude into a machine that beats more modern kit running more modern software hands down. A fabulous endorsement of linux and of this forum as well. I don't really know that much, so the help here has been invaluable. I buy all of you a virtual beer! Nice one...! 

And I did learn a fair bit while I did all of it...but the less I see of xorg.conf the better these days! :)

---

### Post by teamonkey on 2008-03-26
Yes indeed, thanks everyone! Thanks to this thread I have Compiz now working in 24-bit mode on my Dell Inspiron 8500 with a 32MB Radeon 9000M card with a fresh Hardy Heron install.

It took a bit of fiddling and a lot of Googling to get this far, so here's my xorg.conf for reference:
```
# xorg.conf (X.Org X Window System server configuration file)
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver "ati"
	BusID "PCI:1:0:0"
	Option "GARTSize" "32"
	Option "MergedFB" "off"
	Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor "Generic Monitor"
	DefaultDepth 24
	#DefaultDepth 16
	SubSection "Display"
		Depth 24
		#Depth 16
		Virtual 1280 800
		Modes "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0	"Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection

Section "ServerFlags"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

I'm running compiz using the SKIP_CHECKS=yes flag so that it works without fglrx - I put that line in ~/.config/compiz/compiz-manager, as mentioned earlier in this thread. I can also confirm that the Virtual line makes all the difference: without it I get the corruption on the right side of the screen from pixels 1024 onwards in 24-bit mode.

Thanks again! I can't believe I've got it working at last.

---

### Post by Furiattl on 2008-03-26
Yeah, great post.
Helped me a lot.

---

### Post by toon_irc on 2008-05-01
I have a notebook Toshiba A70-s249 and after Ubuntu 6.06, compiz didn't work. The video card is ATI Mobility 9100IGP RS300.

I found this solution that works for me: 

-------------------------------------------------
The Ubuntu fix listed above worked for my Fedore 8 Dell Inspiron 5100 ATI Radeon Mobility M7 LW (7500). [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4)

Just used nano to create the file as mentioned there:

You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" />
-------------------------------------------------



My xorg.conf modifications:

in Section "ServerLayout" add:
Option "AIGLX" "True"

in Section "device" add:
Option "XAANoOffscreenPixmaps" "true"

in Section "ServerLayout" add:
Option "AIGLX" "True"

and at the end:

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection



I hope that's help someone.

---

### Post by funduguy on 2008-05-05
Thanks a lot to all the people who contributed to this threads. I have been trying to make it work on my Dell D600 for last one week. The only solution that worked for me was from this posting. Things really work like a charm with the methods defined in this posting. 

-Nitin

---

### Post by xiphosurus on 2008-05-07
You can actually still get 24bit color without getting the right quarter garbled with Radeon Mobility 9000 using compiz if you set the following in xorg.conf

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Virtual 1920 1440    #fixes the offset bug in compiz
		Modes "1400x1050"
	EndSubSection
EndSection

Of cos, don't forget to match the identifiers and device names.

---

### Post by GPizza on 2008-05-11
Hi all,
I've collected basically all the information from this thread in order to get Compiz running on my T41 with ATI Mobility Radeon 9000.
First I've just copied and paste the xorg.conf from Michael Longval post but system did not work well, I've even to restart on safe mode. Then I've collected some information from many posts and created my own xorg.conf file (which is pretty much what Michael has posted but few modifications).
Problem is that I have the same problem as Matt Yun: after activating visual effects with Compiz (System -> Preferences -> Appearance -> Visual Effects -> Normal), I got REALLY slow motion when moving windows in my desktop. Responses are VERY slow to commands...

I was wondering if this could be because some HW limitations as my videoboard has only 32MB. Do you think that would be the reason or it is possible to have smooth graphics with this HW setup?

Here goes my xorg.conf:

```
Section "Device"
	Identifier "Radeon 9000"
	Driver "ati"
	BusID "PCI:1:0:0"
	Option "GARTSize" "64"
	Option "MergedFB" "off"
	Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Radeon 9000"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Virtual 1920 1440
	Modes "1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Don't know what to do anymore...any help would be highly appreciated. Many thanks!!!

G.Pizza!

---

### Post by Jeroen Wit on 2008-05-26
At last everyting is working now for Dell D600 radeon rv250 driver !!!
Edit your compiz-manager.

/etc/xdg/compiz$ sudo nano compiz-manager

add this line:
SKIP_CHECKS="yes"

My xorg.conf file looks like this :


Section "Device"
Identifier "Radeon 9000"
Driver "ati"
BusID "PCI:1:0:0"
Option "GARTSize" "64"
Option "MergedFB" "off"
Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Radeon 9000"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Virtual 1920 1440
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection



You can Copy and Paste this text in to your xorg.conf file from
Section "device"

my resolution is 1400x1050 !!
color depth 24 bit !!
glxgears 3695 frames in 5.0 seconds = 738.948 FPS

I hope this will help everybody with radeon mobility 9000 card.

My regards,
Jeroen Wit is online now Report Post   	Edit/Delete Message

---

### Post by xiphosurus on 2008-05-27
has anyone else tried using this workaround from thinkwiki to enable 24bit in compiz without screen corruption?

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000)

basically you create a file /etc/drirc with the following contents.

```
<driconf>
       <device screen="0" driver="r200">
               <application name="Default">
                       <option name="allow_large_textures" value="2" />
               </application>
       </device>
</driconf>
```

i tried it, and deleted the virtual line in xorg.conf, rebooted and there is no screen corruption!

just wondering how it compares with the virtual method. IMO, it feels about the same in terms of performance.

---

### Post by apcfreak on 2008-05-27
> **xiphosurus said:**
> has anyone else tried using this workaround from thinkwiki to enable 24bit in compiz without screen corruption?


THANK YOU! I seem to remember trying that a while ago with no effects, but I just did and now I have compiz. :)

---

### Post by another_one on 2008-06-02
Jeroen Wit provided the xorg.conf file in his post for a Latitude D600... for some reason that file does not cause X to start in 1400x1050 when I use it on my D600.  Mine always defaults to 1024x768.

Can anybody shed light on why X would still start in 1024x768 despite my specifications in xorg.conf?  Is there something I need to do to get the X server to obey my xorg.conf file instead of defaulting to 1024x768?

Thanks in advance.

---

### Post by gmanpsycho on 2008-06-07
Thank you. I have broken several walls with my bald head because of this ATI drive mess. I got this to work in Hardy!!! I am running a Dell INspiron 8500 wih an RV250 (Radeon Firegl 9000). My glxgears fps went from ~700 to ~ 1350!!! Yippeee.... Now for Compiz or Beryl....

---

### Post by japhyr on 2008-06-07
Have you had any luck with this yet?  I'm stuck at 1024x768 as well.

---

### Post by Zababa on 2008-06-08
I am very much indebted for this thread. I got stuck during the installation of the open source ATI driver and this thread showed me where I made mistakes.

Most valuable to me were the posts by Michael Longval and fedsharp.

However, I realized, that on my Dell Inspiron 8200 the ATI Radeon Mobility 9000 can handle compiz on Hardy Heron.

---

### Post by hkspvt on 2008-07-04
Resurrecting this thread just to add some (hopefully) useful information.

 I'm running on a Dell Latitude D600 with Radeon 9000 Mobility, and with the help of this thread and a few other resources got my machine's graphics up to snuff. I'm running 1400x1050 with 24bit color, compiz enabled. 

Here's my glxgears scores under that config:

laptop:~$ glxgears
5889 frames in 5.0 seconds = 1177.788 FPS
6024 frames in 5.0 seconds = 1204.621 FPS
6021 frames in 5.0 seconds = 1204.045 FPS
6019 frames in 5.0 seconds = 1203.634 FPS
5946 frames in 5.0 seconds = 1189.127 FPS
laptop:~$ 

You can gain a lot of performance by running in 16bit color, if you can stand to look at it. Be sure to turn off your visual effects before changing to 16bit, or your desktop will not work correctly.

laptop:~$ glxgears
12248 frames in 5.0 seconds = 2449.457 FPS
15383 frames in 5.0 seconds = 3076.418 FPS
15389 frames in 5.0 seconds = 3077.605 FPS
15397 frames in 5.0 seconds = 3079.217 FPS
15399 frames in 5.0 seconds = 3079.668 FPS

The performance difference between 24bit + visual effects and 24bit - visual effects is negligible. 

I'm using the open source ATI driver. Here are the relevant lines from xorg.conf:

```

Section "Device"
	Identifier	"Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AccelMethod" "XAA"
	Option		"AccelDFS" "0"
	Option		"AGPMode" "1"
	Option		"AGPFastWrite" "1"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option		"EnablePageFlip" "1"
	Option		"ColorTiling" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9000"
	DefaultDepth	16
	SubSection	"Display"
		Depth	16
		Virtual 1920 1440
		Modes	"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"			"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Generic Keyboard"
EndSection

Section "DRI"
	Group		"video"
	Mode		0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

```

I've also installed DRI and used the driconf utility to set HyperZ to Yes. This realized a significant performance gain.

Hope that's helpful to someone.

-HKS

---

### Post by wildman4god on 2008-07-07
Hello, I have a dell latitude d600 and i want to use this guide to get the desktop effects running but, I need to know where you all got this open source ati driver. Please help, thanks.

---

### Post by tr45h on 2008-07-08
hi wildman.
i am also new to ubuntu and currently try to optimize radeon 9000. afaik the open source ati driver is the one that is installed as default. binary drivers from ati are currently not supported for our (rather old) graphics card radeon 9000.
hope that helps

---

