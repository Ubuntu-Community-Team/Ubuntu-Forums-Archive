---
title: "Emachines M5310 and 9.10 wireless"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by DeeLeung on 2010-04-13
This is just an FYI for any other similar users out there.  After doing much digging and going through links such as 

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://ubuntuforums.org/archive/index.php/t-823807.html](http://ubuntuforums.org/archive/index.php/t-823807.html)
[https://answers.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+question/60825](https://answers.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+question/60825)

I stumbled into a way to get my Broadcom wireless working.
I'm not sure if my interpretation is correct, but it seems that the issue was that "b43" was loading and though the wifi card was recognized, it just wasn't working.

**lshw -c network** shows that b43-pci-bridge is the running driver, but 
**lsmod** shows b43 running

The solution apparently was to:
1) **sudo gedit /etc/modprobe.d/blacklist.config**
2) change the blacklist b43xx to **blacklist b43** 
3) run synaptic package manager and install **b43-fwcutter**
4) reboot

After reboot, lsmod shows b43legacy running and everything is cool.


This is all from a clean 9.10 install, but I am updating right now, so who knows what will happen afterward.

---

