---
title: "X Disabled"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Del Piero on 2007-02-25
OK here we go, i am currently on winxp ever since my Ubuntu got screwed after something bad i did. X is disabled therefor i have no graphics, to cut the story short i had installed the ati drivers via easybuntu but they werent active or actually installed or whatever you may call'it. I had no hardwear acceleration and the videos were slow, dropping frames etc. So i decided to install or activate the ati drivers installed on the system (according to synamptec package manager and easybuntu. I went to the ATI Ubuntu wiki and got [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"). I didnt follow everything in it as i had the assumption that i had the drivers already on my pc (stupid, i know and sorry for that but trust me i am a quick learner). Here are the steps that i did in order.

> sudo gedit /etc/default/linux-restricted-modules-common

Added "fglrx" to the line "DISABLED_MODULES"

**Removed after X failed using windows XP wordpad and deleted linux-restricted-modules-common~ file wich had the same data.**

> sudo aticonfig --initial

Couldent undo this step after X failed

> Note: An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc.

Replaced ati with fglrx

**Replaced fglrx with ati after X failed using windows XP wordpad and deleted Xorg.conf~**

Obviously my unprofessional try to undo what i had done using XP wordpad did not work and i am stuck now without X. I need help...

---

### Post by r4ik on 2007-02-25
Try,

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

Good luck !

---

### Post by Del Piero on 2007-02-25
> **r4ik said:**
> Try,

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

Good luck !

Thanks alot, i followed the guide but didnt follow his steps. When it came to choosing vesa or vga as he said i chose ATI and i also didnt reconfigure the gdm i just did the xserver with the ati settings. Now system working fine but still no graphics accelaration any help would be appreciated.

---

### Post by r4ik on 2007-02-25
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Del Piero on 2007-02-25
> **r4ik said:**
> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

After installing envy:

Installed Ati drivers manually (Legacy)

X server failed

Uninstalled Ati drivers and restored X like last time by choosing ATI instead of VESA

Installed latets ati drivers same thing happend and i restored X in the same way mentioned above.

Now i am really annoyed as i cant watch any movies or play any videos as they are really slow and keep droping frames.

There is some errors though that occured during the installation of the drivers i hope somebody look at them and tell me what to do. I also hope someone check my system and tell me what do i have installed because i am sure after all these tries i have a big big mess.

Errors that occured during the ATI installation using envy

Screen 1

