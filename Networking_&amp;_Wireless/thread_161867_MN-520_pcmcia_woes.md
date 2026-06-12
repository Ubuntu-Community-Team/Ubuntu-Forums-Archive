---
title: "MN-520 pcmcia woes"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by deathscytheh64 on 2006-04-17
Hello

From what I have read on the forums this particular card is a pain to get working. The problem is, its all I've got and hopefully with some help can get it working.

I have a sony pcg-gr300 notebook running breezy badger and two pcmica slots.
I do have ndiswrapper installed but can't find a mn-520 driver on the net that worked with it.

There are lights on the card that shows that is at least getting power and by using the steps from other forum posts know that ubuntu knows that its there, but isn't recognized in the network utilities, only having eth0 and lo listed as places.

ifconfig 
eth0      Link encap:Ethernet  HWaddr 08:00:46:61:BB:E3
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe61:bbe3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1860724 (1.7 MiB)  TX bytes:296059 (289.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:857093 (837.0 KiB)  TX bytes:857093 (837.0 KiB)
 

iwancfg
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

So all in all the lights are on but nothing is happening. The right driver isnt being loaded but when I try and bind the orinoco_cs driver, that doesn't do anything either.

modprobe orinoco_cs yields
WARNING: Error inserting hermes (/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/hermes.ko): Operation not permitted
WARNING: Error inserting orinoco (/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/orinoco.ko): Operation not permitted
FATAL: Error inserting orinoco_cs (/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/orinoco_cs.ko): Operation not permitted



Any and all help is appreciated.

---

