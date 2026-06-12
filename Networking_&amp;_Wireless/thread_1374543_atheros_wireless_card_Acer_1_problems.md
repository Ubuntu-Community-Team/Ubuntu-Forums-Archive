---
title: "atheros wireless card Acer 1 problems"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by leonmac on 2010-01-06
Help! to all concerned...
Sorry to state, yet another person with problems with the Atheros chipset, and or wireless drivers.
I had thought my problem was solved,by blacklisting; but have since lost wireless capacity. Seemed O.K. after the upgrade to Koala. Later on, mid download, wireless failed. Things are back online on my XP partition. But still no success with Ubuntu.

If there are any suggestions anyone can offer, for at this point I have "fixed" myself into a corner. I have tried innumerable "solutions" from the forum threads.

Is there any help someone can offer, so that I dont have to reinstall? Since by this time, this problem has cost hours and hours of frustration.
It only takes some hours of reinstalling to set programs up as before. But after there is no guarantee that I wont encounter this same thing again...

Thanks so much. 


leon@laptop007:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:23:8b:5c:96:7b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.66 latency=0 multicast=yes
       resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:55200000-5520ffff
leon@laptop007:~$

---

### Post by zaphod777 on 2010-01-07
are you downloading with torrents?

please see this bug.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/374650](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/374650)

---

### Post by leonmac on 2010-01-07
Yes I have been, downloading torrents, but not possible now. Still, would appreciate any trouble shooting suggestions.

Thanks

---

### Post by leonmac on 2010-01-07
I looked over the link, and I dont think thats it, since I no longer get any networks. And never had problems downloading before. 
At this point I may have done more harm than good and have tied myself up in sudo command knots...

Let me know what can be done...

Thanks

---

### Post by zaphod777 on 2010-01-07
See if you can't go back to square one ans then post the results of your syslog during the event and go to the bug and mark it effects you. the more people we have the more attention we can get for a fix. 

I havn't found one so far.

---

### Post by zaphod777 on 2010-01-08
> **zaphod777 said:**
> See if you can't go back to square one ans then post the results of your syslog during the event and go to the bug and mark it effects you. the more people we have the more attention we can get for a fix. 

I havn't found one so far.

I just downloaded and installed the latest updates and it looks like many deal with wireless I am downloading a lot of torrents now and so far so good. I am hoping for the best.

---

### Post by leonmac on 2010-01-10
I have the latest updates but nothing has changed, I am awaiting help from the local freegeek windowsless Wednesdays, and Ubuntu night, surely someone will know...
I suspect its been my blacklisting efforts and following blindly the forum suggestions.
Anyone interested in helping me out of the blacklist hole I find myself in?

Thanks

---

### Post by jml on 2010-01-10
leonmac, assuming you have an Acer Aspire One netbook, have you seen this?

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

It is a rather extensive guide for getting Ubuntu to work on an AAO.  Hope it helps.

Joe

---

### Post by leonmac on 2010-01-11
That is assuming I have extensive technical prowess, which I dont.
Any step by step, hints on what to do about my lack of wireless would be helpful.

Thanks again.

---

### Post by leonmac on 2010-01-14
Still need help...

Thanks

---

### Post by bkratz on 2010-01-14
> **leonmac said:**
> Still need help...

Thanks

See post #38 of this thread.  You probably could get some help there, it is still active.

[http://ubuntuforums.org/showthread.php?t=1309072&page=4](http://ubuntuforums.org/showthread.php?t=1309072&page=4)

---

