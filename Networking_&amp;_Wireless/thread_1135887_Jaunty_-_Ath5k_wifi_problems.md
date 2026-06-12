---
title: "Jaunty - Ath5k wifi problems"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-04-24
I have a Macbook Pro (1,1) with an Atheros AR242x.  It worked fine in 8.10, but with the 9.04 Kubuntu live CD it can't connect to any networks.

Strangely enough, with the 9.04 UBUNTU live CD it works fine!  What gives?

---

### Post by jbrid on 2009-04-24
I have the same problem, and I would imagine that others do to. There was a bug reported on this but apparently it wasn't fixed:

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339313](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339313)

If, in fact, KDE's network manager in 9.04 cannot connect to any wifi needing a password, that seems like a serious bug.

I hope it is fixed soon.

---

### Post by skullmunky on 2009-04-27
Jeez, that IS a serious bug.  

Hm, can't find an emoticon to describe pulling out hair with frustration from another otherwise terrific release of my favorite distro completely falling on its face because of a fundamental showstopping bug in wifi management.  ggaaahhhh ....

---

### Post by neymac on 2009-04-27
Try install wicd

In a terminal type:
sudo aptitude install wicd

It will ask you if you agree remove network-manager and plasma-network-manager-applet
Say yes to both questions.
Then wicd will be installed.
At the menu "internet" start wicd and choose your wireless preferences.
The next version of KDE4 will have wicd in it.

---

### Post by skullmunky on 2009-04-29
Thanks Neymac, that did the trick!

It'd be nice if wicd would dock in the taskbar automatically, but at least you can drag it in there and that'll work.

I like how much control wicd gives you, that's terrific.  Too bad about the knetwork-manager plasmoid, it looked really slick....

---

### Post by Paul Mitchell on 2009-04-29
Works for me too on the AA1. Phew :-)

---

### Post by Wi7ahc4l on 2009-05-06
> **skullmunky said:**
> Thanks Neymac, that did the trick!

It'd be nice if wicd would dock in the taskbar automatically, but at least you can drag it in there and that'll work.

I like how much control wicd gives you, that's terrific.  Too bad about the knetwork-manager plasmoid, it looked really slick....

When you start wicd from the main menu the launchers command is 
wicd-client --no-tray remove "--no-tray" and it'll be in taskbar when you run it. Although if it's configured to run at startup it should start in taskbar anyways.

---

### Post by Anubis on 2010-01-20
[http://wicd.net/punbb/viewtopic.php?id=742](http://wicd.net/punbb/viewtopic.php?id=742)

Clearly WICD only brings other problems with ATH5k, such as not being able to connect after a resumed state. One has to unload the ath5k module then reload it to reconnect to the network.

---

