---
title: "Wireless Unclaimed in Ubuntu 11.10"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by Jackson Tan on 2012-05-06
Hi all!

I am having a problem with my RT2800 wireless on my PC in Ubuntu 11.10. Basically, there is no wireless ('sudo lshw -C network' gives '*-network UNCLAIMED'). This occurred after I've upgraded to 12.04 through Update Manager and then downgraded back to 11.10 using the Live CD (but keeping the files under /home).

The wireless card is definitely working. Previously, it worked out of the box in 11.10, and it also works in Windows 7 and the Live CD (which I'm using right now). It's only not working in my Ubuntu installation.

(On this issue of the Live CD detecting the wireless, it also correctly identified the screen resolution (1920x1080), where my Ubuntu installation shows only 1024x864. Does anyone know a fix for this?)

Is there anything I need to install? ndiswrapper doesn't seem to be installed. My issue is further compounded by the fact that the wireless is my only connection. Will a complete reinstall (including wiping out /home) solve the problem?

Jackson

---

### Post by praseodym on 2012-05-06
Hi,

what card is that? Please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
For the VGA card:

```
lspci -nnk | grep VGA
cat /etc/X11/xorg.conf
```
Wiping /home should never be necessary.

---

### Post by Jackson Tan on 2012-05-06
Hi praseodym,

Thanks for your reply.

lspci -nnk | grep -iA2 net:
```

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
        Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
        Subsystem: Ralink corp. Device [1814:2860]
06:00.0 USB Controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)

```lsmod:
```

Module             Size   Used by
hid_logitech       26520  0
ff_memless         13097  1 hid_logitech
i915              468561  1
usbhid             47199  1 hid_logitech
drm_kms_helper     46978  1 i195
r8169              62099  0
hid                99559  2 hid_logitech,usbhid
drm               242038  2 i915,drm_kms_helper
i2c_algo_bit       13423  1 i915
video              19596  1 i915

```iwconfig:
```

lo       no wireless extensions.

etho0    no wireless extensions.

```rfkill list returns nothing.

lspci -nnk | grep VGA:
```

01:00.0 VGA compatible controller [0300]: nVidia Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)

```cat /etc/X11/xorg.conf:
```
cat: /etc/X11/xorg.conf: No such file or directory
```I should mention that my hard drive (ext3) does not mount automatically when I plugged it in (so I had to manually type the output). It does appear that this downgrade has scrambled certain  functions that is typically considered basic.

---

### Post by praseodym on 2012-05-06
For wireless:

load the driver by hand:

```
sudo modprobe rt2800pci
```

For Graphics: Install the NVIDIA driver via "additional drivers". If installed, change via CTRL+ALT+F1 to the 1st terminal and set up a xorg.conf:

```
sudo service gdm stop
sudo nvidia-xconfig --composite
sudo service gdm start
```
Change gdm to the window manager in use (e.g. lightdm, kdm, etc).

---

### Post by Jackson Tan on 2012-05-07
'sudo modprobe rt2800pci' gives
```

FATAL: Could not load /lib/modules/3.2.0-24-generic/modules.dep: No such file or directory

```

Under the /lib/modules/ directory, I found only one directory: 3.0.0.12-generic. When I booted that kernel, everything returned back to normal (screen resolution, wireless). So it appears that some upgrade must have broken something.

Is there a fix for that?

---

### Post by kamkar1 on 2012-10-07
Recently upgraded to 11.10, and started having loading issues with firefox & chrome.
I changed the wireless setting to Automatic dhcp, and changed my router from dual mode (NG) to only (G). That seems to have fixed my problem.

---

