---
title: "Looking for Wifi help (Realtek, Toshiba A505D)"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by MasterColdSoul on 2010-03-27
I am having trouble getting my wifi working. I have tried the tutorials but maybe I am doing something wrong as while ndiswrapper seems to "see" my card and says the driver loader I don't get anything indicating I have available wifi connections.

Here is the info.

Laptop
Ubuntu 9.10 32 bit
Toshiba A505D, 64 bit


02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
05:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
05:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 064e:d104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 1f28:0020  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:6000(size=256) memory:e7200000-e7203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:e1010000-e1010fff(prefetchable) memory:e1000000-e100ffff(prefetchable) memory:e1020000-e103ffff(prefetchable)

lspci -nn
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
05:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
05:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
05:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netrtle : driver installed
	device (10EC:8136) present (alternate driver: r8101)

I have blacklisted r8101 in .conf I don't know why that warning pops up.

I don't know what other info I can post to help people give me some help. Thanks to anyone who read this far. 

I think I originally messed up and picked the wrong device (my LAN) instead of Wifi, now even after trying to reset it to the Wifi it's stuck on the lan possible, or maybe I am wrong. I can't really test this to much at home as I don't have wifi, but I would like to get it working as I use a USB modem, but wifi can be faster at times, and I can't always get a USB connection.

---

### Post by MasterColdSoul on 2010-03-27
Did I not provide enough information? Anyone willing to help me out?

---

### Post by MasterColdSoul on 2010-03-28
Still looking for some help... Guess it doesn't work?

---

### Post by Dude-PWB- on 2010-03-28
There is a native driver for that wireless device, but it depends whether or not you have the 8192e or the 8192se chipset.

Here is some work on the 8192e chipset:  [http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)

Here is some work on the 8192se chipset: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

lspci -vv should help you determine what chipset you have.

---

### Post by chili555 on 2010-03-28
> **Dude-PWB- said:**
> There is a native driver for that wireless device, but it depends whether or not you have the 8192e or the 8192se chipset.

Here is some work on the 8192e chipset:  [http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)

Here is some work on the 8192se chipset: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

lspci -vv should help you determine what chipset you have.```
lspci -nn
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
```I think that is an 8192E.

---

### Post by chili555 on 2010-03-28
> netrtle : driver installed
device ([COLOR="Red"]10EC:8136[/COLOR]) present (alternate driver: r8101)This is your ethernet device, not your wireless. I suggest you unload the .inf file and find and reload the .inf (and probably the .sys) for the wireless. If you need to use the ethernet, you can un-blacklist r8101.

We probably also need to clean up your .conf files a bit.

---

### Post by MasterColdSoul on 2010-03-28
Thanks to everyone who replied, due to looking more into the 8192E chipset I found the Linux Driver doesn't work for it in this kernel, but ndiswrapper worked and I downloaded the right driver this time and it loaded and WIFI is picked up by ubuntu.

> **chili555 said:**
> This is your ethernet device, not your wireless. I suggest you unload the .inf file and find and reload the .inf (and probably the .sys) for the wireless. If you need to use the ethernet, you can un-blacklist r8101.

We probably also need to clean up your .conf files a bit.

Now as you noted chili I got the wrong drivers loaded.

"WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netrtle : driver installed
	device (10EC:8136) present (alternate driver: r8101)"

How do I unload just the driver listed above if possible from ndiswrapper? If not how do I unload all ndiswrapper so I can reload the correct driver that is now working?

Thanks!

---

### Post by chili555 on 2010-03-28
Please, first, un-blacklist r8101. Then do:```
sudo ndiswrapper -e netrtle
```Then you can load your wireless .inf file. Be sure the corresponding .sys file is in the same directory when you load the .inf.

---

### Post by MasterColdSoul on 2010-03-28
All done, and it's not showing up anymore :)

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net819xp : driver installed
	device (10EC:8192) present

I removed the r8101 from the blacklist. Thanks for your help.

---

### Post by chili555 on 2010-03-28
Is the wireless working as expected?

---

### Post by MasterColdSoul on 2010-03-28
I don't have a wifi hotspot to check it where I am currently. I will try to test it today if I can, but from what I can tell it seems to be working fine.

The network connection manager shows it and allows me to connect to "hidden wifi" so I imagine if there was a open wifi connection  I could connect to it. 

iwconfig shows

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


Thanks for your help again.

---

