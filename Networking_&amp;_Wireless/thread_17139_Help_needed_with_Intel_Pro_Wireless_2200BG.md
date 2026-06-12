---
title: "Help needed with Intel Pro Wireless 2200BG"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by Swift on 2005-02-26
I'm using this card, because it's in the Toshiba Tecra M2 laptop I use. It gets detected OK, but trying to connect with several access points won't happen. Can it be that the length op the WEP-key is a problem (hex 26 characters, 128 bit)?

---

### Post by alastair on 2005-02-26
Who knows. You do not give any real useful information to help diagnose...

Detected? Show the relevant log file messages when the card is loaded and found - in :

/var/log/syslog

After boot, what about network config - in a terminal :

ifconfig -a

iwconfig

The relevant network config file would be :

/etc/network/interfaces

I have a 2100 and it works.

---

### Post by Swift on 2005-02-27
Yes, you're right off course. Sorry about the lack of information in my first post. Here's some information you asked about.

After starting up the section in the logfile (/var/log/syslog) about networking shows:

```
Feb 27 12:35:39 localhost kernel: ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.11
Feb 27 12:35:39 localhost kernel: ipw2200: Copyright(c) 2003-2004 Intel Corporation
Feb 27 12:35:39 localhost kernel: ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 11 (level, low) -> IRQ 11
Feb 27 12:35:39 localhost kernel: ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Feb 27 12:35:39 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
Feb 27 12:35:39 localhost kernel: ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 11 (level, low) -> IRQ 11
Feb 27 12:35:39 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcefe800-fcefefff]  Max Packet=[2048]
Feb 27 12:35:39 localhost kernel: e1000: Ignoring new-style parameters in presence of obsolete ones
Feb 27 12:35:39 localhost kernel: Intel(R) PRO/1000 Network Driver - version 5.2.52-k4
Feb 27 12:35:39 localhost kernel: Copyright (c) 1999-2004 Intel Corporation.
Feb 27 12:35:39 localhost kernel: ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 11 (level, low) -> IRQ 11
Feb 27 12:35:39 localhost kernel: e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
```

As you can see the both the wireless and wired NIC's are identified.

With ifconfig -a I get the following output:

```
eth0      Link encap:Ethernet  HWaddr 00:0E:35:26:24:CC
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x3000 Memory:fceff000-fcefffff

eth1      Link encap:Ethernet  HWaddr 00:0E:7B:E6:98:12
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xcf40 Memory:fcec0000-fcee0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:803777 (784.9 KiB)  TX bytes:803777 (784.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Since I can't post it all in one reply (errormsg about to many tags used) see the next reply for more info.

---

### Post by Swift on 2005-02-27
I'm trying to send all the logs and messages, but I keep getting errormsg, so I'll try to upload them in a textfile. Hope this works.

---

### Post by alastair on 2005-02-27
Wireless is a bit of a pain sometimes - but your card is recognised and a supported one, so you should be better off than most. I have similar problems sometimes - and generally do some command line work to get things going. I see "eth0" is your wireless - because it loads before your wired e1000 "eth1" - so :

Do you know your AP MAC address? Try :

iwconfig eth0 ap <MAC of AP>
iwconfig eth0 essid thuis
iwconfig eth0 key restricted <KEY>

You might need to bring the wired down as well to get routes right i.e. only ONE default route :

check :

route -n

Bring down eth1 (wired) :

ifdown eth1

---

### Post by Swift on 2005-02-27
[QUOTE=alastair]Wireless is a bit of a pain sometimes - but your card is recognised and a supported one, so you should be better off than most. I have similar problems sometimes - and generally do some command line work to get things going. I see "eth0" is your wireless - because it loads before your wired e1000 "eth1" - so :

Do you know your AP MAC address? Try :

iwconfig eth0 ap <MAC of AP>
iwconfig eth0 essid thuis
iwconfig eth0 key restricted <KEY>

You might need to bring the wired down as well to get routes right i.e. only ONE default route :

check :

route -n

Bring down eth1 (wired) :

ifdown eth1[/QUOTE]
 OK, thanks. I'm gonna try this in the next couple of days (I'm a few days offline, because of a business trip) and get back to you with the results.

---

### Post by Swift on 2005-03-04
alastair,

Thanks for the input. I just upgraded to Ubuntu 5.04 and all troubles are vanished. Everything works smoothly after installation and setup. Thanks again.

---

### Post by amerigo5 on 2005-03-24
I used to have a problem with wireless connection on Warty and Hoary. I tried every possible solution I could find but I was unable to fix my wireless connection problem. Then I installed WAPROAMD and GUESSNET (using apt-get) and everything worked. This might not be a solution but it worked for me. Thanks.

---

