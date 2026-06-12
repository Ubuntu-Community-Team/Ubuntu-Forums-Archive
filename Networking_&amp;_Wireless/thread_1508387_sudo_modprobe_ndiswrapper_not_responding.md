---
title: "sudo modprobe ndiswrapper not responding"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by chaide on 2010-06-12
Hey everybody. I just picked up a Netgear WG311v3 Wireless PCI Card and figured I'd try and get it working on my Ubuntu 10.04 LTS machine.

I followed this guide [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) and downloaded/installed the AMD 64 drivers with ndiswrapper (I *initially* got ndiswrapper from Synaptic).

When I input
```
ndiswrapper -l
```
I'm presented with
```
wg311v3 : driver installed
	device (11AB:1FAA) present
```
So I know my driver and card are being successfully detected. However, when I attempt to type in
```
sudo modprobe ndiswrapper
```
Nothing happens. The cursor just goes down a space and keeps blinking, I'm unable to input any new commands unless I force-quit the terminal and open a new one.

I noticed someone with a similar problem in this thread [http://art.ubuntuforums.org/showthread.php?t=1446734](http://art.ubuntuforums.org/showthread.php?t=1446734) but to no avail, as I'm still having issues. I even uninstalled ndiswrapper and compiled the latest version from source, yet I still get hung up when I attempt to modprobe ndiswrapper.

I'm almost certain this is my last roadblock before I can get my wireless card running, so any help would *greatly* be appreciated.

---

