---
title: "No Network Access after Upgrade to 12.10"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by bountonw on 2012-11-05
While upgrading from 12.04 to 12.10 at home on a 3G dongle :) several weeks ago, I was asked to reboot. Upon the reboot, USBs would not mount automatically (including the dongle). Today, I was finally able to bring the box to work but when I tried plugging in the LAN cable it was not recognized.

There were about 700+ MB of downloaded updates that needed installed which I did. For some reason the computer does not recognize eth0 or eth1 for that matter (although there is only one LAN port).

I am not sure where to begin troubleshooting and the terms that I can think to google do not lead anywhere. 

I am thinking that the upgrade didn't happen properly. Is there a way to download all possible network files with dependencies and then apply them manually? I don't want to reinstall if I can avoid it.

---

### Post by bountonw on 2012-11-07
Can someone help prime the pump? I can not for the life of me discover the right terms to google in order to solve my problem.

What bash commands can I use to troubleshoot my network and usb issues?

What are the drivers/programs/apps/files that may have been corrupted by the upgrade that I could download on a different computer and install manually via a mounted usb drive?

How would I go about manually installing the files?

Is there a better solution?

If I get the network working, I can play with apt-get and try to fix anything else that is broken.

Any help is greatly appreciated.

---

### Post by bountonw on 2012-11-07
I can get the USB 3G dongle to open up, but it won't connect. If I could get the 3G dongle working, I wouldn't even worry about the LAN at this stage.

---

### Post by Dn4mycrownj on 2012-11-07
i run 10.04 but i had to delete this file then reboot  the OS regens the file auto



look into your      /etc/udev/rules.d/ 
look for file with suffix

-persistent-net.rules      or

70-persistent-net.rules 

delete that file then 
reboot and try again

that is the name of the file you need but i do not know if that is the location on your build of ubuntu

---

### Post by bountonw on 2012-11-07
Thanks Dn4mycrownj,

Yes, /etc/udev/rules.d contained the file that you mentioned. 

I moved the 70-persistent-net.rules file to my Desktop and rebooted, however, the file did not regenerate and there is still no LAN/3G dongle connection.

---

### Post by varunendra on 2012-11-07
Please post the outputs of (while the USB modem is connected) :
```
lsusb
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
dmesg | tail -20
```

As a side note, upgrades are never guaranteed to work properly. On the contrary, they are prone to errors and such problems. That's why a clean install is always recommended. It has always been an irony that the update manager 'proposes' to upgrade and doesn't warn users of the possible risks.

Also, 12.04 is LTS and switching from an LTS to an interim release is not recommended if you are not an enthusiast and prefer stability over bleeding edge technology.

And the last lesson that you should have already been aware of - always do backups before making any system-wide changes.

---

### Post by bountonw on 2012-11-08
Thank you varunendra,

The grass is always greener on the other side of the upgrade. I was hoping that the stable release would upgrade without problems. I suppose we are enthusiasts. We are at least enthusiastic :)

```
lsusb

Bus 001 Device 003: ID 12d1:1436 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

lspci -nnk | grep -iA2 net

Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI
Express Fast Ethernet controller [10ec:8136] (rev 02)
     Subsystem: ASUSTeK Computer Inc. Device [1043:8347]

```

```
lsmod

Module            Size    Used by
usb_storage       39350    0
vboxpci             22867    0
vboxnetadp       25636    0
vboxnetflt          27232    0
vboxdrv             252270    3    vboxpci, vboxnetadp, vboxnetflt
binfmt_misc      17260    1
ppdev               12817    0
microcode         18209    0
nvidia                10236405    40
psmouse           84843    0
serio_raw          13031    0
parport_pc        31968    1
lp                      13299    0
parport             40753    3    ppdev, parport_pc, lp
floppy               55444    1

```

```
ifconfig -a

lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask: 255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:3520 errors:0 dropped:0 overruns:0 frame:0
           TX packets:3520 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:279520 (279.5 KB)  TX bytes: 279520 (279.5 KB)

```

```
dmesg | tail -20
[ 1111.092592] Buffer I/O error on device fd0, logical block 0
[ 1123.256547] end_request: I/O error, dev fd0, sector 0
[ 1123.256554] Buffer I/O error on device fd0, logical block 0
[ 1135.420500] end_request: I/O error, dev fd0, sector 0
[ 1135.420506] Buffer I/O error on device fd0, logical block 0
[ 1147.576596] end_request: I/O error, dev fd0, sector 0
[ 1147.576602] Buffer I/O error on device fd0, logical block 0
[ 1159.740532] end_request: I/O error, dev fd0, sector 0
[ 1159.740539] Buffer I/O error on device fd0, logical block 0
[ 1171.900722] end_request: I/O error, dev fd0, sector 0
[ 1171.900719] Buffer I/O error on device fd0, logical block 0
[ 1184.068588] end_request: I/O error, dev fd0, sector 0
[ 1196.232544] end_request: I/O error, dev fd0, sector 2
[ 1196.232558] EXT3-fs (fd0): error: unable to read superblock
[ 1208.392510] end_request: I/O error, dev fd0, sector 0
[ 1220.548602] end_request: I/O error, dev fd0, sector 2
[ 1220.548616] EXT4-fs (fd0): error: unable to read superblock
[ 1232.700726] end_request: I/O error, dev fd0, sector 0
[ 1244.852721] end_request: I/O error, dev fd0, sector 0
[ 1244.852735] FAT-fs (fd0): unable to read boot sector

```

