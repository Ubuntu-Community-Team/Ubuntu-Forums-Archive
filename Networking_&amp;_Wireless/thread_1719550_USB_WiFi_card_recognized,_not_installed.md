---
title: "USB WiFi card recognized, not installed"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by MetalHannes on 2011-04-01
Hello,
Yesterday my sytem crashed and some files got corrupt, so I had to reinstall Ubuntu.
But now my Wireless card won't work. It used to work before (plug and play), and I have no problem with it when I boot from the CD.
I cannot use my cable connection because as soon as I plug my computer in, the network crashes, the router doesn't respond, gets hot and refuses to work until I unplug it and let it cool off for 2 minutes.
I'm using Ubuntu 10.10, Desktop PC. 
```

:~$ lsusb
Bus 001 Device 002: ID 0846:4260 Netgear, Inc. WG111v3 54 Mbps Wireless [realtek TRL818B]

```
```

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
```

:~$ lsmod
Module       Size Used by
usbhid      36882 0
hid         67742 1 usbhid
floppy      54311 0
ahci        19198 2
pata_atiixp  3288 0
libahci     21728 1 ahci
r8169       36521 0
mii          4425 1 r8169

```

```

:~$ sudo lshw -C network 
Product: RTL8111/8168B PCI Express Gigabit Ethernet Controller
logical name: eth0
```
I'm currently typing all this from my laptop so I hope you forgive me that I don't post the entire output here. It doesn't say anything about my wifi card though.

I do not have internet on my PC now, so I have to burn everything on a CD which is why I didn't try out any drivers. Besides it worked before and with the CD without drivers.

I tried plugging it in on different USB ports, and restarted the computer several times.

Thank you for reading this

Hannes

---

### Post by matt_symes on 2011-04-02
Hi 

Please post the output of

```
lsmod | grep rtl8187
```

that is RTL8187 in lower case. And also

```
modprobe -l | grep rtl8187
```

Lower case L again.

Kind regards

---

### Post by MetalHannes on 2011-04-02
The only output I didn't show completely is that of ```
sudo lshw -C network 
``` The others are complete. Sorry that I wasnt clear on that. As such ```
lsmod | grep rtl8187
``` had no result.

THe other command on the other hand was rather interesting.
```

:~$ modprobe -l | grep rtl8187
FATAL: Could not load /lib/modules/2.6.35-28-generic/modules.dep: No such file or directory

```
The only directory in /lib/modules/ was 2.6.35-22-generic.
So I booted that kernel and now it works :D .
Thank you :D

Hannes

---

