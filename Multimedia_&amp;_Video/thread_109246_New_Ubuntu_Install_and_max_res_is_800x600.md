---
title: "New Ubuntu Install and max res is 800x600"
date: 2005-12-28
forum: Multimedia &amp; Video
---

### Post by nofun2020 on 2005-12-28
Dear All Ubuntu User,

I have old computer brio 71xx
celeron 333, ram 96mb, and onboard mga g100 productiva

yesterday i had successfully install Ubuntu 5.10
but when i want to change the default resolution in System > Preferences > Screen Resolution, then i realyze that the maximum resolution is 800x600

So, anyone can tell me how to change the resolution to 1024x768?

Btw, I'm really really a new user of linux. But I'm happy because when I try install ubuntu, I get success :) 

best regarts,
novan_as

---

### Post by lutrafobic on 2005-12-28
Try this:

Open a terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

...this will start a guide that will ask you questions about your computer, stuff like which resolutions your graphiccard/screen and use.

---

### Post by nofun2020 on 2005-12-29
Hii lutrafobic,

I change **[COLOR="DarkRed"]ubuntu [/COLOR]**to **[COLOR="LightBlue"]kubuntu[/COLOR]**
but my max resolution is still 800x600

my question:
what program that i have to run to write your code? unfortunately i'm really new to linux. 
for example if i want to edit registry in my windows 
follow this order:
start > run..
tipe regedit

best regards
novan_as

---

### Post by anil_robo on 2005-12-29
Reboot your machine, and when it asks for username and password, click on the SESSION button and select "failsafe terminal". Then enter your username and password and boot in.

