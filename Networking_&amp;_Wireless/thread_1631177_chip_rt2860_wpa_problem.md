---
title: "chip rt2860 wpa problem"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by Dsky on 2010-11-26
i found this

> WPA/WPA2 are broken in every module everybody has tried (AFAIK) since Adam's 1.7.1.1 DKMS driver. Downgrade like so:

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

2) Go to terminal, and move the pre-installed driver so it won't get loaded.

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak


3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

the deb file gives me an error.. i'm a little new with ubuntu... can anybody help me?

---

### Post by chili555 on 2010-11-26
The .deb file you are using is for the Ubuntu version Intrepid. That's quite old. I notice his site no similar versions up to the still quite old Jaunty. That suggests he has discontinued development because the issue no longer exists. At the least, I'd suggest you post the exact error here. Also, we'd be happy to troubleshoot your rt2860sta issues. What are your symptoms? As you attempt to connect, what does this tell us?```
sudo tail -n50 /var/log/syslog 
uname -r
modinfo rt2860sta | grep version
```

---

### Post by Dsky on 2010-11-26
thanks so much

```
uname -r
2.6.35-23-generic
fil@fil-901:~$ modinfo rt2860sta | grep version
version:        2.1.0.0
srcversion:     1CC5B0F527E33CC4AF73D2B
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
```

```

Nov 26 15:24:02 fil-901 kernel: [ 5338.321936] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 1)
Nov 26 15:24:02 fil-901 kernel: [ 5338.520142] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 2)
Nov 26 15:24:02 fil-901 kernel: [ 5338.720136] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 3)
Nov 26 15:24:03 fil-901 kernel: [ 5338.920140] wlan0: direct probe to fc:fb:fb:6b:a7:10 timed out
Nov 26 15:24:12 fil-901 wpa_supplicant[784]: Authentication with fc:fb:fb:6b:a7:10 timed out.
Nov 26 15:24:12 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Nov 26 15:24:12 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Nov 26 15:24:13 fil-901 wpa_supplicant[784]: Trying to associate with fc:fb:fb:6b:a7:10 (SSID='SERRA-PACINOTTI' freq=2412 MHz)
Nov 26 15:24:13 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  scanning -> associating
Nov 26 15:24:13 fil-901 kernel: [ 5349.572538] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 1)
Nov 26 15:24:13 fil-901 kernel: [ 5349.773080] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 2)
Nov 26 15:24:14 fil-901 NetworkManager[708]: <warn> (wlan0): link timed out.
Nov 26 15:24:14 fil-901 kernel: [ 5349.972182] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 3)
Nov 26 15:24:14 fil-901 kernel: [ 5350.172206] wlan0: direct probe to fc:fb:fb:6b:a7:10 timed out
Nov 26 15:24:23 fil-901 wpa_supplicant[784]: Authentication with fc:fb:fb:6b:a7:10 timed out.
Nov 26 15:24:23 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Nov 26 15:24:23 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Nov 26 15:24:24 fil-901 wpa_supplicant[784]: Trying to associate with fc:fb:fb:6b:a7:10 (SSID='SERRA-PACINOTTI' freq=2412 MHz)
Nov 26 15:24:24 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  scanning -> associating
Nov 26 15:24:24 fil-901 kernel: [ 5360.820300] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 1)
Nov 26 15:24:25 fil-901 kernel: [ 5361.020773] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 2)
Nov 26 15:24:25 fil-901 kernel: [ 5361.220120] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 3)
Nov 26 15:24:25 fil-901 kernel: [ 5361.420079] wlan0: direct probe to fc:fb:fb:6b:a7:10 timed out
Nov 26 15:24:26 fil-901 NetworkManager[708]: <warn> Activation (wlan0/wireless): association took too long.
Nov 26 15:24:26 fil-901 NetworkManager[708]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Nov 26 15:24:26 fil-901 NetworkManager[708]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 26 15:24:26 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0/wireless): connection 'Auto SERRA-PACINOTTI' has security, and secrets exist.  No new secrets needed.
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Config: added 'ssid' value 'SERRA-PACINOTTI'
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Config: added 'scan_ssid' value '1'
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Config: added 'psk' value '<omitted>'
Nov 26 15:24:30 fil-901 NetworkManager[708]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 26 15:24:30 fil-901 NetworkManager[708]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> Config: set interface ap_scan to 1
Nov 26 15:24:30 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Nov 26 15:24:31 fil-901 wpa_supplicant[784]: Trying to associate with fc:fb:fb:6b:a7:10 (SSID='SERRA-PACINOTTI' freq=2412 MHz)
Nov 26 15:24:31 fil-901 NetworkManager[708]: <info> (wlan0): supplicant connection state:  scanning -> associating
Nov 26 15:24:31 fil-901 kernel: [ 5367.609346] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 1)
Nov 26 15:24:31 fil-901 kernel: [ 5367.808221] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 2)
Nov 26 15:24:32 fil-901 kernel: [ 5368.008227] wlan0: direct probe to fc:fb:fb:6b:a7:10 (try 3)
Nov 26 15:24:32 fil-901 kernel: [ 5368.208225] wlan0: direct probe to fc:fb:fb:6b:a7:10 timed out

