---
title: "WirelessTroubleshoot--Senao2511"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by katamari on 2006-01-27
Hi Ubuntu peoples! This is my first post on here, and before everything else, I must stress that I really enjoy how accessible this distribution is and how supportive the community is on the forum.  I've been working on this problem since the beginning of the week but since I haven't figured it out I thought I would learn from the gurus and hopefully this thread will help someone else that bought the same card (the ebay seller seems to sell a lot of them).  I bought this card because AFAIK prism2.5 supports sniffing, so if someone has info to the contrary, please let me know. 

My situation is as follows:  I'm using what I believe to be a rebadged Senao 2511.  It's supposed to have the Prism 2.5 chipset. I got it working in Windows with the senao driver install utility (I guess the files are bound up in the executable, which is annoying cause there's no INF to use with ndiswrapper, all i can find is a .sys)  so I know that that card works and the pcmcia slot works.

The first time I ever plugged it in I only got "eth1" but  since I installed hostap-utils  I get "wifi0" and "wlan0" at the same time the Network Settings GUI.  
Here is the output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Warning: Driver for device wifi0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wifi0     IEEE 802.11b  ESSID:"test"
          Mode:Master  Access Point: 00:00:00:00:00:00   Bit Rate:11 Mb/s
          Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"test"
          Mode:Master  Access Point: 00:00:00:00:00:00   Bit Rate:11 Mb/s
          Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

here is the relevant output of lshw:
  *-network
       description: HFA384x/IEEE
       product: Version 01.02
       vendor: INTERSIL
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:02:6f:00:00:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.1 - 2005-05-22 firmware=1.0.3 multicast=yes wireless=IEEE 802.11b

here is some stuff from dmesg:
: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode  WDS
[4294723.516000] wifi0: registered netdevice wlan0
[4294723.974000] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0x a00fffff
[4294916.013000] NET: Registered protocol family 10
[4294916.013000] Disabled Privacy Extensions on device c02eb280(lo)
[4294916.014000] IPv6 over IPv4 tunneling driver
[4294926.049000] eth0: no IPv6 routers present
[4295501.569000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4295501.569000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295503.123000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295503.123000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295504.132000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4295504.132000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295504.290000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295504.290000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296800.656000] Scan result translation succeeded (length=0)
[4296818.037000] Scan result translation succeeded (length=0)
[4296827.936000] wlan0: no IPv6 routers present
[4296843.816000] wlan0: Host AP mode does not support 'Any' essid
[4296854.063000] wlan0: no IPv6 routers present
[4302859.190000] hostap_cs: CS_EVENT_CARD_REMOVAL
[4302859.190000] wifi0: card already removed or not configured during shutdown
[4302859.190000] wifi0: Interrupt, but dev not OK
[4302859.200000] wifi0: card already removed or not configured during shutdown
[4302859.446000] hostap_cs: Driver unloaded
[4302859.454000] hostap_crypt: unregistered algorithm 'NULL' (deinit)
[4338733.399000] hostap_crypt: registered algorithm 'NULL'
[4338733.439000] hostap_cs: 0.4.1 - 2005-05-22 (Jouni Malinen <jkmaline@cc.hut.f i>)
[4338733.447000] hostap_cs: setting Vcc=33 (constant)
[4338733.447000] hostap_cs: CS_EVENT_CARD_INSERTION
[4338733.447000] hostap_cs: setting Vcc=33 (from config)
[4338733.447000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[4338733.447000] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[4338733.447000] io->flags = 0x0046, io.base=0x0000, len=64
[4338733.451000] hostap_cs: Registered netdevice wifi0
[4338733.491000] hostap_cs: index 0x01: Vcc 3.3, irq 3, io 0x0100-0x013f
[4338733.687000] prism2_hw_init: initialized in 196 ms
[4338733.689000] wifi0: NIC: id=0x800c v1.0.0
[4338733.689000] wifi0: PRI: id=0x15 v1.0.4
[4338733.689000] wifi0: STA: id=0x1f v1.0.3
[4338733.690000] wifi0: defaulting to host-based encryption as a workaround for firmware bug in Host AP mode WEP
[4338733.690000] wifi0: defaulting to bogus WDS frame as a workaround for firmwa re bug in Host AP mode WDS
[4338733.695000] wifi0: registered netdevice wlan0
[4339131.434000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
Then it repeats that last bit about a million times:)

here's my /etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

So thanks in advance for taking the time to read this, and please let me know what other information is relevant.  Like I mentioned before, I'm into this card because I believe it has features that I can use with kismet, ethereal, nmap, and those other fun toys, so ideally I want to use a driver that will allow it to sniff in promiscuous mode.  This is only my second week in Linux so this is very much a learning experience.   Thanks for your suggestions!

---

