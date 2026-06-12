---
title: "Marvell 88w8335 [Libertas] Wireless (Advent 7105)"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by Jintawk on 2012-02-15
Hello,

I'm running Lubuntu 11.10 on my Advent 7105 laptop and I'm having a lot of trouble getting a wireless network connection.

I've followed a lot of installation guides for installing drivers using ndiswrapper, including this one: 
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

And this one:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

I've tried every step mentioned a few times with no results.

I'm assuming my issue with the wireless is that the network is reported as UNCLAIMED when I run *lshw -C Network*.
However I don't know how to resolve this.

_This is the output from *lspci -nn:*_
[I]...
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 43):[/I] 

_This is the output from *lshw -C Network*:_
[I]root@jim-Lubuntu:~# lshw -C Network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febffc00-febffcff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 43
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:febe0000-febeffff memory:febd0000-febdffff[/I]

[U]This is the output from *ndiswrapper -l*
[/U][I]root@jim-Lubuntu:~# ndiswrapper -l
mrv8335 : driver installed
	device (11AB:1FAA) present[/I]


Even though ndiswrapper module is configured to be loaded at boot, running *lsmod | grep ndis* returns nothing. 

Running *sudo modprobe ndiswrapper* results in any interaction with any network related function to be completely broken. For example now running *lshw -C Network* will cause terminal to halt indefinitely, as will running such commands as *iwlist*. This can only be solved by a reboot.


There is a physical wireless toggle button on the laptop which does nothing when pressed, there is no visible wireless LED.


Any suggestions on this would be much appreciated.

Thanks.

---

### Post by praseodym on 2012-02-15
Hi,

check this thread, post 1113

[http://ubuntuforums.org/showthread.php?t=885847&page=112](http://ubuntuforums.org/showthread.php?t=885847&page=112)

---

### Post by Jintawk on 2012-02-15
Thanks for replying,

I tried the instructions from post #1113 twice.. one on my current installation of lubuntu and once on a new fresh installation.

Unfortunately the results are the same.

I followed the steps in post #1113, installed the relevant mrv8335 drivers into ndiswrapper and rebooted. The network is still listed as UNCLAIMED.

---

