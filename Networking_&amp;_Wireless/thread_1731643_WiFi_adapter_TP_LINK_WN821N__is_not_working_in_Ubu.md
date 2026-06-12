---
title: "WiFi adapter TP LINK WN821N  is not working in Ubuntu 10.10"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by dealancer on 2011-04-17
WN821N is notworking. Please, need help. 

dmesg|tail

```

[   14.513504] r8169 0000:01:00.0: eth0: link up
[   14.513513] r8169 0000:01:00.0: eth0: link up
[   24.526233] eth0: no IPv6 routers present
[   36.369220] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   36.371159] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   38.037394] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   38.189209] EXT4-fs (sda8): re-mounted. Opts: user_xattr,commit=0
[  130.645969] lo: Disabled Privacy Extensions
[  729.317442] usb 2-1.1: USB disconnect, address 3
[  732.579109] usb 2-1.1: new high speed USB device using ehci_hcd and address 7

```

lsusb

```

Bus 002 Device 007: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 002 Device 006: ID 041e:406b Creative Technology, Ltd 
Bus 002 Device 005: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 002 Device 004: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

hwinfo --usb

```

07: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_cf3_7015_12345_if0
  Unique ID: R8DB.PdzA0RnclB9
  Parent ID: FKGF.0j9+vWlqL56
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0
  SysFS BusID: 2-1.1:1.0
  Hardware Class: unknown
  Model: "Atheros UB95"
  Hotplug: USB
  Vendor: usb 0x0cf3 "Atheros Communications, Inc."
  Device: usb 0x7015 "UB95"
  Revision: "2.02"
  Serial ID: "12345"
  Speed: 480 Mbps
  Module Alias: "usb:v0CF3p7015d0202dcFFdscFFdpFFicFFisc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 20:cf:30:bb:da:fd  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:febb:dafd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3184833 (3.1 MB)  TX bytes:594476 (594.4 KB)
          Interrupt:44 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33920 (33.9 KB)  TX bytes:33920 (33.9 KB)

```

---

### Post by dealancer on 2011-04-22
Any ideas?

---

### Post by eeverson on 2011-04-22
I have exactly the same issue. I have tried using compat-wireless and that failed so have fun out of ideas.

Will post back if I find a fix.

---

### Post by eeverson on 2011-04-22
I have fixed it... however the bad point is that I am not sure what I did to actually fix it.

I installed compat-wireless-2.6.35-1 by downloading the tar from their web site.

[http://wireless.kernel.org/en/users/Download/stable/#Older_stable_release](http://wireless.kernel.org/en/users/Download/stable/#Older_stable_release)

cd /path/to/compat-wireless-2.6.32-rc5


There is a bug in this release and thus you need to replace the following file.
sudo mv scripts/update-initramfs scripts/update-initramfs_old

sudo vi script/update-initramfs

and paste in the following code:

> #!/bin/bash
# Copyright 2009        Luis R. Rodriguez <mcgrof@gmail.com>
#
# Since we provide ssb, the Ethernet module b44 some people may
# rely on it to netboot, so update the initrafms for each
# distribution.
#
# Note that in the future people may want to wireless-boot
# so this will help with that as well.

LSB_RED_ID=$(/usr/bin/lsb_release -i -s)

KLIB=/lib/modules/2.6.31-wl/build
KLIB=/lib/modules/$(uname -r)/build
ver=$(echo $KLIB | awk -F "/lib/modules/" '{print $2}' | awk -F"/" '{print $1}')
dir=/boot/

case $LSB_RED_ID in
"Ubuntu")
        echo "Updating Ubuntu's initramfs for $ver under $dir ..."
        mkinitramfs -o $dir/initrd.img-$ver $ver
        echo "Will now run update-grub to ensure grub will find the new initramfs ..."
        update-grub
        mkinitramfs -o $dir/initrd.img-$ver $ver
        update-initramfs -u
        echo "update complete"
        echo "Will now run update-grub to ensure grub will find the new initramfs ..."
        update-grub
        ;;
*)
        echo "Warning:"
;;

esac

now start to compile compat wireless

sudo make
sudo make install

NOTE: I missed the step out to select the driver to install. On previous installs when I selected the driver it didn't work.

Reboot (remove the USB device before start up so you can see the logs when its inserted)

On reboot insert the USB device and then run:

dmesg tail

and you should hopefully see wan0. If you do then run the following to restart networkmanager and you are off and running.

sudo /etc/init.d/networkmanager restart

If its still not working go back into the compat wireless folder and run the following command to uninstall it. I think I had to do this to get mine working, but this is the point where I lost track of changes i had made.

sudo make uninstall

Then do the restart procedure again.

Good luck :)

---

