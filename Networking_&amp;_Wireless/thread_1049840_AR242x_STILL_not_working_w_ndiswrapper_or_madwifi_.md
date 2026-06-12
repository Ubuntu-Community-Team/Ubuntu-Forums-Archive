---
title: "AR242x STILL not working w/ ndiswrapper or madwifi (Intrepid)"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by e_racer1999 on 2009-01-25
I've tried and tried and tried for close to a WEEK!

All of the sudden my wifi stopped working in Hardy. Tried troubleshooting and googling to no avail.

Followed these instructions for nidswrapper:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Card is recognized and driver works but device does nothing.

Madwifi (ath_pci, ath_hal, and ath5k) doesn't work either.


iwconfig:
> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg:
> [   13.133959] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   13.380342] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.380374] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.466824] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   13.467124] ndiswrapper 0000:03:00.0: enabling device (0000 -> 0002)
[   13.467134] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.467174] ndiswrapper (ZwClose:2198): closing handle 0xf6aeed28 not implemented
[   13.467364] ndiswrapper 0000:03:00.0: setting latency timer to 64
[   14.284309] ACPI: Battery Slot [BAT1] (battery present)
[   14.284957] ACPI: WMI: Mapper loaded
[   14.461110] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[   14.476040] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.871114] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   14.928049] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   15.246693] ndiswrapper: using IRQ 17
[   15.448566] wlan0: ethernet device 00:19:7e:35:02:66 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   15.453968] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK




Anyone else having these problems recently? Let me know what you want me to run and I'll post the results.

---

### Post by kevdog on 2009-01-25
Enable the linux backport modules within the /etc/apt/sources.list or within synaptic so you can download and enable the ath5k driver.

---

### Post by Cannaregio on 2009-01-25
I had a similar problem on a PackardBell netbook ("dot 010").
Tried both Intrepid and Jaunty (beta 3) on it... to no avail.
Tried ndiswrapper and many madwifi manipulations... to no avail.

Finally I had to ditch Ubuntu and Install [COLOR="Blue"]Fedora 10[/COLOR] instead. 
Works like a charm with the [COLOR="Blue"]Atheros AR242x[/COLOR], that was recognized immediately "out of the USB" without any fuss.
I don't like Fedora/Red Hat as much as our Debian distros, but that definitively solved my problem.

If anyone cares to try some other distros I hope he'll let us know what worked and what not (I might try to install Sabayon just to see if it works as well as Fedora on this netbook).

A pity, one box less for Ubuntu :-(
Let's hope the Ubuntu developers will learn from Fedora how to recognize this rather common card :-)

---

### Post by e_racer1999 on 2009-01-25
> **kevdog said:**
> Enable the linux backport modules within the /etc/apt/sources.list or within synaptic so you can download and enable the ath5k driver.

No luck with that either. ath5k simply isn't working for me, which is why I resorted to ndiswrapper, but no dice on that :(. I think I may try Fedora, but I've been otherwise satisfied w/ Ubuntu (I had been running it successfully for ~2 yrs until the wireless suddenly stopped working)

---

### Post by kevdog on 2009-01-25
Telling us things are not working for you is not very helpful.  That is such a noob way of crying and explaining things.  You need to provide specifics if you want any meaningful help.

---

### Post by e_racer1999 on 2009-01-26
> **kevdog said:**
> Telling us things are not working for you is not very helpful.  That is such a noob way of crying and explaining things.  You need to provide specifics if you want any meaningful help.

What? I am simply asking for help. I'm sorry if I'm not the most proficient at Ubuntu; I had hoped that when I asked for some assistance people tried to help me out and teach me so that I might be a little better at providing the right information.

At any rate, here's is the corresponding information in syslog:

```
Jan 26 15:52:23 laptop NetworkManager: <info>  wlan0: driver is 'ath5k_pci'. 
Jan 26 15:52:23 laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jan 26 15:52:23 laptop NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Jan 26 15:52:23 laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_19_7e_35_02_66_0 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): bringing up device. 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): preparing device. 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Jan 26 15:52:27 laptop NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
```

I'm assuming it's the "(reason: 2)" that is preventing this from working. By the way, this is currently without ndiswrapper or madwifi and I am attempting to run the backport module. FYI - in the Restricted Hardware Driver section the "Support for 5xxx Atheros" driver will not activate. I already removed ath_hal, ath_pci, ath5k, and ath5k_pci from ~/etc/modprobe.d/blacklist

---

### Post by ch33zy on 2009-01-28
I had to build compat-wireless from source to get mine working.  Had to rebuild today after the kernel upgrade, as well.  Google for compat-wireless to find the tar-ball and instructions for building.

---

