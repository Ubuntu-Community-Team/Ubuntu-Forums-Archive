---
title: "I downloaded some updates and now natty doesn't work"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aviramof on 2011-02-19
```
Commit Log for Sat Feb 19 18:04:23 2011


removed:
libindicator2

upgraded:
indicator-applet (0.4.8-0ubuntu1) to 0.4.9-0ubuntu1
indicator-applet-appmenu (0.4.8-0ubuntu1) to 0.4.9-0ubuntu1
indicator-applet-complete (0.4.8-0ubuntu1) to 0.4.9-0ubuntu1
indicator-applet-session (0.4.8-0ubuntu1) to 0.4.9-0ubuntu1
indicator-application (0.2.93-0ubuntu2) to 0.2.93-0ubuntu3
indicator-appmenu (0.1.94-0ubuntu1) to 0.1.95-0ubuntu1
indicator-datetime (0.1.93-0ubuntu1) to 0.1.94-0ubuntu1
indicator-me (0.2.13-0ubuntu1) to 0.2.13-0ubuntu2
indicator-messages (0.3.91-0ubuntu1) to 0.3.92-0ubuntu1
indicator-session (0.2.13-0ubuntu1) to 0.2.14-0ubuntu1
indicator-sound (0.5.9-0ubuntu1) to 0.6.0-0ubuntu1
libappindicator1 (0.2.95-0ubuntu1) to 0.2.95-0ubuntu2
linux-generic (2.6.38.3.17) to 2.6.38.4.18
linux-headers-generic (2.6.38.3.17) to 2.6.38.4.18
linux-image-generic (2.6.38.3.17) to 2.6.38.4.18
python-appindicator (0.2.95-0ubuntu1) to 0.2.95-0ubuntu2
unity (3.4.4-0ubuntu1) to 3.4.4-0ubuntu2
unity-common (3.4.4-0ubuntu1) to 3.4.4-0ubuntu2

installed:
libindicator3 (0.3.19-0ubuntu1)
linux-headers-2.6.38-4 (2.6.38-4.31)
linux-headers-2.6.38-4-generic (2.6.38-4.31)
linux-image-2.6.38-4-generic (2.6.38-4.31)
```

What can i do now?

Thanks in advance.

---

### Post by zika on 2011-02-19
What is the precise meaning of &#8222;now natty doesn't work&#8220;...?
I did (I think) the same upgrade lately...
```
Start-Date: 2011-02-18  18:03:59
Commandline: apt-get dist-upgrade
Install: libindicator3:amd64 (0.3.19-0ubuntu1, automatic)
Upgrade: unity:amd64 (3.4.4-0ubuntu1, 3.4.4-0ubuntu2), indicator-me:amd64 (0.2.13-0ubuntu1, 0.2.13-0ubuntu2), unity-common:amd64 (3.4.4-0ubuntu1, 3.4.4-0ubuntu2), indicator-applet:amd64 (0.4.8-0ubuntu1, 0.4.9-0ubuntu1), indicator-sound:amd64 (0.5.9-0ubuntu1, 0.5.9-0ubuntu2), indicator-messages:amd64 (0.3.91-0ubuntu1, 0.3.92-0ubuntu1), indicator-applet-session:amd64 (0.4.8-0ubuntu1, 0.4.9-0ubuntu1), python-appindicator:amd64 (0.2.95-0ubuntu1, 0.2.95-0ubuntu2), indicator-appmenu:amd64 (0.1.94-0ubuntu1, 0.1.95-0ubuntu1), libappindicator1:amd64 (0.2.95-0ubuntu1, 0.2.95-0ubuntu2), indicator-session:amd64 (0.2.13-0ubuntu1, 0.2.14-0ubuntu1), indicator-datetime:amd64 (0.1.93-0ubuntu1, 0.1.94-0ubuntu1), indicator-application:amd64 (0.2.93-0ubuntu2, 0.2.93-0ubuntu3)
Remove: libindicator2:amd64 (0.3.18-0ubuntu1)
End-Date: 2011-02-18  18:04:25
```
among many others...

---

### Post by aviramof on 2011-02-19
Well it reaches the purple ubuntu screen meaning plymouth or maybe unity if it's the new name and stay this
way period no matter how long i wait.

---

### Post by cariboo on 2011-02-19
Did you upgrade all the Xorg packages, and are you using the restricted ATI/AMD drivers?

---

### Post by aviramof on 2011-02-21
I didn't do partial update if that what you mean and i tried to download the driver from jockey but it didn't worked.

---

