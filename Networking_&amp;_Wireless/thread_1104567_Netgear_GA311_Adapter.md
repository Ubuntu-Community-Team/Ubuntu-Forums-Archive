---
title: "Netgear GA311 Adapter"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by goonman on 2009-03-23
Well a couple of geeks at work got me interested in trying Ubuntu, but after my first installation I'm about ready to switch back to Windows already.

I have been working for 2 days trying to get network connectivity.  At first I had a Linksys wireless card.  When that wasnt working I figured I'd get a more traditional hardwired ethernet card.  I installed the Netgear GA311NA gigabit card but still nothing.

From browsing the forums I think I have learned enough to know this information is important...  here is my lspci and ifconfig data:

****LSPCI****
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:06.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

****IFCONFIG****
lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:6 errors:0 dropped:0 overruns:0 frame:0
        TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0 
        RX bytes:368 (368.0 B)  TX bytes:368 (368.0 B)

So it looks like it is detected as Realtek device but if its found why isnt it working?!?!?!?!? :mad:

If its this hard to get the basic network connected I can just imagine whats going to happen when I start concentrating on my other devices.

Thanks for your help.

---

