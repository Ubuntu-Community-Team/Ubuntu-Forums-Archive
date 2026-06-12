---
title: "Problems with network manager connecting to wireless"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by hiro24 on 2012-04-04
Hello all, I've tried looking through some of the problems with wireless networking and I can't quite find one that resolves my issue.  Here's the deal.

The install of Ubuntu 11.10 on this laptop is about a week old, and wireless was working with the proprietary Broadcom STA wireless drivers.  I'm not sure if it was due to an update or what, but I shut my laptop down, and today I can't connect to a wireless network.

The network manager shows the wireless interface, and it shows the access point.  However, when I click on it, nothing happens.  This is my device from lspci:

```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

So far I've tried stopping and restarting network manager, rebooting, removing and reinstalling the driver from additional drivers window, and I've installed firmware-b43-lpphy-installer via the software center.  I've also removed and reinstalled bcmwl-kernel-source.  None of this seems to change anything.  Any help is greatly appreciated.  Thanks!

---

### Post by hiro24 on 2012-04-04
Ok, I got this working... sort of.  And this is how.

I ran sudo gnome-nettool.  Selected wireless device and hit "Configure".  Then went to wireless and add.  I manually entered the information for the ap I was trying to connect to (I'd never connected to it before).  Then was able to double click it o the list and it connected.

Note I had to sudo gnome-nettool, b/c just clicking the network manager icon and going to edit connections -> add left everything greyed out.

I hope this helps somebody else somewhere.  If anybody has any insight why things are suddenly like this, I'd love to hear an explanation.  Clearly something is still "wrong", but at least I have a working wireless connection now.

---

### Post by alex.nucleo on 2012-04-04
See my thoughts here: [http://ubuntuforums.org/showthread.php?t=1951032](http://ubuntuforums.org/showthread.php?t=1951032)

In short, I also could not connect to wireless with Broadcom drivers proposed in "Additional drivers". I've removed those, installed b43 from repositories directly. Package is called "firmware-b43-installer", version 1:015-9 (precise), NOT LPPHY. Now it seems to work correctly and all connections are shown in NM menu.

Blame testers of "Additional drivers" dialog and NM developers.

---

### Post by dik23 on 2012-04-25
> **alex.nucleo said:**
> Blame testers of "Additional drivers" dialog and NM developers.

:D

Thanks for this, I've been down so many dead ends in relation to this problem it's untrue ! I had come to the conclusion that Ubuntu (who allowed this into the distro?) had dropped the ball really badly - and it seems that they have.

It's really good to realise that I'm not, after all this time, incompetent !

Again, thanks for pointing this out. For anyone else out there who's having this issue - mine would work but regularly drop - you need to find and force install :

b43-fwcutter_015-9_i386.deb

and

firmware-b43-installer_015-9_all.deb

Again, thank you !  :D

---

