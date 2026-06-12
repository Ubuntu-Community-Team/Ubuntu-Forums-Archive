---
title: "Unity 2D with Natty and an old tablet"
date: 2011-01-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fonix232 on 2011-01-26
I am having problems with the new Unity 2D UI on my old Motion M1400.
I've installed Ubuntu 11.04 Alpha1, Unity 3D does not work due to no proper driver for the Intel GMA 855 built in my motherboard. So I've updated my install, grabbed all unity-2d package and tried to log into it, but it drops me back to the login screen. But the old Unity 2D was working with 10.10 (but Maverick has this problem with overheating the Intel graphics card).

What should I do? I would really need Unity for my tablet as the current GNOME UI is not good for the tablet, not so easy to use...

---

### Post by Favux on 2011-01-26
Hi fonix,

You might want to check into the xorg.conf in post #13 of this thread:  [http://ubuntuforums.org/showthread.php?t=1647181&page=2](http://ubuntuforums.org/showthread.php?t=1647181&page=2)  As always back up your current working xorg.conf and be prepared to reinstall it from the command line if your changes break X.  There's also a good link or two.

Another thread with some good links:  [http://ubuntuforums.org/showthread.php?t=1655440](http://ubuntuforums.org/showthread.php?t=1655440)

---

### Post by fonix232 on 2011-01-27
> **Favux said:**
> Hi fonix,

You might want to check into the xorg.conf in post #13 of this thread:  [http://ubuntuforums.org/showthread.php?t=1647181&page=2](http://ubuntuforums.org/showthread.php?t=1647181&page=2)  As always back up your current working xorg.conf and be prepared to reinstall it from the command line if your changes break X.  There's also a good link or two.

Another thread with some good links:  [http://ubuntuforums.org/showthread.php?t=1655440](http://ubuntuforums.org/showthread.php?t=1655440)

Thank you very much, solved it by updating the whole pack of **** :D Looks like Natty comes with the old libunity0 libraries, and that caused the problem...

However, I have another question. This Qt port of Unity 3D does not contain all features yet, does it? As on PC, I have some more stuff (apps listed, and not launched on main menu click, search bar works, etc), what don't work on 2D, and I had a feeling I ****** it up again :S

---

### Post by Favux on 2011-01-27
I'm pretty sure the Unity for Natty is pretty feature incomplete right now.  But they are working on it like mad since they want Unity to be the Natty default desktop, not Gnome 3.  Although apparently you can default to the old gnome desktop.  I have no idea about whether you can default to the KDE desktop, i.e. do a replace.  I think you can expect a whole lot of updates and upgrades to be coming through over the next few months.

---

### Post by fonix232 on 2011-01-28
> **Favux said:**
> I'm pretty sure the Unity for Natty is pretty feature incomplete right now.  But they are working on it like mad since they want Unity to be the Natty default desktop, not Gnome 3.  Although apparently you can default to the old gnome desktop.  I have no idea about whether you can default to the KDE desktop, i.e. do a replace.  I think you can expect a whole lot of updates and upgrades to be coming through over the next few months.

Just what I thought :D
I've tried out KDE's Mobile interface but it is pretty like Unity, unfinished, a lot of things won't work (Wifi display, contacts lists, etc) and buggy like hell (like, I can't launch Settings, has no interface for proper pages, like if I want to connect to a WiFi network I have to use a keyboard (no virtual one), etc). So Unity is currently the best.

By the way, Unity 3D works, but it is buggy too :O It draws window edges weird, opaque, Aero-like, and such :S

---

