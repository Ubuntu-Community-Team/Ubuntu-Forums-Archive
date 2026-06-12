---
title: "Kubuntu 10.10 and KDE Wireless Woes"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by SawBones on 2010-10-30
So I would love to give KDE a try and have installed it, but like most people, it doesn't work with my wireless equipment.

I have searched the forums and tried just about everything posted, including removing the kdenetwork manager and using WICD .... still nothing.  It is stuck at "getting ip address".

I'm using a desktop computer with a D-Link DWA-552 Xtreme N PCI card.  I have had absolutely no problems with Gnome; but KDE has never successfully connected to my encrypted network.

So, I'm pretty much a Linux n00b.  Anyone have any suggestions?

thanks.

---

### Post by SawBones on 2010-10-30
UPDATE: I noticed there is a similar thread posted regarding wireless problems in Mint KDE.  I even tried those solutions which were outlined at the Linux Mint Forums (Link: [http://forums.linuxmint.com/viewtopic.php?f=109&p=310366](http://forums.linuxmint.com/viewtopic.php?f=109&p=310366))  No luck.

Any other suggestions?  I've googled this multiple times already and noticed that there are hundreds of people having trouble with KDE and wireless.  Certainly with a desktop environment as big as KDE there must be a fix somewhere.

Thanks.

---

### Post by Zorael on 2010-11-02
Hmm, I've never had any problems. The Mint forum seems to be down , too.

Is there a bug report for it on [the KDE bug tracker](http://bugs.kde.org)?

Alternatively you can just use the GNOME networking tray applet **nm-applet** (from the [**network-manager-gnome**](apt://network-manager-gnome) package), though you may need to go through some scripting hoops if the KDED network management module keeps wresting control from it.

---

