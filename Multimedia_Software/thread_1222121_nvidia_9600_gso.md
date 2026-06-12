---
title: "nvidia 9600 gso"
date: 2009-07-24
forum: Multimedia Software
---

### Post by dgun on 2009-07-24
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Hello all![/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Please excuse any n00bery in this, my first post.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I'm running 2.6.28-13 kernel, Ubuntu 9.04, my video card is a nvidia 9600 gso/PCI-e/ with 750 or so MB of RAM, an Intel dual core processor. I have an ASUS pq5 motherboard also, with the latest BIOS update.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I have a 64 bit system, but I first installed the 32 bit OS, worried about compatibility and support, etc. [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]When I enabled visual effects from the desktop it said it needed a driver, it found it and installed it, requiring a reboot. I rebooted the system and it opened in 'low graphics mode', an X desktop I suppose with an error message, something similar to:[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3](EE) NVIDIA(0): Failed to initialize the NIVIDIA kernel module.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3](EE) NVIDIA(0):Screen found, but none with a usable configuration[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]So I did some googling, tried some things, including downloading the driver from nvidia and running their setup program, with the same result.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Now when I say I tried some things, I mean I spent several hours over several days trying various tips and instructions I found browsing forums such as this, and also reading the NVIDIA readme file. Nothing worked.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]However, I decided to try the 64 bit OS. So I installed it alongside the 32 bit version, opened up the display properties window, enabled visual effects, it installed the NVIDIA driver the first time with no problems and no errors.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]In 32bit Ubuntu, the system was able to detect the card and would report the correct hardware, but could not use the driver for some reason. Or, am I totally confused? I did not notice any specification on the video card that limited it to use with 64bit systems.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Another thing to note, on boot I get PCI bug[0000000001] or something very close to that. I checked ASUS website and did not find anything about it, but I can't help but suspect it is related to the problem.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]There is also some very noticeable lagging when browsing the web with Firefox, of which I’m fairly confident is related to the video card also. The reason being I have tried other browsers and the speed is the same. The package manager, however, downloads at a high rate, as does a Windows system on the same connection.[/SIZE][/FONT][/FONT][/COLOR]
 
 
[FONT=Arial][SIZE=3]I am hoping that maybe one of the Gurus here could tell what was going on based on what I describe above. I am posting this from work, so I don’t have access to my error logs and other info, which I will be happy to post those later.[/SIZE][/FONT]
[FONT=Arial][SIZE=3][/SIZE][/FONT] 
[FONT=Arial][SIZE=3]Incidentally, if I don’t run into snags with the 64 bit system, I’ll just keep running it (although I have not tried my video capture card yet).[/SIZE][/FONT]

---

### Post by theparticle010 on 2009-08-18
I am having the same problem... I wish the drivers worked... I guess it is time to upgrade to 64 bit though...

---

