---
title: "Wireless Driver issue"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Kobra7 on 2010-09-28
Hello, It's my first time trying out a Linux and everything is going great except for my networking.
I just recently purchased a wireless usb adapter 802.11n and I tried to install the driver from the cd it came with, but when I read the readme file it said it only supports up to kernel versions 2.6.18 ~ 2.6.29. Since I'm using Ubuntu 10.04 my kernel type is 2.6.32.25. Does anyone know if there are any updated versions of similar drivers online? or do I have to return this wireless adapter and get a different one?

Thanks in advance!

---

### Post by kreggz on 2010-09-29
If you try and install it might just do a recompile. Otherwise use NDISwrapper or take it back and get a supported Intel or Broadcom.

---

### Post by dineshs on 2010-09-29
If you connect your device and post the output of the following commands.I think someone can help you
```
sudo lshw -C network
```
```
iwconfig
```

---

### Post by Kobra7 on 2010-09-29
hey, thanks for the quick replies!

ummm I already tried to compile the driver but I always get an error on when I input  insmod 8712u.ko and I also did try using NDISwrapper on my autorun.inf file and I got the message "error during installation" 

here are my specs

```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5705_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:0a:0b.0
       logical name: eth0
       version: 03
       serial: 00:11:25:f6:50:be
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5705-v3.18 ip=192.168.1.101 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:d0000000-d000ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:8c:d7:2f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```

---

### Post by Kobra7 on 2010-09-29
```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Kobra7 on 2010-09-30
buump

---

### Post by dineshs on 2010-10-01
pl post the result of```
lsusb
```when device is connected

---

### Post by Kobra7 on 2010-10-01
```
:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by dineshs on 2010-10-01
> Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 

Have you tried searching [google]("http://www.google.com/search?client=ubuntu&channel=fs&q=0bda%3A8172+Realtek+Semiconductor+Corp+ubuntu&ie=utf-8&oe=utf-8")
[This]("http://ubuntuforums.org/showthread.php?t=1365082") may help

---

### Post by Kobra7 on 2010-10-03
hey, I managed to get my internet working. thx a lot!

---