### Post by cariboo on 2011-02-21
> **aviramof said:**
> I didn't do partial update if that what you mean and i tried to download the driver from jockey but it didn't worked.

It won't work, as the restricted drives won't work with the latest Xorg. This has been covered several times in this sub-forum. Check out this [sticky]("http://ubuntuforums.org/showthread.php?t=1675614")

---

### Post by aviramof on 2011-02-21
So now what what all i got to do is to wait and keep downloading updates via the recovery mode and eventually it should work again?

---

### Post by cariboo on 2011-02-21
If you are using an ATI/AMD graphics card you'll probably have to wait until just before the RC is released to get proper closed source drivers.

---

### Post by aviramof on 2011-02-21
I don't need that good of drivers, for now what i need is for ubuntu to pass plymouth and continue to load with no problems.

---

### Post by cariboo on 2011-02-22
If you've got an /etc/X11/xorg.conf file, remove it, and you should be able to boot to a desktop.

---

### Post by Harry33 on 2011-02-22
And uninstall fglrx drivers.
See that you have this installed:
xserver-xorg-video-ati

---

### Post by cariboo on 2011-02-22
Thanks Harry33, the only system I have with ATI graphics is so old that the restricted drivers don't support it, so I have no idea what the name of the driver is.

---

### Post by DoubleClicker on 2011-02-22
> **Harry33 said:**
> And uninstall fglrx drivers.
See that you have this installed:
xserver-xorg-video-ati
xserver-xorg-video-ati apparently doesn't work "out of the box" on a 27" iMac .   
 I get  a black screen 
any suggestions?

---

### Post by Harry33 on 2011-02-22
> **DoubleClicker said:**
> xserver-xorg-video-ati apparently doesn't work "out of the box" on a 27" iMac .   
 I get  a black screen 
any suggestions?

Tell us more about your install.
Graphics card model?
Is it fully updated Natty with xserver 1.9.99.901+git20110131... ?
Any extra PPA's in use?
Did you purge fglrx_8.801-0ubuntu2 with Jockey?

---

### Post by DoubleClicker on 2011-02-23
> **Harry33 said:**
> Tell us more about your install.
Graphics card model?
Is it fully updated Natty with xserver 1.9.99.901+git20110131... ?
Any extra PPA's in use?
Did you purge fglrx_8.801-0ubuntu2 with Jockey?

TI Radeon HD 4670:
  Resolution:	2560 x 1440
  Pixel Depth:	32-Bit Color (ARGB8888)