You'll see only a little terminal window in the lower right corner of the screen. TYpe this command :```
sudo dpkg-reconfigure xserver-xorg
``` and press enter.

Follow the directions very carefully. THere is a lot of text on the screen but it's worth reading. After you're done, reboot your machine again, and you should be able to select higher resolutions, just as I  did! :)

---

### Post by nofun2020 on 2005-12-31
Horray :)

Thanks everyone i got 1024x768 right now
i show you how to doit tomorrow
right now i have to go

regards,
novan_as

---

### Post by pathematica on 2006-01-01
Query to lutrafobic who offered helpful suggestions following a post by nofun2020[QUOTE=anil_robo]Reboot your machine, and when it asks for username and password, click on the SESSION button and select "failsafe terminal". Then enter your username and password and boot in.

You'll see only a little terminal window in the lower right corner of the screen. TYpe this command :```
sudo dpkg-reconfigure xserver-xorg
``` and press enter.

Follow the directions very carefully. THere is a lot of text on the screen but it's worth reading. After you're done, reboot your machine again, and you should be able to select higher resolutions, just as I  did! :)[/QUOTE]

Dear OtterAter

I have a similar problem, except that I am offered only one choice of resolution (the lowest avaiable, that is 640 x 480). I followed your helpful instructions and attempted to reconfigure the system without success. I would be grateful for any further suggestions.

Unnecessary (beware of the otters) background 
I am attempting to install ubuntu 5.10 (downloaded as an ISO image burned using K3B running under SuSE 9.0) onto an old machine that I self-assembled from spare parts for my mother (it has become available to me as I have bought her a new one which runs the vile XP in an attempt to shield her from the spyware and viruses that bedevilled her W98SE activities). I have also downloaded and installed all of the available updates that were offered by the automatic update function on the first run. 

Necessary background information (no otters in here):
The relevant parts of the old machine are:
Pentium II 333 MHz (underclocked to 300 MHz for stability - my mother lives a long way away from me)
440 LX mainboard running at 66 MHz
Intel i740 8MB AGP graphics card
IBM G54 15" CRT monitor
8 GB hard drive, with all partitions deleted using fdisk prior to a clean install of ubuntu onto the entire disk (without windows cohabitation) 

Attempts at reconfiguration so far (still no otters):
I ran the sudo reconfiguration program as suggested by you. I checked the  various parameters for the IBM G54 and these have been correctly identified by the autodetect facility. I deselected the highest offered resolution (I think it was 1280 x 1024) from those offered by the autodetect, leaving only the lowest three (up to 1024 x 768, which I hoped to specify). I rebooted before trying to set the screen resolution to 1024 x 768 but again I am offered only the lowest resolution of 640 x 480. I have also tried setting the colour depth lower (as low as 8, rather than the preselected 24, in case there was insufficient memory) without success. 

Further unnecessary background (caution is urged; the otter firewall is down):
I also hope to load ubuntu onto my laptop (dual boot with windows XP, which unfortunately I need for other reasons), which I use for work. I am using the old desktop to experiment before doing this. At present, I have SuSE 9.0 as a dual boot on the laptop but I have not been able to make this do certain essential things (including wireless networking). I would prefer to try ubuntu rather than upgrade the SuSE. Despite using SuSE (and despite familiarity with command line protocols in CPM and MSDOS) I still find much about Linux very opaque. In particular, I even find it difficult to install new applications using YAST and rpms. I recently uninstalled openoffice 1.1 and, to my shame, I have been unable to install openoffice 2. I was hoping that ubuntu might prove easier to use. 

Help me, Obi Wan, the Force is growing weak.

---

### Post by pathematica on 2006-01-01
Sorry, I have just noticed that there were two replies to nofun2020's original query; one from lutrafobic and the other from anil_robo. I suspect anil_robo will not understand the references to otters. It should make sense to lutrafobic, honest. Anyway, I would be grateful for advice from anyone, regardless of their opinions of semi-aquatic mustelid carnivores.

---

### Post by pathematica on 2006-01-01
Hello again. I have solved the problem by following a link to a page on the wiki on another thread. For those who follow that might be trying to solve the same problem, this is the link:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

For those not familiar with nano (like me) and who wish to do the equivalent of looking at the diagram on the gear stick of a car before changing gear, this is a link to suitable instructions (I wanted to check how to save the file)

[http://www.tqnyc.org/tutorial/nano/](http://www.tqnyc.org/tutorial/nano/)

The problem in my case was solved using the second suggestion ("Undetected Monitor Specs"). I had to add two lines to the configuration file (opened using "sudo nano /etc/X11/xorg.conf" from the safe terminal accessed as indicated by lutrafobic and anil_robo above) with the details of HorizSync and VertRefresh.

Sorted. Done, done and I'm on to the next one.

Thanks for the help. I'm off to see some otters.

---

### Post by pathematica on 2006-01-01
This is now me on my new (old) linux box. Flippin' brilliant.

---

### Post by nofun2020 on 2006-01-17
Sorry for long time offline :)

Oke everyone this is what I do to make my resolution 1024x768

1. Reboot your machine, and when it asks for username and password, click on the SESSION button and select "failsafe terminal". Then enter your username and password and boot in.

You'll see only a little terminal window in the lower right corner of the screen. TYpe this command :
Code:
sudo dpkg-reconfigure xserver-xorgand press enter. 

This command make me login to blue screen configuration
thnks to lutrafobic and anil_robo :)

2.1. attemp to autodetect video hardware? 
i choose **yes**

2.2. select desired x server driver: 
I choose **mga** because my vga driver is mga

2.3. enter an identifier for your video card:
I just choose **oke** because there is my vga driver

2.4. user of PowerPC machine...
choose **ok**

2.5. please enter the video card's bus identifier 
I choose default then **ok**

2.6. enter the amount of memory (in Kb) to be used by your video card
I type notting then **ok**

2.7. use kernel framebuffer device interface?
I choose **no** because i do not want any problem

2.8. autodetect keyboard layout?
a choose **no**

2.9. for the x server to handle your keyboard correcly...
hit **enter**

2.10. please select keyboard layout
default is **us** then hit enter keyboard

2.11. please select the XKB rule set to use
default is **xorg** then hit enter keyboard (couse i do not know the rule)

2.12. for the x server handle your keyboard correctly...
hit enter keyboard

2.13. please select your keyboard model
default is pc104 then hit enter keyboard

2.14. for the x server to handle your keyboard as you desire, ...
hit enter keyboard

2.15. please select your keyboard variant
leave blank then hit enter keyboard (i used us variant)

2.16. for the x server to handle your keyboard as you desire, ...
hit enter keyboard

2.17. please select your keyboard option
leave blank then hit enter keyboard (couse i do not know)

2.18. Emulate 3 button mouse?
i choose **yes**

2.19. Enable scroll events from mouse wheel?
i choose **yes**

2.20 it is possible to customize...
hit enter keyboard

2.21. select the X org server module that should be load by default
leave default then hit enter keyboard (couse i do not know what it is)

2.22. Write default Files section to configuration file?
i choose **yes**

2.23. writre default DRI section to configuration file?
i choose **yes**

2.24. Attemp monitor auto detection?
i choose **yes**

2.25. Enter an identifier for your monitor
default is **Generic Monitor** (I do not change it, but you can change it for example **Compaq V710**. It just an identifier) then hit enter keyboard

2.26. Select the video modes you like to the x server to use
default is 1024x768, 800x600, and 640x480
I change it to just 1024x768, other not choose by hit space keyboard
then hit enter

2.27. for the x window system grafical user interface...
hit enter keyboard

2.28. please choose the method for selecting your monitor characteristic
i choose **medium** then hit enter keyboard

2.29. please select your monitor's best video mode
default is 1024x768 @ 60Hz
hit enter keyboard

2.30. write monitor sync range to configuration file?
i choose **yes**

2.31. usually 24-bit color is...
hit enter keyboard

2.32. please select your desired default color depth in bits
default is **24** but i choose **16** because i used old vga :)
hit enter keyboard

3. you will come to command line again
tipe **exit** then enter keyboard

4. you will go to login screen again
choose restart

well that is :P
enjoy your day

---

### Post by tkjacobsen on 2006-01-17
To make it a little easyer for yourself use:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
The -phigh option makes dpkg do most of the choices for you. You only have to chooce X server driver and video modes (resolution) yourself...

---

### Post by nofun2020 on 2006-02-03
Ahhh...

That a better idea :)

Thanks a lot ;)

---

