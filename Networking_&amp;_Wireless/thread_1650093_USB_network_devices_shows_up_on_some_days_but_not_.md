---
title: "USB network devices shows up on some days but not on others"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by bluesmoon on 2010-12-21
I'm using Ubuntu 10.10 with linux-2.6.35-23-generic

I have a USB cable modem that shows up:
$ lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 069a:4501 Askey Computer Corp. Scientific-Atlanta WebSTAR 2000 series Cable Modem
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


It's the Askey Computer Corp entry up there.

Now when I set this up yesterday, the cdc_ether / usbnet modules loaded up and set up the device as eth1 and assigned it a mac address.  This is what showed up in /var/log/messages:

Dec 20 12:20:26 homestead kernel: [   33.191780] cdc_ether 6-1:1.0: eth0: register 'cdc_ether' at usb-0000:00:1d.1-1, CDC Eth
ernet Device, 00:1a:c3:5c:33:ef
Dec 20 12:20:26 homestead kernel: [   33.192243] usbcore: registered new interface driver cdc_ether
Dec 20 12:20:26 homestead kernel: [   33.219729] cfg80211: World regulatory domain updated:
Dec 20 12:20:26 homestead kernel: [   33.219733]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 20 12:20:26 homestead kernel: [   33.219737]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 20 12:20:26 homestead kernel: [   33.219740]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 20 12:20:26 homestead kernel: [   33.219743]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 20 12:20:26 homestead kernel: [   33.219746]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 20 12:20:26 homestead kernel: [   33.219749]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
...
Dec 20 12:20:26 homestead kernel: [   34.780783] udev[424]: renamed network interface eth0 to eth1


This worked correctly across reboots.

Today it no longer works.  The usbnet and cdc_ether modules do not automatically get loaded into the kernel.  When I plug in the device, this is all that I see:
Dec 21 14:24:00 homestead kernel: [ 2426.696106] usb 6-1: new full speed USB device using uhci_hcd and address 4

lsmod | grep usb
gives me nothing.

Is there some way to explicitly tell the usb subsystem to load the cdc_ether module when this device is plugged in and to get it to associate it with eth1?

---

### Post by chili555 on 2010-12-21
You might just tell the system to load the modules at boot no matter what. In a terminal:```
sudo su
echo cdc_ether >> /etc/modules
exit
```

---

### Post by bluesmoon on 2010-12-21
Adding the module itself has no effect on the system.  There seems to be something else that tells the kernel that that particular device is a network device handled by cdc_ether and I can't tell what that is.

---

### Post by bluesmoon on 2010-12-22
And today it appears to be working again without me doing anything.

Dec 22 12:32:54 homestead kernel: [   29.111917] cdc_ether 6-1:1.0: eth0: register 'cdc_ether' at usb-0000:00:1d.1-1, CDC Eth
ernet Device, 00:1a:c3:5c:33:ef
Dec 22 12:32:54 homestead kernel: [   29.112062] usbcore: registered new interface driver cdc_ether
Dec 22 12:32:54 homestead kernel: [   29.159075] [drm] Initialized drm 1.1.0 20060810
Dec 22 12:32:54 homestead kernel: [   29.189129] udev[437]: renamed network interface eth0 to eth1

---

