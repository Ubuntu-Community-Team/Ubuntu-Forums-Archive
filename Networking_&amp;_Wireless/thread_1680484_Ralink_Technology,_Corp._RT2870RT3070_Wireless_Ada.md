---
title: "Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by Zeno Cosini on 2011-02-02
As the built-in wireless of my notebook failed some time ago, I am now trying a HAMA WLAN USB stick ( 62278 ) under Ubuntu 10.10. 

When plugging it in, the NetworkManager Applet shows the new entry "Wireless Network (Ralink 802.11 n WLAN) - wireless is disabled". The option "Enable Wireless" is grayed-out.

What do I have to do to enable it?

Here are a few pieces of information:

The relevant line in the output of "lsusb" is as follows:

```

Bus 001 Device 010: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
```

"iwconfig" shows the following:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

"lsmod | grep -e rt" shows the following:

```

parport_pc             26058  0 
rt2870sta             406690  0 
crc_ccitt               1351  1 rt2870sta
parport                31492  3 parport_pc,ppdev,lp
agpgart                32011  3 ttm,drm,ati_agp
```

Finally, "ls /etc/modprobe.d | grep -e ndis -e black" results in

```

blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
```

---

### Post by TBABill on 2011-02-07
Can you paste back here the contents of the file /etc/modprobe.d/blacklist.conf? That may be the key here since you have the right driver enabled already in /etc/modules.

---

### Post by Zeno Cosini on 2011-02-08
> **TBABill said:**
> Can you paste back here the contents of the file /etc/modprobe.d/blacklist.conf?

Sure, here it is:

```
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

# added because of problems with Ralink RT2870/RT3070 Wireless Adapter
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
```

---

### Post by Zeno Cosini on 2011-02-16
> **TBABill said:**
> Can you paste back here the contents of the file /etc/modprobe.d/blacklist.conf?

Any idea after seeing the file blacklist.conf?

---