i have whatever xserver that is installed by natty as of yesterday (i
m booted in mac os so i can't see the installed version number right now)

i'm not familiar with jockey (if it's a gui app i can't use it until after this problem is fixed). What does it do that apt doesn't?

I don't really see how any of this info is helpful though, since this not a problem with  just my machine. It's a problem everyone with a 27 inch imac has with the open source driver. The driver redirects video to the external video connector, instead of the internal display. 

Before the update that removed fglrx. there was not problem. I would like not to have to wait for the fglrx driver to be updated, before i can use ubuntu on my machine (no i'm not going to reinstall maverick).

---

### Post by aviramof on 2011-02-23
> **cariboo907 said:**
> If you've got an /etc/X11/xorg.conf file, remove it, and you should be able to boot to a desktop.

I can't find xorg.conf file is it possible that natty is using something else or a different path?

---

### Post by Harry33 on 2011-02-24
> **aviramof said:**
> I can't find xorg.conf file is it possible that natty is using something else or a different path?

A setup using open source drivers does not use "xorg.conf", so it is OK not to find it.
It is installed only into the folder /etc/X11/.
You will, however, find the file "xorg.conf.failsafe" there.
That is needed to instruct the system to use vesa driver for failsafe X environment (via recovery mode).

---

### Post by cecilpierce on 2011-02-24
Some how my main Natty got really trashed, It says vesa not installed in recovery mode, all I can get is tty1 command line. What is the correct way to install and activate vesa or nvidia from the command line ? Using GF 6200 :(

---

### Post by zika on 2011-02-24
I would try with:
sudo apt-get install xserver-xorg-video-vesa

---

### Post by cecilpierce on 2011-02-24
> **zika said:**
> I would try with:
sudo apt-get install xserver-xorg-video-vesa

Thanks, I'll give it a whirl :)

---

### Post by Harry33 on 2011-02-24
> **cecilpierce said:**
> Thanks, I'll give it a whirl :)

This command will then install the latest version of vesa.
Remember that it needs the xserver 1.10 series beta too.
And, remember, you cannot install nvidia-current into that setup no more.
It will break your system.
So, in case of nvidia, also (in addition to vesa driver) use this command to install nouveau open source driver:
```
sudo apt-get install xserver-xorg-video-nouveau
```

It is also imperative, that nvidia-current is purged from the very same setup first:
```
sudo apt-get purge nvidia-current
```

---

### Post by aviramof on 2011-02-24
> **Harry33 said:**
> A setup using open source drivers does not use "xorg.conf", so it is OK not to find it.
It is installed only into the folder /etc/X11/.
You will, however, find the file "xorg.conf.failsafe" there.
That is needed to instruct the system to use vesa driver for failsafe X environment (via recovery mode).

So what should i do now to boot to ubuntu? install xserver-xorg-video-vesa?

---

### Post by Harry33 on 2011-02-25
> **aviramof said:**
> So what should i do now to boot to ubuntu? install xserver-xorg-video-vesa?

The NVidia isssue is fixed now.
Just go to the X Updates PPA here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
Choose "Natty" and "View package details" and download these two packages according to your architecture (32-bit or 64-bit):
- nvidia-current (270.29-0ubuntu1~xup)
- nvidia-settings (270.29-0ubuntu1~xup)

There you have the nvidia proprietary drivers that do support the latest xserver 1.10.
So you can fully upgrade your Natty now.

See my other thread here for more info:
[http://ubuntuforums.org/showthread.php?t=1694894](http://ubuntuforums.org/showthread.php?t=1694894)

---

### Post by aviramof on 2011-02-25
I have ati card not nvidia.

---

### Post by Harry33 on 2011-02-25
> **aviramof said:**
> I have ati card not nvidia.

Yes OK.
Then you should first check that you do not have package fglrx installed.
If it is, uninstall it. It does not work with the latest xserver 1.10 series.

After that check that the following two packages are installed:
- xserver-xorg-video-ati
- xserver-xorg-video-vesa

---

### Post by aviramof on 2011-02-25
Everything is installed and yet ubuntu don't log on to gnome.

---

### Post by Harry33 on 2011-02-25
> **aviramof said:**
> Everything is installed and yet ubuntu don't log on to gnome.

What do you mean by everything.
I ask that because fglrx should not be installed.
Can you boot into recovery mode?
Or perhaps from the menu there:
```
Failsafe graphics mode
```

---

### Post by aviramof on 2011-02-26
There was a time that i could but now i can't do even this all i can do is to download updates 
via the dpkg option or netroot but trying to log on to gnome always ends up with just the 
background no mouse no nothing or the purple plymouth screen again no mouse no nothing,
and i have reinstalled ubuntu several times in the past few days with full format.
 
Something in the xorg drivers updates is not working so well for me i guess.

---

### Post by afoglia on 2011-02-26
You're much, much better off than I am.  I'm using an Envy 14, and I tried switching to the ATI card.  Screen went black, and all I was left with was a mouse pointer.  Restarted, and the screen just turns off.  (If I start in recovery, I see a few seconds of boot messages and then the screen goes dark.)

This despite setting the videocard to the integrated in /etc/rc.local with an "echo OFF > /sys/kernel/debugvgaswitcheroo/switch".

Guess I'm going to have the spend the weekend re-installing maverick.

---

### Post by Harry33 on 2011-02-26
> **aviramof said:**
> There was a time that i could but now i can't do even this all i can do is to download updates 
via the dpkg option or netroot but trying to log on to gnome always ends up with just the 
background no mouse no nothing or the purple plymouth screen again no mouse no nothing,
and i have reinstalled ubuntu several times in the past few days with full format.
 
Something in the xorg drivers updates is not working so well for me i guess.

Aviramof,
Please note that Natty Narwhal (11.04) is in a fast development phase right now.
I suggest you install Maverick (10.10) now and wait for Natty to develop into beta2 or actula release version in April.

---

### Post by aviramof on 2011-02-26
I tried Maverick 10.10 it's nice but not to my liking and beside i love the new ubuntu look so going 
back to the previous two panels look doesn't sound so good to me,and beside maverick felt a bit 
slow for me when i tried it then and then was no new compiz and etc so i guess i'll just keep 
downloading updates from time to time till it would sort out or a new formal version like alpah 3 be released.

---

### Post by aviramof on 2011-02-26
Well for the time being i have decided to try trisquel's till ubuntu 11.04 is officially release.

---

### Post by aviramof on 2011-02-26
And it's really is a really good distribution i would highly recommend everyone to try it out.

---

