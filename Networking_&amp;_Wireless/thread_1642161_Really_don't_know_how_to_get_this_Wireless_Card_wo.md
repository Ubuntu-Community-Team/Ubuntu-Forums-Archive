---
title: "Really don't know how to get this Wireless Card working."
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by serpx on 2010-12-10
I posted this elsewhere, but it doesn't seem like the people in the area know much on the subject -- I just found this area of the forum, and I'm really hoping someone can at least point me in the right direction.

I checked the stickys regarding wireless cards that are supported with ubuntu, but navigating everything really went over my head as I don't know much about the subject matters.  I REALLY want to get rid of Windows as it destroys my computer -- Ubuntu runs awesome, but I can't use my wireless card.  The big hump: **no functional ethernet port.**  Bold because, from my research so far, that makes things more complicated.

Anyways, here's the problem: Again,  I hate Windows, I want to get rid of it so  I downloaded and installed Ubuntu.  Everything works great, except I  cannot connect to the internet, or figure out a way to connect.

I want to get my wireless card  working.  I have the latest Ubuntu installed (Netbook edition), and  here's some basic information about my laptop:

It's a Dell Inspiron 1318.  The wireless card is a Dell Wireless 1395  WLAN Mini-Card. Chipset: BCM4315.  I'm currently using Windows Vista Home Premium to  browse the web.  

If anyone can give me some ideals to try, or point me to somewhere that  may help me out, I'd really appreciate it, because I would REALLY like  to fully experience Ubuntu, and hopefully get rid of processing-hogging  Windows.   :smile:

Also, Ubuntu says I don't have the firmware or whatever for the  wireless.  I don't know, I assume a driver just needs to be found and  installed that operates on Ubuntu.  Please, any ideas would be appreciated!  This is really the last place I know to go for help haha.  I've googled for hours, and even asked a fellow friend whos pretty smart on Ubuntu matters.

---

### Post by bkratz on 2010-12-10
Your 1395 card is listed as support by the STA driver. Normally, with ethernet it would be simple, but since that is not an option you might want to look at the read me file here

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and see one method available which could be downloaded remotely and transfered to your system via key.

---

### Post by grahammechanical on 2010-12-10
A lot of people feel the same about Windows but knowing how you feel does not help us help you. 

Have you tried going to System>Administration>Additional drivers?

What information do you get when you try out the left and right click options of the network manager icon?

This is a link to a trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by serpx on 2010-12-10
Just wanted to say I really appreciate you guys taking your time to help with this issue.  I will look into your thoughts and post back if needed.  Yes, saying how much I hate Windows is irrelevant, but, I just like vocalizing it haha.

---

### Post by serpx on 2010-12-10
So close.  The "Additional Drivers" component of Ubuntu just gives me an error about trying to get stuff from the internet, and then the next screen pops up supposedly lists additional drivers I can "Enable", but, nothing was on the list.

Anyways, I downloaded the linux supported driver onto my USB drive, and followed its directions.  When attempting to do "make" under the terminal, I got this message:

```
odin@ubuntu:~/Downloads/wireless/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  LD      /home/odin/Downloads/wireless/hybrid_wl/built-in.o
/bin/sh: ar: not found
make[2]: *** [/home/odin/Downloads/wireless/hybrid_wl/built-in.o] Error 127
make[1]: *** [_module_/home/odin/Downloads/wireless/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2
```

I'm assuming I don't have all the right stuff to make a kernal or whatever.  The readme file recommends me to do this:

```
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux
```

But amazingly that requires the internet I do not have.  Does anyone have any idea of where I can download these files?  I'll put them on my USB and manually put the files in their proper places on Ubuntu.

---

### Post by bkratz on 2010-12-10
Here is another method that was originally written for 10.04, but should work for 10.10 (if that is what you have). Apparently the files you need are on the installation disk or installation thumbdrive.

[http://ubuntuforums.org/showpost.php?p=9223467&postcount=21](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21)


and still another about 1/2 way down the page STA no internet access

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43) - No Internet access

---

### Post by serpx on 2010-12-10
> **bkratz said:**
> Here is another method that was originally written for 10.04, but should work for 10.10 (if that is what you have). Apparently the files you need are on the installation disk or installation thumbdrive.

[http://ubuntuforums.org/showpost.php?p=9223467&postcount=21](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21)


and still another about 1/2 way down the page STA no internet access

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43) - No Internet access

Awesome.  I'll try this tonight, and if it works, change my prefix to solved.  Thanks so much for the links!

---

### Post by bkratz on 2010-12-10
Well only you can change your prefix to solved (under the tools menu), since only you can determine if it is! Anyway, good luck tonight.

---

### Post by serpx on 2010-12-11
Issue solved.  Thanks a lot for the help -- and I misworded, I meant I'll change it, if figure out how haha.

I had to do a lot more work than what you presented me, but the links provided was all that was needed.  I'm currently using Ubuntu now and it's great!

---

### Post by bkratz on 2010-12-11
> **serpx said:**
> Issue solved.  Thanks a lot for the help -- and I misworded, I meant I'll change it, if figure out how haha.

I had to do a lot more work than what you presented me, but the links provided was all that was needed.  I'm currently using Ubuntu now and it's great!

I really am glad you resolved it--it would have been easy if you had ethernet access!

---

