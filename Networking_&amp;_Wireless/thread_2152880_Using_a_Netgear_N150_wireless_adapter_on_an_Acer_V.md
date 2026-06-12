---
title: "Using a Netgear N150 wireless adapter on an Acer Veriton"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by stephengoz on 2013-06-09
I recently got a Netgear N150 wireless adapter for my Acer Veriton. The adapter worked right out of the box and the computer recognized immediately and I connected to my wifi within a minute. But the connection keeps cutting out. It shows that I am still connected to the wifi but I have to disconnect and reconnect again for it to work. This happens about once every minute. The N150 is the smallest one, should I have gotten the N300 or something bigger?

---

### Post by kurt18947 on 2013-06-09
If your Negear N150 uses RealTek's RTL-8188CUs chipset as it seems, the fix is easy thanks to Tim Phillips.  To determine the chipset the Netgear uses, plug it in to a USB port, open a terminal and type "lsusb"  You should see similar to this:
```

daily@saucy-GA-MA785GM-US2H:~$ lsusb
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]  [COLOR=#0000cd]This line should mention something about RealTek, not Atheros[/COLOR]

Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 002: ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 009 Device 003: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter

```

If your device is indeed RTL-8188CUs based,  see this post:
[http://ubuntuforums.org/showthread.php?t=2092934](http://ubuntuforums.org/showthread.php?t=2092934)
in particular posts # 9 & 10.  This fix is better than the official driver from RealTek because it includes DKMS.  The driver from RealTek requires re-running the installation script with each kernel upgrade.  This does not.  I'm using this with an Edimax 7811Un adapter and it works perfectly.

---