[[IMG]http://img100.imageshack.us/img100/3360/dsc00824cy8.jpg[/IMG]](http://imageshack.us)


Screen 2

[[IMG]http://img529.imageshack.us/img529/7803/dsc00825cs3.jpg[/IMG]](http://imageshack.us)

Screen 3

[[IMG]http://img528.imageshack.us/img528/3932/dsc00826hn9.jpg[/IMG]](http://imageshack.us)

---

### Post by r4ik on 2007-02-25
This is not even a bit funny.
Please try to pm tseliot (forum staff) who is the creator of this script and ask him wtf is going on. (nice please)
I have never seen such a mess and linked a lot of people to that script.
I am very sorry for the inconvenience but my knowledge stops here.

---

### Post by Del Piero on 2007-02-25
> **r4ik said:**
> This is not even a bit funny.
Please try to pm tseliot (forum staff) who is the creator of this script and ask him wtf is going on. (nice please)
I have never seen such a mess and linked a lot of people to that script.
I am very sorry for the inconvenience but my knowledge stops here.

Dont be sorry, i am greatfull you were trying to help. Anyway installed all the codecs in the synaptec manager including vlc player, tried to play a video with it and it worked fine its just totem. I dont know what i have installed now or if i have 3D rendering or not but i am sure i have a big mess. I will be greatfull if you can help me see what do i have installed and if i have actuall 3d renderring or not i been working on this since yesterday.

---

### Post by r4ik on 2007-02-25
In terminal fglrxinfo
please post it might help.

---

### Post by Del Piero on 2007-02-25
> **r4ik said:**
> In terminal fglrxinfo
please post it might help.

There it is mate:

> omar@Ubuntuserv:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


---

### Post by r4ik on 2007-02-25
And you're  glxgears -printfps  please ?

---

### Post by Del Piero on 2007-02-25
It dosent seem to be stoping soon so far:

> omar@Ubuntuserv:~$ glxgears -printfps
1499 frames in 5.4 seconds = 277.732 FPS
1482 frames in 5.4 seconds = 272.381 FPS
1368 frames in 5.3 seconds = 256.860 FPS
1474 frames in 5.4 seconds = 273.928 FPS
1482 frames in 5.4 seconds = 274.409 FPS
1368 frames in 5.1 seconds = 268.778 FPS
1482 frames in 5.4 seconds = 274.517 FPS
1368 frames in 5.1 seconds = 270.763 FPS
1482 frames in 5.4 seconds = 274.588 FPS
1368 frames in 5.1 seconds = 270.818 FPS
1482 frames in 5.4 seconds = 272.842 FPS
1368 frames in 5.1 seconds = 270.179 FPS
1482 frames in 5.4 seconds = 274.501 FPS
1482 frames in 5.4 seconds = 275.075 FPS
1368 frames in 5.1 seconds = 268.536 FPS
1482 frames in 5.4 seconds = 274.455 FPS
1368 frames in 5.1 seconds = 267.830 FPS
1482 frames in 5.1 seconds = 288.404 FPS
1368 frames in 5.1 seconds = 266.782 FPS
1596 frames in 5.2 seconds = 309.486 FPS
1596 frames in 5.2 seconds = 306.517 FPS
1596 frames in 5.2 seconds = 308.029 FPS
1596 frames in 5.1 seconds = 315.226 FPS
1596 frames in 5.1 seconds = 310.184 FPS
1607 frames in 5.1 seconds = 317.474 FPS
1596 frames in 5.1 seconds = 313.489 FPS
1596 frames in 5.2 seconds = 308.287 FPS
1596 frames in 5.1 seconds = 312.478 FPS
1596 frames in 5.2 seconds = 308.817 FPS
1596 frames in 5.1 seconds = 315.292 FPS
1596 frames in 5.1 seconds = 315.235 FPS
1596 frames in 5.1 seconds = 311.459 FPS
1596 frames in 5.1 seconds = 315.629 FPS
1596 frames in 5.1 seconds = 310.596 FPS
1482 frames in 5.2 seconds = 283.152 FPS
1368 frames in 5.1 seconds = 270.217 FPS
1368 frames in 5.1 seconds = 267.958 FPS
1368 frames in 5.0 seconds = 272.913 FPS
1368 frames in 5.1 seconds = 268.334 FPS
1368 frames in 5.0 seconds = 273.112 FPS
1368 frames in 5.1 seconds = 266.425 FPS
1368 frames in 5.1 seconds = 270.066 FPS
1368 frames in 5.1 seconds = 267.972 FPS
1368 frames in 5.1 seconds = 270.732 FPS
1368 frames in 5.1 seconds = 268.685 FPS
1368 frames in 5.0 seconds = 272.693 FPS
1368 frames in 5.1 seconds = 266.064 FPS
1368 frames in 5.0 seconds = 272.669 FPS
1368 frames in 5.1 seconds = 268.113 FPS
1368 frames in 5.0 seconds = 273.000 FPS
1368 frames in 5.1 seconds = 268.092 FPS
1368 frames in 5.0 seconds = 271.087 FPS
1368 frames in 5.1 seconds = 268.475 FPS
1368 frames in 5.0 seconds = 272.192 FPS
1368 frames in 5.1 seconds = 268.486 FPS
1368 frames in 5.0 seconds = 272.722 FPS
1368 frames in 5.0 seconds = 272.850 FPS
1368 frames in 5.1 seconds = 265.723 FPS
1460 frames in 5.4 seconds = 271.506 FPS
1368 frames in 5.1 seconds = 267.871 FPS
1368 frames in 5.0 seconds = 272.150 FPS
1368 frames in 5.1 seconds = 267.607 FPS
1368 frames in 5.4 seconds = 252.879 FPS
1254 frames in 5.1 seconds = 244.758 FPS
1368 frames in 5.1 seconds = 270.042 FPS
1482 frames in 5.3 seconds = 281.679 FPS
1482 frames in 5.4 seconds = 273.747 FPS
1368 frames in 5.3 seconds = 258.785 FPS
1368 frames in 5.0 seconds = 273.482 FPS
1368 frames in 5.0 seconds = 273.126 FPS
1368 frames in 5.2 seconds = 264.314 FPS
1482 frames in 5.1 seconds = 288.407 FPS
1482 frames in 5.8 seconds = 255.183 FPS
1368 frames in 5.2 seconds = 264.571 FPS
1596 frames in 5.2 seconds = 304.088 FPS
1596 frames in 5.1 seconds = 316.025 FPS
1596 frames in 5.0 seconds = 317.965 FPS
1596 frames in 5.1 seconds = 313.996 FPS
1596 frames in 5.0 seconds = 318.182 FPS
1482 frames in 5.1 seconds = 288.388 FPS
1596 frames in 5.1 seconds = 314.416 FPS
1482 frames in 5.2 seconds = 285.644 FPS
1368 frames in 5.1 seconds = 270.518 FPS
1482 frames in 5.4 seconds = 274.492 FPS
1368 frames in 5.1 seconds = 270.063 FPS
1482 frames in 5.4 seconds = 273.580 FPS
1368 frames in 5.1 seconds = 267.646 FPS
1482 frames in 5.4 seconds = 273.954 FPS
1368 frames in 5.1 seconds = 270.108 FPS
1482 frames in 5.4 seconds = 274.104 FPS
1368 frames in 5.1 seconds = 269.976 FPS


---

### Post by r4ik on 2007-02-25
A bit in advance sorry,

glxinfo |grep rendering

should tell you more it has to look like this,

:~$ glxinfo |grep rendering
direct rendering: Yes

---

### Post by r4ik on 2007-02-25
I got to go i have 4 hours sleep left and need them.

Good luck !

---

### Post by Del Piero on 2007-02-25
:( 

> omar@Ubuntuserv:~$ glxinfo |grep rendering
direct rendering: No

---

### Post by tseliot on 2007-02-26
Del Piero:
1) does the Internet connection work in Ubuntu?
2) can I see your /etc/apt/sources.list ?

---

### Post by Del Piero on 2007-02-26
> **tseliot said:**
> Del Piero:
1) does the Internet connection work in Ubuntu?
2) can I see your /etc/apt/sources.list ?