```

---

### Post by Dsky on 2010-11-26
i tried this and now it works.... is it fine?


> **TBABill said:**
> I searched the forums for answers and finally came across the fix for my wireless. It works perfectly in 10.04 and cannot connect to a network in 10.10. The card is a Ralink RT2860 and normally works out of the box with any distro, but here's what I found on the forums that fixed mine (so others can search and find an answer easily):
 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
Add the following lines to the end of blacklist.conf:
> blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

---

### Post by chili555 on 2010-11-26
If it works, it's fine! Post back if you have any more issues.

---

### Post by Dsky on 2010-11-26
thanks ;)

no more issues at the moment

---

### Post by Dsky on 2010-12-08
after the last updating the problem appeared again....

how can i check last updates?

---

### Post by chili555 on 2010-12-09
Please do:```
sudo modprobe rt2860sta
dmesg | grep -i rt2
```Let's see if there are any errors or interesting messages.

---

### Post by Dsky on 2010-12-09
> fil@fil-901:~$ sudo modprobe rt2860sta
[sudo] password for fil: 
fil@fil-901:~$ dmesg | grep -i rt2
[    6.827947] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.239632] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.239726] rt2860 0000:01:00.0: setting latency timer to 64
[    8.431362] <==== rt28xx_init, Status=0
[    8.634533] <==== rt28xx_init, Status=0


i would only to take off the last changes of the update

---

### Post by chili555 on 2010-12-09
> after the last updating the problem appeared again....What problem, exactly? I don't think you ever really told us the exact nature of your problem. Please post:```
lspci -nn
cat /etc/modprobe.d/blacklist.conf
lsmod | grep rt2
```Thanks.

---

### Post by Dsky on 2010-12-09
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
04:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

```

```
cat /etc/modprobe.d/blacklist.conf
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

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

```

```
lsmod | grep rt2
rt2860sta             504366  1 
crc_ccitt               1351  1 rt2860sta

```

---

### Post by TBABill on 2010-12-09
Would it improve if you ```
sudo gedit /etc/modules
``` and add ```
rt2860
rt2860sta
``` to the end of that file, save and restart?

---

### Post by Dsky on 2010-12-09
in this way i tried and still not working (keep asking the password of the WPA.. the same problem i had at first 

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

rt2860
rt2860sta

---

### Post by TBABill on 2010-12-09
I wonder if it is just being blocked for some strange reason since it was just working perfectly for you? Chili could tell for sure...the obvious wireless expert to be sure. Perhaps you will get a response soon with additional information. However, in the meantime can you look at ```
sudo rfkill list
``` and see if you are soft or hard blocked?

---

### Post by Dsky on 2010-12-09
it turned back on work again..

dont ask me why :-)

let see .... thanks for the moment

---

### Post by TBABill on 2010-12-09
Great news!

---

