---
title: "WEP Wireless Authentication Rejected (Though Key is Correct)"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by benali72 on 2011-02-18
I have 2 laptops running Ubuntu 10.04.  One connects to my Linksys wireless modem fine while the other does not.

The one that does not connect, will connect fine within the instances of Windows XP SP3 and Puppy Linux 5.1 that run on the same laptop. Ubuntu wireless worked fine with version 8.04 on this laptop before upgrading to 10.04.

When trying to connect within 10.04, Ubuntu pops up the dialog box to enter the authentication key. It rejects the correct key, and after a moment, pops up the same dialog box asking for the key again. I'm using WEP 40/128-bit encryption and the key I enter in the dialog box is the correct 26-character key.

The laptop is a Toshiba Satellite Pro 6000 (1g ram/40g disk).  Here are some vital outputs --

root@user-laptop:/home/bsmis# iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.
irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"kr_wireless"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:3
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

=====================================================================

root@user-laptop:/home/bsmis# lshw -c network

  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:c7:f0:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:f7efe000-f7efefff ioport:eec0(size=64) memory:f7ec0000-f7edffff

  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0
       resources: irq:11

  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:35:2a:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

===========================================================

root@user-laptop:/home/bsmis# lspci -v |less

...
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f7efe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at eec0 [size=64]
        Memory at f7ec0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: e100
        Kernel modules: e100
...
=====================================================================

If I turn off or disable WEP security on the modem, when I try to connect via Wireless, after a moment or two Ubuntu 10.04 gives me the message that it failed to connect.

Thank you for any help you can give me.

---

### Post by benali72 on 2011-02-19
I was hoping someone else might have run into this issue, but I guess not.

Since wireless does work under Windows XP on the affected laptop, I think I'll back up the instance I've got, then go ahead and see if I can get NDISWRAPPER working with it to use that working XP driver.

Thank you.

---

### Post by fluffkitten on 2011-02-21
I've seen a few people having problems with the combination of Orinoco driver, Lucent/Agere firmware, network manager and wpa_supplicant (had it with my laptop and 10.10 before I broke the thing.). It appears to be what's happening with your connection. 

There are a few threads about it though I'm not sure if there is a known solution. Sorry I can't be of any real help. A search on orinoco or lucent/agere should bring up a lot of it.

---

### Post by benali72 on 2011-02-24
Thanks for your reply. Yes, I looked through lots of complicated threads and found other people with the same problem symptom as mine, but no one has solved it using my specific hardware.

I have another solution though. I'm just buying another insertable laptop wireless card.  I've decided to buy the [D-Link WNA-2330 RangeBooster G Notebook Adapter]("http://www.amazon.com/D-Link-WNA-2330-RangeBooster-Notebook-Adapter/dp/B000P5KW7G/ref=cm_cr_pr_product_top"), since two posters on Amazon said it worked fine with Ubuntu 10.04 and both WEP and WPA wireless security. Also it's very cheap at under $15 US.

I'll post back with results after I receive and test the card, in about a week. Thanks everyone.

---

### Post by ZudoHackz on 2013-02-17
I am having the same problem, but with 11.10 and WPA-Personal. I am rather new to linux and would like help as I dont know what to do to send you information.

---

