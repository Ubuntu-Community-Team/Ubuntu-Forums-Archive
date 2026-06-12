---
title: "Network not working after motherboard upgrade"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by igreen on 2012-04-03
Hi

I had to replace the motherboard and drive so I copied the partitions across to the new drive. Everything worked except the networking (wired). The strange thing is if I boot the system from sysrescuecd the network goes. Also if I boot from a live cd the network goes. There must be a lingering setting in the settings from the old nic that have come across when I cloned the drive. I haven't been able to work out where the might be or how to get rid of them so the new nic works. Any ideas would be appreciated. Ifconfig only brings up lo. There is no eth showing. lshw -class network shows as unclaimed.

---

### Post by alex.nucleo on 2012-04-04
Have you tried

sudo rm /etc/network/interfaces

?

If this file has old information, then NM doesn't start or starts and doesn't connect.
After you remove the file and reboot, NM recreates the file and puts there something like

auto lo
iface lo inet loopback

---

