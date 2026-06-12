---
title: "new at ubuntu - problem connecting til wireless"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by BubbiBjQrn on 2009-11-10
Hey i just upgraded my ubuntu to 9.10 but after i have upgraded then i can't connect to my wireless.

i can scan the network but i can't connect, and i'm sure that i'm typing the right wpa2 key

peter@peter-laptop:~$ dmesg |grep intel
[    0.001679]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.001684]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    1.467489] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.629063] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   14.152050] intel8x0_measure_ac97_clock: measured 55433 usecs (2671 samples)
[   14.152056] intel8x0: clocking to 48000
[   21.480343] intel_rng: FWH not detected
[   27.486802] ieee80211: Copyright (C) 2004-2005 Intel Corporation <[EMAIL="jketreno@linux.intel.com"]jketreno@linux.intel.com[/EMAIL]>
[   33.276381] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   33.276403] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode

taking from syslog

Nov 10 11:30:52 peter-laptop wpa_supplicant[1000]: Trying to associate with 00:23:f8:0b:bf:29 (SSID='sonicwall' freq=2472 MHz)
Nov 10 11:30:52 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 10 11:30:52 peter-laptop wpa_supplicant[1000]: Association request to the driver failed
Nov 10 11:30:53 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 10 11:30:53 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 10 11:30:57 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-SCAN-RESULTS 
Nov 10 11:30:57 peter-laptop wpa_supplicant[1000]: Trying to associate with 00:23:f8:0b:bf:29 (SSID='sonicwall' freq=2472 MHz)
Nov 10 11:30:57 peter-laptop wpa_supplicant[1000]: Association request to the driver failed
Nov 10 11:30:57 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating
Nov 10 11:30:58 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 10 11:30:58 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 10 11:31:01 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-SCAN-RESULTS 
Nov 10 11:31:01 peter-laptop wpa_supplicant[1000]: Trying to associate with 00:23:f8:0b:bf:29 (SSID='sonicwall' freq=2472 MHz)
Nov 10 11:31:01 peter-laptop wpa_supplicant[1000]: Association request to the driver failed
Nov 10 11:31:01 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating
Nov 10 11:31:02 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 10 11:31:02 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 10 11:31:06 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-SCAN-RESULTS 
Nov 10 11:31:06 peter-laptop wpa_supplicant[1000]: Trying to associate with 00:23:f8:0b:bf:29 (SSID='sonicwall' freq=2472 MHz)
Nov 10 11:31:06 peter-laptop wpa_supplicant[1000]: Association request to the driver failed
Nov 10 11:31:06 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating
Nov 10 11:31:07 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 10 11:31:07 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 10 11:31:08 peter-laptop NetworkManager: <info>  eth1: link timed out.
Nov 10 11:31:10 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 10 11:31:10 peter-laptop wpa_supplicant[1000]: CTRL-EVENT-SCAN-RESULTS 
Nov 10 11:31:10 peter-laptop wpa_supplicant[1000]: Trying to associate with 00:23:f8:0b:bf:29 (SSID='sonicwall' freq=2472 MHz)
Nov 10 11:31:10 peter-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating

hope that anyone can help me

---

