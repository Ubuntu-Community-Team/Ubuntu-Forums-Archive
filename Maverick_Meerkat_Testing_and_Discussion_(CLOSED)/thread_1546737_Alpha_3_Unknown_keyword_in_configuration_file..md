---
title: "Alpha 3: Unknown keyword in configuration file."
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-08-05
I can not get alpha 3 to boot from liveusb.

Unknown [s]keyboard[/s] *keyword* in configuration file.
boot:

Attached screenshot (sorry for poor quality). First line normal. I'm guessing second line is normal. Then for whatever reason doesn't boot.

Same problem on my nettop. And that was after I reinstalled to usb.

Anyone else seeing same problem?

I downloaded normal 32bit desktop edition torrent. Going to try other versions (kubuntu). Alpha 2 worked fine. I have ubuntu 10.10 with updates installed on nettop, so must be some startup error with default alpha 3?

EDIT:
Replace keyboard with keyword.

---

### Post by ranch hand on 2010-08-05
I can't find it now but that was the bug that caused us to have a rebuild in ISO testing of the desktop amd64 ISO.  I am sure you can find it if you search on launchpad (don't remember any workarounds).

It could be that it was not fixed for all hardware configurations.  This is why we need as many ISO testers  as we can scrap up.

I would keep trying the dailies and see if it gets straightened out after you file on the bugger (launchpad should find the bug from testing for you that way).

---

### Post by andrewabc on 2010-08-05
Can't find bug. Google doesn't show anything.

Well guess I'll download 64 bit desktop, since I already have 10.10 installed on other computer.

If this affects lots of people (normal 32bit desktop livecd/usb), expect complaints soon. :O

---

### Post by mdurham on 2010-08-05
> **andrewabc said:**
> I can not get alpha 3 to boot from liveusb.

Unknown keyboard in configuration file.
boot:


Are you sure it said "keyboard"? I thought mine (usb stick install) said "keyword".
I could be wrong though, I have been before.

---

### Post by andrewabc on 2010-08-05
> **mdurham said:**
> Are you sure it said "keyboard"? I thought mine (usb stick install) said "keyword".
I could be wrong though, I have been before.

Now that you mention it and I look at screenshot, it most likely says keyword.

---

### Post by cariboo on 2010-08-06
I had the same **keyword** error when trying to boot a daily iso on a usb device. Burning the iso to cd and installing worked without any errors.

---

