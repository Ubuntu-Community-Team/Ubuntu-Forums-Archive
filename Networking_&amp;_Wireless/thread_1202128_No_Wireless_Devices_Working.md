---
title: "No Wireless Devices Working"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by Sankou on 2009-07-01
I'm having and insanely hard time getting internet to work with my ubuntu installation. Right now i'm dual booting with xp because no other installation method would work except for installing though windows :( and I've tried 3 different wireless devices (all tested in windows and working) and none of them work in ubuntu. I've been working on this for nearly 7 hours and i'm getting nowhere. 

Results:

First one i tired is an encore usb wireless model enuwi-g2
It connects to my router and works but i never get speeds faster than a few bytes a second. It also drops the connection after 2 seconds and takes nearly 5 min to reconnect.

Second one is a netgear wg311 v3 pci wireless adapter. it doesn't even show up. I tried to install the windows drivers with ndiswrapper but it still doesn't show up.

Third one is a Buffalo WLI2-PCI-G54S Wireless PCI Adapter. I tried to install the windows drivers with ndiswrapper and this was the result-

___________________________________________________

admin@ubuntu:~$ ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netg54s : driver installed    
device (14E4:4318) present (alternate driver: ssb)
____________________________________________________

I don't know what the warning is about, but that seemed to be a good result. It still didn't show up or work though. The card shows up in network devices but wont work at all. It wont even find my router.

Maybe there's an error with ndiswrapper working on startup.... this is the file.

_________________________________________________
admin@ubuntu:~$ gksu gedit /etc/modules

/etc/modules: kernel modules to load at boot time.#

# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

ndiswrapper

______________________________________________________

I really have no idea what I'm doing wrong or why none of these divices work, but it's really annoying. I'm begining to think almost no wireless devices work with ubuntu.

I'm trying to avoid climbing into my attic to run an ethernet cable across my house from my router....

Any help would be great.

---

### Post by MaindotC on 2009-07-01
Try the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and visit the ndiswrapper section.

---

