---
title: "Flaky wifi in Breezy"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by abaddon80 on 2006-02-26
Hi guys,

I have an Xterasys XG600 mini-PCI wifi card (Intersil ISL3890) using the prism54 driver.  It's been working great up until these last couple days.  I've been noticing that my internet was really slow, some pages wouldn't load, I'd get connection timeouts occasionally, etc.  For example, I could get to ebay.com, and browse for a bit, but eventually, one page or another would stall and get a connection timeout.  If I came back later (either after I restarted networking,  rebooted router, rebooted machine, or even just did nothing and waited), the page would eventually load.  So it's not like specific pages won't load.

At first, I thought it was my ISP (Comcast), so I tried on my wired Windows desktop; everything was working normally.  Then I suspected the wireless connection, so I turned on a couple other laptops (Powerbook and a Sony VAIO running Windows), and those worked fine as well.

So then I suspected *my* wireless card, so I booted up Windows on my laptop (I have a dual-boot setup), and internet worked fine there as well.  All pages loaded within a reasonable amount of time, and no connection timeouts.  Finally, I booted back into Linux, I turned off my wifi card, and plugged in to my router with a Cat5.  No connectivity problems whatsoever.

While on the wireless connection, I continued to browse what I could on the web, and then I looked at the output of ifconfig.  I didn't see any TX or RX errors.

At this point, I'd like to be able to watch outgoing packet traffic on eth1.  I installed ethereal, but I really don't know how to use it that well, so I'm not sure what I'm looking for.

Does anyone have advice on anything else I can try to debug the problem?  It doesn't make much sense as things were working just fine a week ago.  I also made sure I dist-upgraded and have the latest packages.

Thanks in advance.

---

### Post by Alphableeder on 2006-03-11
Same problem here. I get 2-10mins of a solid connection sometimes but then it starts to cut in-and-out with timeouts. I know the signal is fine so it must be software related. I havent changed a thing since install.

---

### Post by russbuss on 2006-03-13
I have been having very similar problems, although I DO see errors and dropped TX packets in my ifconfig:

russbuss@moonblobs:~$ ifconfig

ra0       Link encap:Ethernet  HWaddr 00:0F:66:70:97:44
          inet addr:192.168.1.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe70:9744/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:406515 errors:0 dropped:0 overruns:0 frame:0
          **TX packets:724511 errors:4807 dropped:4807 overruns:0 carrier:0**
          collisions:43604 txqueuelen:1000
          RX bytes:474389741 (452.4 MiB)  TX bytes:50015625 (47.6 MiB)
          Interrupt:17 Base address:0x8000

Has anybody determined what might be the cause of this?  Also, I don't know that much about what TX errors or dropped packets might be symptomatic of, but I could stand some enlightenment if anybody would care to offer their wisdom.



-B.

---

### Post by sveinn on 2006-05-11
Hi, 

Just noticed this thread.

I have the same problem, please see

[http://www.ubuntuforums.org/showthread.php?t=170448](http://www.ubuntuforums.org/showthread.php?t=170448)

Currently, I am at a different location, and am not experiencing any problems. 

I am running the same Netgear wireless DSL-modem/router/firewall in both places. 

The main differnence is that in the second location, where the wireless is stable, there are is only one other nearby WiFi access point with a weak signal. 

In the first location, where the connection is flaky, there are at least five other access points with stray signals.

Reg, 

Sveinn

---

