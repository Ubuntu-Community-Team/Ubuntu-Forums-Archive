---
title: "Trouble enabling wireless with atheros card"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by jimmyhilldrix on 2009-03-15
Hello

I recently installed Ubuntu 8.10 64 bit version of Linux on my laptop and I'm having some issues with enabling wireless.  Wired networking works just fine.

Originally I was using Ubuntu 8.4 32 bit and I used the ndiswrapper with the atheros windows driver to get wireless and it worked just fine.  I saw that a Linux driver for Atheros cards had recently been released so I thought I would try that instead of the wrapper.

When I first logged in, I noticed that there was no option to "enable wireless" in the network manager applet.  I also noticed that when I run ipconfig, only eth0 and lo showup, no wlan0 like on the previous install.

I looked at System -> Administration -> Hardware Drivers and it says that the driver for the Atheros card is running and active.

I can also use the network applet to edit a wireless connection, but that doesn't help because I'm still unable to actually connect to the network.

Here's some debug information that I hope will help, it seems like there is simply no configuration for the wireless card, but I'm not very knowledgeable about Linux networking so I have no idea how to set one up.

output from the lsmod

> 
lsmod | grep ath

ath_pci               109168  0 
wlan                  234784  1 ath_pci
ath_hal               225904  1 ath_pci


The hardware I'm using
> 
lspci | grep Ath

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Output of ifconfig (if it helps)
> 
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c2:50:52  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fec2:5052/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40073 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72686395 (72.6 MB)  TX bytes:5540050 (5.5 MB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:211816 (211.8 KB)  TX bytes:211816 (211.8 KB)


As I said, in 8.4 I saw a wlan0 in that listing.

Any idea how to get wireless enabled on my laptop?

Thanks.

---

