---
title: "rtl8185B driver fails to start successfully"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by rpgoldman on 2010-09-14
I just bought a new TrendNet TEW-423PI for my ubuntu box (10.04), and have not been able to get it to start.  This has the RealTek RTL-8185

I first tried starting up out with the stock install with the built in r8180 drivers.  No luck.  The board is seen (visible in lshw -C network), but the network device (eth1, or wlan0) never gets created.

I googled for some help, and got the suggestion that I should install the RealTek r8185 drivers.  I did that.  I still have the same problem.  Looks like something is going wrong in the drivers.  Here's what I see in lshw:
```

*-network:1 UNCLAIMED
description: Ethernet controller
product: RTL-8185 IEEE 802.11 a/b/g Wireless LAN controller
...
physical id: 9 
bus info: pci@0000:00:09.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=32 maxlatency=64 mingnt=32
resources: ioport:d000(size=256) memory: 1c020000-1c0203ff

```

and in dmesg I see
```

Linux kernel driver for RTL8180 RTL8185 based WLAN cards
Copyright (c) 2004-3005 Andrea Merello
...
rtl8185B: WW:MAC chip not recognized: version 7. Assuming RTL8180
...
rtl8185B: No channels, aborting
rtl8185B: Initialization failed

```

This is all very disappointing, and I was hoping someone might have a suggestion.

thanks!

---

### Post by maverik35 on 2010-10-19
Hi...Have you tried blacklisting the #8180 module and installing the 8185?..I can see that card has not been recognized, since not even mac address is shown...
I have myself a alfa awpci06rh with realtek 8185B, same thing happens, no interface is created...If you type in a terminal: lspci and lsmod, you will see that ubuntu loads the 8180 modules, and it sees your card, but the 8180 modules, is not compatible "at all" with 8185B..Is not the "818x" type..It is 8180 or 8185 or 8187, separetly..
So I think that you could try compiling the driver, unload 8180 module (rmmod rtl8180) and load the 8185 module (modeprobe rtl8185)..See what happens..Type lspci and lsmod and see if modules were loaded...Then type the dhclient "your interface" to assign it a valid IP (from router or where the DHCP server is)..
I still trying, I use Jaunty...

---

