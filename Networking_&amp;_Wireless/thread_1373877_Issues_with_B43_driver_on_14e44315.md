---
title: "Issues with B43 driver on 14e4:4315"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by hypergeek14 on 2010-01-06
Hello.  

I've got _Xubuntu 9.10_ on my _Lenovo S10e_.  It uses a _Broadcom BCM4312_ with _14e4:4315_.  I have been having many a problem with trying to get my wireless to work with the B43 driver.  

I followed the directions on this famous thread: [http://ubuntuforums.org/showthread.php?t=1266620]("http://ubuntuforums.org/showthread.php?t=1266620"), but when I restart after the first script, *uname -a* tells me that I am still using the kernel version of 2.6.31.  Giving up on that, I went to System>Hardware Drivers and saw, in addition to the Broadcom STA driver which I used to use, the Broadcom B43 driver.  So I activated it and it says "Activated and currently in use", but I still am not picking up any networks with wicd.  

Do I need to update my kernel?  And if so, how?

---

### Post by hypergeek14 on 2010-01-25
Also, iwconfig is showing that I have no wireless extensions associated with eth0.  But Hardware Drivers still says B43 is activated and currently in use.  

Do I need to update my kernel?

---

### Post by bkratz on 2010-01-25
chenxiaolong apparently just updated his directions in the thread about a week ago, you might want to look at it again if it was longer ago that you looked.  EthO is not the wireless controller so I don't quite understand the second post.

Could you copy/paste the outputs of:
 uname -a
iwconfig
sudo lshw -C network

back here?

Also, see this

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)  under section 1.3

---

### Post by hypergeek14 on 2010-01-27
> **bkratz said:**
> chenxiaolong apparently just updated his directions in the thread about a week ago, you might want to look at it again if it was longer ago that you looked.  

Yes, but that is all about getting it to work in the fancy new kernel.  

> **bkratz said:**
> EthO is not the wireless controller so I don't quite understand the second post.

That's eth0 (eth-zero).  It's what I had in wicd as the wireless controller, with eth1 as the wired.  At least that worked with Broadcom STA driver.  

> **bkratz said:**
> Could you copy/paste the outputs of:
 uname -a
```
keith@keith-netbook:~$ uname -a
Linux keith-netbook 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
```
> **bkratz said:**
> iwconfig
```
keith@keith-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated 
[INDENT]Tx-Power=20 dBm   
Retry  long limit:7   RTS thr:off   Fragment thr:off
Power Management:off[/INDENT]
```
> **bkratz said:**
> sudo lshw -C network
```
keith@keith-netbook:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:83:39:da
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:f0200000-f020ffff

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0400000-f0403fff

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:00:cd:b8:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```


> **bkratz said:**
> Also, see this

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)  under section 1.3

I couldn't find anything about kernel updates in there, just packages.  

All this talk about eth0 made me curious, so I switched wicd's wireless controller to wlan0.  It worked for a few seconds (detected nearby nectorks), but disconnected before I could connect to a network.  Several retries later, it worked again, but disconnected again before I could connect to anything.  I've fiddled with trying other controllers, but haven't been able to get on at all yet.  

Do you think that I need to update my kernel?

---

### Post by bkratz on 2010-01-27
Boy, he updated it again and made it more confusing to follow! But yes it looks like the only way to get reliable service is to follow his directions and update to the newer kernel. I did a preliminary download of the unreleased 10.04 and wireless did work quite well, I did go back to 9.04 were it worked well too.  If you can wait until the development is completed 0n 10.04 that would be ideal, but if you need it now it looks like you have to follow his description.

---

### Post by hypergeek14 on 2010-01-27
OK, thanks man, I'll try it again.

---

