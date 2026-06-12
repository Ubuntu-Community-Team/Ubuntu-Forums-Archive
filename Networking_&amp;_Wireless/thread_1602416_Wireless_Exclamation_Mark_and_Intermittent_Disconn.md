---
title: "Wireless Exclamation Mark and Intermittent Disconnectivity :("
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by pcsrao on 2010-10-21
I got a NetGear wireless router recently. Attached it to my Huawei (pardon the spelling) modem. I have a HP 540 laptop running Ubuntu 10.04 (love it absolutely!)

The wireless gets connected. But there's an exclamation mark almost all the time. Very frequently these days, the connection gets bogged down or websites just don't open at all. But the icon (with the exclamation mark) shows Active Connection.

I don't know where to start looking for bugs. Seems odd. Wireless is connected, I can connect to sites, but there's the exclamation.. and sooner or later, connection goes off but the icon still stays the same with "active" label.

Thanks in advance guys.

---

### Post by P4man on 2010-10-21
Hmm.. can you tell us a bit more about the laptop? The output of

```
lspci
```

and 

```
lsusb
```

would help us determine what wificard you have. The output of 

```
lshw -C network
```

Would tell us a bit more about it, including stuff like used drivers. Just copy paste those commands in a terminal (applications > accessories > terminal). To paste you can use middle mouse click (or shift+control+v). Copy paste the output back here

---

### Post by pcsrao on 2010-10-23
hi. sorry for the delay. got busy with work :(

but here are the outputs for those commands...

For "lscpi" i got this:

```

00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```


For "lsusb" :

```

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And for "lshw -C network" :

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:64:74:fe:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-2 latency=0 multicast=yes
       resources: irq:27 memory:e4600000-e461ffff memory:e4620000-e4620fff ioport:4020(size=32)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:90:d4:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.0.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:e4000000-e4003fff

```

Hope this helps. :)

Really thanks for looking into this. It really bugs me off when sometimes, I am sending a mail and suddenly the network goes AWOL!!

---

### Post by P4man on 2010-10-23
Allight, another broadcom victim :) Follow the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

---

### Post by pcsrao on 2010-10-23
> **P4man said:**
> Allight, another broadcom victim :) Follow the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)
hehe. the way you put it really made me rotfl. 

thanks for the help. i am now installing the drivers. will post as soon as i activate the fwcutter stuff. 

:)

---

### Post by pcsrao on 2010-10-23
hi.

the wireless disconnectivity problem doesn't seem to exist now although it's only been a day and a half since my last network awol.

i installed the package as mentioned on the website. but the hardware drivers list doesnt show any new stuff that can be activated :(

[IMG]http://picasaweb.google.com/lh/photo/Sr4zv7Lv4rQiAMRCqXp9pg?feat=directlink[/IMG]

That's about it. Another seeming dead-end.

And there's this exclamation mark problem still! Any ideas on why, even if the network's connected, an exclamation mark keeps appearing?

---

### Post by P4man on 2010-10-23
Im not sure I understand. The disconnections stopped, so in fact, it just works, except you have an exclamation mark?

Can you post the output again of 

```
lshw -C network
``` ?

If its still using the wl driver, try unloading it:

```
sudo modprobe -r wl ssb
```

Make sure you temporarily have a wired connection, then see if jockey proposes a new driver in "additional drivers". If it doesnt, and you have no wireless at this point, try loading the b43 driver manually:

```
sudo modprobe b43
```

---

### Post by pcsrao on 2010-10-23
oh ok.. i'll try that. :) thanks :)

---

