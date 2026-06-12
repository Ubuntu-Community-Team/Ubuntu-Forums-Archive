---
title: "Usb Wireless Modem ZtE"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by bluemountain399 on 2010-11-25
Hello i am newbie in Ubuntu i want to use a usb wireless gsm modem on ubuntu(zte ac2766). But i cann't intall it please help how can i use it on ubuntu..
Thanks.

---

### Post by Hippytaff on 2010-11-25
Hi and welcome
can you open a terminal (CTRL+ALT+T) and do the following
```

lsusb | grep -i net > wireless.txt

``````

iwconfig >> wireless.txt

``````

lshw -C network >> wireless.txt

```and post the wireless.txt document here?
:-)

Edit ->With the usb plugged in btw

---

### Post by bluemountain399 on 2010-11-27
hello this was the output..

```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:19:d1:29:55:63
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:b800(size=256) memory:feaffc00-feaffcff

```

---

### Post by Hippytaff on 2010-11-27
is it usb?

if so what does ```
lsusb
``` return (if not ```
lspci
```

Probably Ralink driver issues - depends which one though :-)

---

### Post by bluemountain399 on 2010-11-27
Yes it is a USB Wireless Modem.
lsusb:

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
Here it is detecting it.
Bus 002 Device 002: ID 19d2:fff1 ONDA Communication S.p.A.
```  

lspci:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

---

### Post by Hippytaff on 2010-11-27
try usb-modeswitch [http://manpages.ubuntu.com/manpages/karmic/en/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/usb_modeswitch.1.html)
so that the device is recognised as a wireless usb...my worst fear is that this is a bug :-s

---

### Post by bluemountain399 on 2010-11-27
which command i should use to swich modem??

---

### Post by Hippytaff on 2010-11-27
[http://www.draisberghof.de/usb_modeswitch/#usage](http://www.draisberghof.de/usb_modeswitch/#usage)

I'm not sure of the exact usage and I don't want to guess and mess you around...if you read the above link and can't get your head around it post back and hopefully someone with a bit more experience will jump in :-) I've only ever done it once so not an expert :-)

---

### Post by sikander3786 on 2010-11-27
I found a tutorial in my notes regarding your ZTE device.

[http://mobi-solutions.blogspot.com/2010/06/usb-modem-installation-in-linux-for.html](http://mobi-solutions.blogspot.com/2010/06/usb-modem-installation-in-linux-for.html)

It was intended for Jaunty but might still help.

---

### Post by widda on 2011-01-08
I've had plenty of adventures with ZTE bb modems and ubuntu, and I know that Network Connection Settings are crucial. 
So now I've just had a 3day wrestle with the settings since reinstal of 10.4, I've done a step-by-step guide
Here it is, but I wonder if there's a better place to put it.
Oh I cant do it, file too big, screenshots 'n'all.

---

### Post by widda on 2011-01-10
But until I get that together,
one crucial thing is Plan Name , if you're on one. Select "My plan is not listed"

---

