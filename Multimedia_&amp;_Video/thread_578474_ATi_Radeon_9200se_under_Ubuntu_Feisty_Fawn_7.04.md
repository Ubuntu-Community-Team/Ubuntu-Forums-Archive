---
title: "ATi Radeon 9200se under Ubuntu Feisty Fawn 7.04"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by UberrrSauce on 2007-10-17
Okay so I'm running Ubuntu Feisty Fawn 7.04 on my low end machine, dual booting with XP. I'm trying to get UT2K4 installed on here but to do that I'm going to need 3D acceleration. I also wish to get the tv-out on my card functioning - at the moment all I get on my TV is static... *coloured* static that resembles the current image on the screen :P

The card functions flawlessly under WinXP home.

Anyway so I went to the ATi website and downloaded the Ubuntu drivers but I get the following output in the terminal.

```
hillam@P4-1:~/Desktop$ ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

I've tried installing fglrx as it says in the ATi documentation that it is no longer included in the packages, however they only provide them in .rpm format. Furthermore the check.sh script they provide gives me the error 

```
hillam@P4-1:~/Desktop$ bash ./check.sh
=====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

```

I am running the script from the console, and I do have console ownership. Anyway so I just decided to try install the cglrfx packages available from the ATi website and hope that it worked, however the packages are only available in .rpm repositories so I had to convert them to .deb repositories using alien but I cannot install these either as I get the error 

```
hillam@P4-1:~/Desktop$ sudo dpkg -i ./fglrx-4-3-0_8.28.8-2_i386.deb
(Reading database ... 105756 files and directories currently installed.)
Unpacking fglrx-4-3-0 (from .../fglrx-4-3-0_8.28.8-2_i386.deb) ...
dpkg: error processing ./fglrx-4-3-0_8.28.8-2_i386.deb (--install):
 trying to overwrite `/usr/share/man/man8/atieventsd.8.gz', which is also in package xorg-driver-fglrx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
[: 262: abort-install: bad number
Errors were encountered while processing:
 ./fglrx-4-3-0_8.28.8-2_i386.deb

```

Okay so nevermind about that fglrx stuff, I just found out that The 'fglrx' driver does not support cards earlier than the 9500, so scratch that.

Please help me :(

I want to play UT2K4 :(

---

### Post by UberrrSauce on 2007-10-18
*bump*

I know, It hasn't quite been 24 hours yet but I'm going to to sleep soon and would like to get this working by tomorrow night or over the weekend.

---

### Post by svneighty on 2007-10-18
My ATI Radeon 9250 started working after I upgraded to 7.10; I would recommend you to do the same if you're able to. :-)

---

### Post by tab0u on 2007-10-19
@svneighty :
I have also ati radeon 9250.Can you tell me which driver have you select in ubuntu 7.10?
Sorry for my bad english :(

---

### Post by UberrrSauce on 2007-12-16
just upgraded to 7.10 tonight and still no dice. Why can some people get this working but others can't? I really expected better compatibility from Ubuntu - I always hear such great things about it and would really love to believe it. Does ANYBODY know ANYTHING about how I can get this working? :(

---

