---
title: "Help with Atheros AR5006EG"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by ShadowGrrl on 2009-02-25
Hi everyone. I recently installed Ubuntu 7.10 on my new laptop that came with Vista Home Premium. The wireless was working fine with Vista and when booting with Ubuntu live CD, but after fulling installing Ubuntu it's not working anymore, the wireless light on my keyboard is Amber (off state) instead of blue (on state) and pressing the button doesn't seem to turn it on. I've read alot of guides so far, but none have worked for me.

I've tried the ndiswrapper method where I was able download the correct Windows driver for my card (tried several versions so far) and use the Windows Wireless Drivers thingy to install it.

I've also followed every instruction given here: [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

I had acctually installed many different drivers before I read that guide but I've removed them all now except for the one the guide used (Version 6; net5416) (and also netw5v64, from an older guide I used is still there; the GUI Windows Wireless Drivers wont let me remove it, nothing happens when I click Remove Driver, but it's invalid anyway, so if you see it come up in the copy-paste, ignore it).

I'm completly new to Linux, but from searching this problem for a few hours, I know first thing people are going to ask me for is for the output for certain commands, so here goes...

```
natasha@natasha-laptop:~$ lspci | grep Ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev ff)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
natasha@natasha-laptop:~$ lspci | grep Ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev ff)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
natasha@natasha-laptop:~$ sudo ifconfig
[sudo] password for natasha:
eth0      Link encap:Ethernet  HWaddr 00:1F:16:44:5E:6D  
          inet6 addr: fe80::21f:16ff:fe44:5e6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967278 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:1F:16:44:5E:6D  
          inet addr:169.254.4.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

natasha@natasha-laptop:~$ getconf LONG_BIT
32
natasha@natasha-laptop:~$ ndiswrapper -l
net5416 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
netw5v64 : invalid driver!

```

I have blacklisted ath_pci on the blacklist list and made sure Atheros HAL was unticked in the GUI just like this image:
[http://quilombo.files.wordpress.com/2008/01/pantallazo-controladores-restringidos.png](http://quilombo.files.wordpress.com/2008/01/pantallazo-controladores-restringidos.png)

But as you can see I am still getting "(alternate driver: ath_pci)", is this a problem too?

Thanks in advance. :]!

---

### Post by ShadowGrrl on 2009-02-27
Bump. >.>

I see alot of people with simmilar problems getting replies, am I not giving enough information?

---

