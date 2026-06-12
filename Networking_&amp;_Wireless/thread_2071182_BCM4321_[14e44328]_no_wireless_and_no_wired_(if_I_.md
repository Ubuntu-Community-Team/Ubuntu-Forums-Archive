---
title: "BCM4321 [14e4:4328] no wireless and no wired (if I don't blacklist wl)"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by alfonso78 on 2012-10-14
Hi,

wireless stopped working a while ago but now I need it again.
I just upgraded the kernel to 3.6.2 (because of other issues).
Up until a certain point I was able to connect on wired. Then I followed the patch of a page to workaround an error I got while trying to compile bcmwl-kernel-source and since then I'm in trouble.
Now not even wired work if I don't blacklist wl.

any idea?

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

```
$ uname -a
Linux NAS 3.6.2-030602-generic #201210121823 SMP Fri Oct 12 22:31:22 UTC 2012 i686 i686 i386 GNU/Linux
```

```
$ lspci -vnn |grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
```

```
$ sudo lshw -c network
[sudo] password for alfonso: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe600000-fe603fff memory:d0100000-d01fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 06
       serial: 00:01:2e:36:c1:90
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
```

```
$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2860sta
# blacklist open source Broadcom drivers to support 5 GHz
blacklist ssb
blacklist bcma
blacklist b43
blacklist wl
```

---

### Post by alfonso78 on 2012-10-14
rookie mistake…

I was following the instructions at [http://www.mindwerks.net/2012/06/wireless-bcm4312-with-the-3-4-and-3-5-kernel/](http://www.mindwerks.net/2012/06/wireless-bcm4312-with-the-3-4-and-3-5-kernel/)

```
$ sudo find / | grep wl.ko
/home/alfonso/wifi/wl/wl.ko
/home/alfonso/wifi/wl/.wl.ko.cmd
/lib/modules/3.6.2-030602-generic/updates/dkms/wl.ko
/lib/modules/3.6.2-030602-generic/kernel/drivers/net/wireless/wl.ko
```

I copied /home/alfonso/wifi/wl/wl.ko on /lib/modules/3.6.2-030602-generic/kernel/drivers/net/wireless/wl.ko instead of copying it to /lib/modules/3.6.2-030602-generic/updates/dkms/wl.ko

now it works!

---