Yes internted works fine, and envy was able to download the packages before the installations if thats what you want to know.

/ect/apt/sources.list

> #
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

#  deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-fre
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.albertomilone.com/drivers/dapper/latest/32bit](http://www.albertomilone.com/drivers/dapper/latest/32bit) binary/



---

### Post by Del Piero on 2007-02-26
Help please :(

---

### Post by r4ik on 2007-02-26
Oke here we go again first replace you're sources list with this,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Just follow the guide exactly.

After that try Envy again just follow instructions please.

---

### Post by Del Piero on 2007-02-26
> **r4ik said:**
> Oke here we go again first replace you're sources list with this,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Just follow the guide exactly.

After that try Envy again just follow instructions please.

I am following the instructions and i replaced the files and clicked save but i didnt do the final commands they mentioned in the guide to save'it just yet. Gedit opened normally and everything and i was able to replace the information inside with the one you gave me but this message appeared in the terminal.

> (gedit:8311): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Should i countinue normally?

---

### Post by Del Piero on 2007-02-26
Also if it counts when i used envy last time it didnt have trouble downloading it had problems while installing (the screens i posted earlier).

---

### Post by r4ik on 2007-02-26
If you do not save the file it will not function end of story.
If you dont follow instructions from anyone who is trying to help and keep mixing them with you're own idea's nobody can help you properly.
I am not gonna loose sleep over this again.
One advice before i go if you follow a guide follow it to the letter or just don't.

Good luck !

---

### Post by Del Piero on 2007-02-26
> **r4ik said:**
> If you do not save the file it will not function end of story.
If you dont follow instructions from anyone who is trying to help and keep mixing them with you're own idea's nobody can help you properly.
I am not gonna loose sleep over this again.
One advice before i go if you follow a guide follow it to the letter or just don't.

Good luck !

I am gonna follow the guide but i was asking if the error that i got at the terminal was normal or not. I appreciate your tries to help me and the time you waste while doing so so i am just trying to be helpfull by providing you with information about everything happening.

---

### Post by Del Piero on 2007-02-26
Here is the output after i followed the guide:

> omar@Ubuntuserv:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
omar@Ubuntuserv:~$ sudo apt-get update
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [48.5kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [3530B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 1331kB in 1m9s (19.1kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages (/var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_dapper_free_binary-i386_Packages)
[B]W: Duplicate sources.list entry [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages (/var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_dapper_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
[/B]

is that normal?

---

### Post by r4ik on 2007-02-26
Proceed what on earth could go wrong.

---

### Post by Del Piero on 2007-02-26
> **r4ik said:**
> Proceed what on earth could go wrong.

I did, read the above post. Now give envy a try? if yes should i go for automatic install or manual, if i choose manual should i go for Legacy or Latest. I just wanna do it right this time its been more 48 hours with this problem and i still have a big list after that to start actually using the system.

---

### Post by r4ik on 2007-02-26
Automatic'

---

### Post by r4ik on 2007-02-26
_

---

### Post by Del Piero on 2007-02-26
Just did an auto install and rebooted and X didnt fail like the usual. Now i will do the tests we did earlier and paste the outputs.

---

### Post by Del Piero on 2007-02-26
fglrxinfo
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

glxgears -printfps
> 4209 frames in 5.0 seconds = 841.782 FPS
7636 frames in 5.0 seconds = 1527.103 FPS
7922 frames in 5.0 seconds = 1584.291 FPS
7230 frames in 5.0 seconds = 1445.913 FPS
8213 frames in 5.0 seconds = 1642.592 FPS
8213 frames in 5.0 seconds = 1642.508 FPS
8212 frames in 5.0 seconds = 1642.363 FPS
8205 frames in 5.0 seconds = 1640.860 FPS
8184 frames in 5.0 seconds = 1636.754 FPS
8209 frames in 5.0 seconds = 1641.664 FPS
8212 frames in 5.0 seconds = 1642.246 FPS
8213 frames in 5.0 seconds = 1642.437 FPS
8212 frames in 5.0 seconds = 1642.227 FPS
7912 frames in 5.0 seconds = 1582.345 FPS
7760 frames in 5.0 seconds = 1551.973 FPS
7001 frames in 5.0 seconds = 1400.100 FPS

glxinfo |grep rendering
> direct rendering: Yes

Its all looks good, Totem still plays the videos slow but i guess thats the player problem. Anyway i really dont know how to thank you for this, and sorry for being an annoying prick. You guys were really helpfull and i really really appreciate'it i really mean it. thanks again. you rock :guitar: .

---

### Post by r4ik on 2007-02-26
When you got the time ditch Totem and use Mplayer witch is the better player i.m.o

Good luck !!

---

### Post by r4ik on 2007-02-26
Mark the thread resolved by reading this please,

[http://www.ubuntuforums.org/showthread.php?t=343754&highlight=mark+resolved](http://www.ubuntuforums.org/showthread.php?t=343754&highlight=mark+resolved)

---

### Post by Del Piero on 2007-02-26
> **r4ik said:**
> Mark the thread resolved by reading this please,

[http://www.ubuntuforums.org/showthread.php?t=343754&highlight=mark+resolved](http://www.ubuntuforums.org/showthread.php?t=343754&highlight=mark+resolved)

Done

once again thanks alot :)

---

### Post by r4ik on 2007-02-26
Glad it worked !

---