After all that typing, I'm a little less enthusiastic, but still an enthusiast :)

---

### Post by varunendra on 2012-11-08
> **bountonw said:**
> After all that typing, I'm a little less enthusiastic, but still an enthusiast :)
I can understand, by the looks of the outputs I feel as if I'm dealing with a minimal install ;)

What happens if you do (please restore the *70-persistent-net.rules* file to its original place and reboot before you do the following) -
```
sudo modprobe -v r8169
```
and check-
```
ifconfig -a
```

If nothing happens, or it gives errors, please post the outputs of following -
```
locate r8169
cat /etc/udev/rules.d/70-persistent-net.rules
sudo lshw -C network
```

As for the usb modem, you may try-
```
sudo modprobe -v option
```
then try plugging-in the modem and see if it makes any difference.

---

### Post by bountonw on 2012-11-12
Thank you Varunendra,

(Been away from the office for a few days. Now I should have daily access to this computer for the rest of the week.)

I restored  the file 70-persistent-net.rules.

```

sudo modprobe -v r8169

FATAL: Module r8169 not found.

```

```

ifconfig -a

lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask: 255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:864 errors:0 dropped:0 overruns:0 frame:0
           TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:68846 (68.8 KB)  TX bytes: 68846 (68.8 KB)
```

I finally got smart and piped the commands and copied to USB which mounted automatically. Not sure why the 3G dongle is still not working...
```

locate r8169

/lib/modules/3.0.0-12-generic/kernel/drivers/net/r8169.ko
/lib/modules/3.0.0-13-generic/kernel/drivers/net/r8169.ko
/lib/modules/3.0.0-16-generic/kernel/drivers/net/r8169.ko
/lib/modules/3.0.0-17-generic/kernel/drivers/net/r8169.ko
/lib/modules/3.2.0-21-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-22-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-23-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-30-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-31-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-32-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.2.0-33-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/usr/src/linux-headers-3.0.0-12-generic/include/config/r8169.h
/usr/src/linux-headers-3.0.0-13-generic/include/config/r8169.h
/usr/src/linux-headers-3.0.0-16-generic/include/config/r8169.h
/usr/src/linux-headers-3.0.0-17-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-21-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-21-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-22-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-22-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-31-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-32-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-32-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.2.0-33-generic/include/config/r8169.h
/usr/src/linux-headers-3.2.0-33-generic-pae/include/config/r8169.h
/usr/src/linux-headers-3.5.0-18-generic/include/config/r8169.h

```

```

cat /etc/udev/rules.d/70-persistent-net.rules

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:15:db:8f:41", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


```

```

sudo lshw -C network

  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff
       memory:febf0000-febfffff

```

```

sudo modprobe -v option

FATAL: Module option not found

```

The LAN is plugged in also but does not connect to the network.
```

sudo ifdown eth0

ifdown: interface eth0 not configured

sudo ifup eth0

Internet Systems Consortium DHCP Client 4.2.4
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Cannot find device "eth0"
Bind socket to interface: No such device
Failed to bring up eth0

```

Again, thank you very much for your help.

---

### Post by varunendra on 2012-11-12
Hmm.. I've never dealt with a situation like this before. Maybe someone more knowledgeable could suggest a better and precise solution.

So let's first consider things that make some sense before eventually trying all the nonsense I'm going to suggest in the last ;)

1) The first thing that comes to mind is to try 'dpkg - repair broken packages' in 'Repair mode'. If everything required is available and intact in /var/cache/apt directory, it should be able to install/fix broken packages.

2) Another way may be using [chroot]("https://help.ubuntu.com/community/BasicChroot") from a live cd of same version of 12.10 that you have installed. But I've never used it myself so can't say if it'll work as I'm expecting. The idea is to get connected to internet using a live cd of 12.10 --> then 'chroot' into the '/' of the installed ubuntu --> then do -
```
sudo apt-get install --reinstall linux-image-[COLOR=DarkRed]*<currently installed version here>*[/COLOR] linux-headers-[COLOR=DarkRed]*<currently installed version here>*[/COLOR]
sudo apt-get update
sudo apt-get dist-upgrade
```You can get the current version by -
```
uname -r
``` *(From the output of 'locate' it looks like it is **3.5.0-18-generic**)*


Now something that is my own 'brrrilliant' idea.. :D (thus almost guaranteed to fail miserably) -

If you have the .deb package of the last downloaded kernel image (that you are currently using) in your /var/cache/apt/archives directory (if not, you can download it [from here]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/")), you can open it on archive manager, browse to '/lib/modules/[COLOR=DarkRed]*<your version here>*[/COLOR]/kernel/drivers/net/ethernet/realtek/' and simply extract the r8169.ko file to your desktop.

Once you have the r8169.ko driver (for your ethernet) file on the desktop, do the following (you can copy-paste the commands to avoid typos)-
```
cd ~/Desktop
sudo su
cp r8169.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/realtek/
depmod -a
modprobe -v r8169
exit
```If any of this returns any errors, post back the error and we may try to dig deeper.

However, if (against my expectation) everything goes fine, you should have your ethernet up and running (hopefully). In that case, also do the following (immediately after you get connected) -
```
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
```Reboot and see if the ethernet is detected.

---