### Post by arpanaut on 2010-08-06
@ andrewabc
Here's the fix for that:
[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

Had to use it tonight, worked great.
Man, the new live installer is sweet! 
Been using the Alt. installer for the past few years as it was easier
but, this new live one is nice.

---

### Post by andrewabc on 2010-08-06
I tried 64 bit. Same problem.

@ arpanaut
I looked over that thread but don't see a solution. I see that someone found the problem and the file involved but doesn't say what to do. And I tried locating that file but it was not on 64bit liveusb.

I'll try kde version, but I suspect same problem.

I use ubuntu 9.10. I suppose that old usb creator is causing problems?

Hmm, my nettop has maverick installed. Does this mean I can put my .iso on it and install to liveusb and it should work? Gonna try that instead. Also, would burning livecd work (then I could create liveusb from it)? This is a problem with older usbcreator?

EDIT:
Making liveusb in maverick install works!
So I'm guessing the problem is with older usbcreator. So create livcd and make liveusb from that would solve some of the problems. Although would be nice to not have to burn cd.

EDIT:
Umm, I thought shotwell replaced f-spot as default image editor? How come my alpha 3 32bit has f-spot but no shotwell? I am running  alpha 3 as intel vid driver is latest version (which wasn't in alpha 2, and I havn't downloaded any dailycd).

If a mod could edit title of thread that would be great.

EDIT:
Love simplescan. Detects scanner, and no more need to compile my own driver.

Anyone else when opening firefox and type in web address google custom search first appears? Then if you type it in again it goes to proper website? Hmm, can't reproduce it now.

---

### Post by decibyte on 2010-08-09
> **andrewabc said:**
> I looked over that thread but don't see a solution. I see that someone found the problem and the file involved but doesn't say what to do.

VMC actually mentions the solution in #1. I didn't see it either, but having a closer look, I saw that "ui" was removed from the last line in the file. I just tried that, and it works :)

---

### Post by krash1220 on 2010-08-10
[QUOTE=andrewabc;9685038]I tried 64 bit. Same problem.

@ arpanaut
I looked over that thread but don't see a solution. I see that someone found the problem and the file involved but doesn't say what to do. And I tried locating that file but it was not on 64bit liveusb.

I'll try kde version, but I suspect same problem.

I use ubuntu 9.10. I suppose that old usb creator is causing problems?

Hmm, my nettop has maverick installed. Does this mean I can put my .iso on it and install to liveusb and it should work? Gonna try that instead. Also, would burning livecd work (then I could create liveusb from it)? This is a problem with older usbcreator?

EDIT:
Making liveusb in maverick install works!
So I'm guessing the problem is with older usbcreator. So create livcd and make liveusb from that would solve some of the problems. Although would be nice to not have to burn cd.
  

What I did to get around it was to format the usb drive, run syslinux under Lucid, then copied  the syslinux directory from my Lucid usb install to the second usb , mounted the Maverick ISO and copied all of the files and folders except the isolinux folder to the usb drive and it now boots just fine.

---

### Post by VMC on 2010-08-10
The problem lies in the older syslinux. If you create a usb/cd using Lucid and older releases, it uses the older syslinux. 

Maverick syslinux has been updated to syslinux version 4.

The file located at "/syslinux/syslinux.cfg" when created shows the contents below:

```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
**[COLOR="Red"]ui[/COLOR]** gfxboot bootlogo
```

If you created this with the older syslinux, you need to remove the "ui" keyword.

---

### Post by JayminP on 2010-08-10
i tried to remove 'ui' but it give me error....

Unknown keyword in configuration file: gfxboot

---

### Post by VMC on 2010-08-10
> **JayminP said:**
> i tried to remove 'ui' but it give me error....

Unknown keyword in configuration file: gfxboot

With your USB/cd plugged in type this. Use your own ***media*** location.

For example:
```
$ head -2 /media/Boot/ldlinux.sys

SYSLINUX 3.63 Debian-2008-07-15 
```

Some time later: Read this [Bug#608382]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382") report on the matter.

---

### Post by JayminP on 2010-08-10
i think i will just wait for 10.04.1 which i think should be released on Aug 12th...
according to [https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

---

### Post by andrewabc on 2010-08-10
> **JayminP said:**
> i think i will just wait for 10.04.1 which i think should be released on Aug 12th...
according to [https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

I doubt that will have the fix for usb-creator.

Unless you mean install 10.04.1 until 10.10 final released.

---

### Post by JayminP on 2010-08-10
if next release won't work its fine...untill 10.10 I'm planning to use live-usb for fun...alpha 2 live usb works for me anyway...i guess i will keep on using alpha 2 until next one that works for me :)

current ubuntu stable doesn't support my laptop...so I can't use that either...

so excited for 10.10....

---

### Post by andrewabc on 2010-08-10
> **JayminP said:**
> if next release won't work its fine...untill 10.10 I'm planning to use live-usb for fun...alpha 2 live usb works for me anyway...i guess i will keep on using alpha 2 until next one that works for me :)

current ubuntu stable doesn't support my laptop...so I can't use that either...

so excited for 10.10....

The problem is in older usb-creator program.

If you can't figure out the 'fix', you could burn the .iso of 10.10 to cd-rw, boot it up, and use usb creator to create alpha 3 liveusb.

---

### Post by JayminP on 2010-08-10
i will try that with cd/dvd and create live usb...its cool if its stays as live-cd/dvd i just need it to boot up

---

### Post by stone1343 on 2010-08-11
I used Startup Disk Creator on today's Ubuntu, Kubuntu and Xubuntu iso's (running on a current Ubuntu Lucid). The only one that worked "out of the box" was Ubuntu. Both Kubuntu and Xubuntu had the 'ui' in syslinux.cfg, removed them it worked fine.

---

### Post by JayminP on 2010-08-11
ah im gone download it ... is the the correct one? 
11-Aug-2010 07:35
link [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

if not can you please provide the link...

tx.

---

### Post by zulli1942 on 2010-08-17
Removing the 'ui' worked for me too - netbook edition on a dell 10v. Thanks for the info!

---

### Post by quixote on 2010-08-18
I was trying to install a 64-bit Maverick alpha3 using LiveUSB.  Same problem.  Removing the "ui" on the last line of syslinux.cfg worked for me too.

---

### Post by JayminP on 2010-08-19
> **quixote said:**
> I was trying to install a 64-bit Maverick alpha3 using LiveUSB.  Same problem.  Removing the "ui" on the last line of syslinux.cfg worked for me too.

were you using alpha 3 or daily build...because im trying to get 64-bit too...
tx

---

### Post by ranch hand on 2010-08-19
As far as I know the CD and DVD images work fine.  Burn to RW.  Install.  No problem.

The other bugs will work out in time.

---

### Post by JayminP on 2010-08-20
Should option help me boot....work?

Basically it creates adds option during boot up to boot from img(stored in computer)...without cd/dvd

---

### Post by quixote on 2010-08-20
JayminP: as far as I know, it was just alpha3.  This file: maverick-desktop-amd64.iso from this link: [http://cdimage.ubuntu.com/releases/maverick/alpha-3/](http://cdimage.ubuntu.com/releases/maverick/alpha-3/)

---

### Post by Untitled_No4 on 2010-08-21
It is also possible to work around this problem.
When you get this error just type help and press enter. You are then presented with a menu, and then you just have to press enter again. After that it's all back to normal.


Edit: Help -> help.

---

### Post by quixote on 2010-08-21
Thanks for the tip!

---

### Post by JayminP on 2010-08-22
i got it working with live cd & installed it on USB...solved 4 me...tx guys for help

---

### Post by shihkster1015 on 2010-08-26
Burn it to a DVD if you can't boot from a  USB
that' what i did and it worked

---

### Post by kshmatov on 2010-08-27
I still get the error on booting from USB with maveric-netbook (08/27/2010).
I remove 'ui' from last line in syslinux.cfg and now get:
```
Unknown keyword in configuration file: gfxboot
```

I don't have CD/DVD on my netbook, so can't try to boot from it. And I don't get the command line after this error and can't type anything.

---

### Post by altonbr on 2010-09-03
I have this same error using liveusb-creator on Linux Mint 9 (Ubuntu 10.04) and trying to use maverick-desktop-amd64.iso, zsynced to the latest 10.10 beta.

I looked at my *syslinux.cfg* file and it already contained the proper configuration as per this thread: [http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
```

---

### Post by arpanaut on 2010-09-03
There was an update yesterday in Lucid that was aimed at correcting this behavior of Startup Disk Creator.  I haven't tried using it yet, but the issue should be corrected re: Lucid now.

Meant to post this yesterday but got distracted.

---

### Post by richardamullens on 2010-10-01
This problem still exists as a hurdle for would be users in the Maverick release candidate.

After removing "ui " as suggested above I was able to boot from my flash disk successfully.

---

