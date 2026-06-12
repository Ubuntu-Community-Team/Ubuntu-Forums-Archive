---
title: "wireless stopped working after system update"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by carolinealicia on 2009-04-11
I've searched through threads, and googled, and I've tried everything. I've put up my best effort to help myself, I give up at this point. So here is my info (laptop Acer TravelMate C300 Tablet):

ubuntu version/kernel:
> Ubuntu 8.10 2.6.27-11-generic i686


lspci:
> Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



sudo lshw -C network (using Ethernet cable connected to router right now)
> 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 03
       serial: 00:0a:e4:0b:69:a0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.07 ip=192.168.1.101 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:e0:11:2d:fd:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Before when I used the modprobe ipw2200 command I got a lot of errors:
> [ 2438.516821] ipw2200: Unknown symbol ieee80211_is_valid_channel
[ 2438.517265] ipw2200: disagrees about version of symbol alloc_ieee80211
[ 2438.517267] ipw2200: Unknown symbol alloc_ieee80211 

now I am getting:
> FATAL: Module ipw2200 not found.


nothing pertaining to wireless (ieee20811) shows up when I use lsmod command.

Now it may have been a bad choice on my part, but I *think* i uninstalled all the ieee80211 & ipw2200 files. I was hoping to just reinstall them. I have all the ndiwrapper files and the like. 

I've tried installing ipw2200-1.2.0, ieee80211-1.2.18, using ndsiwrapper to install windowXP driver of intel2100b.zip (all of this was done before i uninstalled everything.) So I uninstalled and cleaned everything. When I search, there are no longer any ieee80211 files. Despite this i still only get ERROR messages when i try to install the ieee80211 & ipw2200 files. 

Thanks for any advice/help that can be given. I guess if I can't get this fixed the next step is to delete the ubuntu partition and figure out how to use that space for my XP partition [-(.

---

### Post by superprash2003 on 2009-04-11
when you boot, grub shows you the list of kernels which you can choose to boot.. try choosing an older kernel and see if it works..

---

### Post by carolinealicia on 2009-04-11
thank you for the advice ;), but I've tried doing that as well. no go :mad:

---

### Post by MaskedMarauder on 2009-04-20
I have exactly the same problem and can't find any way to make it work in 8.10.  It did work in 8.04.

I'm trying to use an IBM Thinkpad T42.  Is it unique to this machine, or its family?  I can't believe a totally broken driver like this would escape Ubunutu Central.

I've tried rebuilding the ieee80211 and ipw2200 modules from source and trying newer (up to 3.1) firmware, all with no joy.

If ANYONE has a working ipw2200 card on a 32 bit intel platform, please send me your info, preferably a tar of the working ipw220/ieee80211 kernel modules.

---

### Post by carolinealicia on 2009-04-25
upgraded to 9.04 (beta or not, nothing else to lose i figured) and my wireless is working agian. Thank God no more 100ft ethernet cord to trip over in the morning...

---

### Post by MaskedMarauder on 2009-04-26
Glad to hear it works.  I'll give upgrading a shot.  It can't be worse than 8.10.

---

