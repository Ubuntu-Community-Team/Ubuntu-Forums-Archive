---
title: "Net card previously OK, now not seen by Ubuntu"
date: 2006-03-26
forum: Networking &amp; Wireless
---

### Post by cisde on 2006-03-26
Running Warty on a desktop PC with acpi=off, after a power outage everything seems fine on re-boot except onboard network card which previously worked fine.

Live CD Knoppix can correctly find and use the card. 

Some relevant output -
-------------------------------------------------------------------------------------------
admin@cartopa:~ # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:87142 (85.0 KiB)  TX bytes:87142 (85.0 KiB)

admin@cartopa:~ # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
RTL-8029(AS)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc.
VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc.
VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
**0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II]**
(rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623
[Apollo CL E266] integrated CastleRock graphics (rev 03)
admin@cartopa:~ # ifup eth0
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth0.

admin@cartopa:~ # dmesg | grep eth
admin@cartopa:~ #
---------------------------------------------------------------------------------------

Any thoughts appreciated.
David

---

### Post by dermotti on 2006-03-26
This a pci adapter or onboard?

---

### Post by cisde on 2006-03-26
Onboard. And, as I say, Knoppix can find and use it.
David

---

