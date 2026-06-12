---
title: "ATI Catalyst Driver won't install"
date: 2009-10-27
forum: Multimedia Software
---

### Post by rinoshea on 2009-10-27
I have a 5 year old Dell Inspiron 6000. The graphics card is an **ATI Mobility Radeon X300**. I've been having trouble with speed of flash video playback, so I decided to install the ATI **Catalyst** proprietary **driver**, to try to speed things up. 

However, when I run the ati-driver-installer-9-3-x86.x86_64.run install script, it unpacks, then throws an **error**:

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

```If anyone knows what this means, it would be very helpful!
By the way, I'm running 9.10 Karmic RC.

---

### Post by rinoshea on 2009-10-27
bump

Does anyone know what this means?

---

### Post by openxs on 2009-10-28
I have the same problem here, also using Karmic 9.10... I found this reply in the forums...

[http://ubuntuforums.org/showthread.php?t=1221221](http://ubuntuforums.org/showthread.php?t=1221221)

We are also using a Dell machine with an ati x300 card.

ATI no longer supports the ATI Radeon 9500-9800, X300-X2100, Xpress. We are now restricted to the ATI 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty (9.04) or the new Koala (9.10).

I have looked at Xorg and have found bug reports, but ultimately its a case of go backwards or wait for xorg to work with the ATI driver... it might be fixed in the next Xorg release.

This post describes how to downgrade xserver in Jaunty, but I wont bother personally:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

This is the Unoffical Linux ATI driver wiki, it may prove useful:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

== my info ==
Using Ubuntu Karmic Koala 9.10 RC

# uname -rm

2.6.31-14-generic i686

# Xorg -version

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux karl-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=695753d1-5073-496c-9cd6-911bf6022275 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.

# lspci -k

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
	Kernel modules: radeon, radeonfb

---

### Post by sammyboy405 on 2009-10-28
I Too have the Same issues.

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```

And as you said ATI No longer supports a Ton of Cards that people still use Exclusively. Which is complete crap.  

Id Love to set dual Monitors back up But even with Generic drivers I cant do it.  I want my Compiz Back too. I Should of Just stayed with 8.04

---

### Post by markbuntu on 2009-10-28
ATI has not dropped support for "a ton of cards". They have shifted their support for those cards to the open source driver efforts and have a number of their employees working on them alongside the community driver writers This has pushed progress on those drivers dramatically.

The rv300-500 series cards will no longer be supported by the ati proprietary fglrx driver, ever. The latest open source ati and radeon drivers have full 2D and 3D support for all RV300-500 cards including the x300. 

Xorg will never be "fixed" to work with the old fglrx drivers so don't hold your breath on that one.

 If you have no 3D or can't get dual monitors working using the System/Preferences/Display then something is wrong with your setup or the driver is misinstalled. Many people using Karmic report better performance with the latest open source drivers than they ever got with fglrx. You should go here for help:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by openxs on 2009-10-31
Yes, Ubuntu 8.10 is the last working fglrx/xorg combination. We had 8.10 installed on the same machine so out of curiosity I ran glxgears to get an idea of frame rates in fullscreen. Just type 'glxgears' at the command prompt without the quotes if you want to try it out.

Agreed, for compiz eyecandy, the open source driver does a fine job, however, Alien Arena is unplayable, so it depends what you're intending to do. Anyway, glxgears fullscreen on 9.10 using raedeon open source driver gave an average frame rate of 150 frames every 5 seconds while using 8.10 with fglrx proprietry drivers managed an average of 500 frames/5 sec.

Its got to be said, 2 years ago ATI was a nightmare, but larger hardware companies are taking *nix more seriously now, I can't even remember the last time I used ndiswrapper to make wireless work =o)

---

### Post by fernandoc1 on 2009-10-31
ATI is the worst choise for Linux users.
Catalyst is a really junk in Linux, compared to its performance on Windows.

If someone needs a real card, it should be NVIDIA, that plays well everywhere, at any time.

---

