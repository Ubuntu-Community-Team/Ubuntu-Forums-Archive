---
title: "AWUS036NEH partially working"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mluis on 2012-10-27
Hello.

I have an Ubuntu Server 12.04 running on a Virtualbox VM instance. This Ubuntu's VM
instance is running 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686
i686 i386 GNU/Linux Kernel. When I plug the awus036neh wireless dongle it is automatically
detected on the guest system.

This is the syslog:

```
Oct 27 23:41:42 v0x kernel: [ 2093.520179] usb 1-1: new high-speed USB device number 3 using ehci_hcd
Oct 27 23:41:42 v0x kernel: [ 2093.838014] Compat-wireless backport release: compat-wireless-v3.4-rc3-1-1-g0c7b53f-snp
Oct 27 23:41:42 v0x kernel: [ 2093.838016] Backport based on linux-stable.git v3.4.4
Oct 27 23:41:42 v0x kernel: [ 2093.842764] cfg80211: Calling CRDA to update world regulatory domain
Oct 27 23:41:43 v0x kernel: [ 2093.846700] cfg80211: World regulatory domain updated:
Oct 27 23:41:43 v0x kernel: [ 2093.846707] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 27 23:41:43 v0x kernel: [ 2093.846710] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2093.846714] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2093.846717] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2093.846720] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2093.846724] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.032186] usb 1-1: reset high-speed USB device number 3 using ehci_hcd
Oct 27 23:41:43 v0x kernel: [ 2094.697456] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697459] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697461] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697462] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697463] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697465] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697466] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697467] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697468] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697470] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697471] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697472] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697473] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697475] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697476] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697477] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697478] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697480] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697481] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697482] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697483] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697485] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697486] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697487] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697488] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697490] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697491] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:41:43 v0x kernel: [ 2094.697492] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:41:43 v0x kernel: [ 2094.697602] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Oct 27 23:41:43 v0x kernel: [ 2094.697991] Registered led device: rt2800usb-phy0::radio
Oct 27 23:41:43 v0x kernel: [ 2094.698016] Registered led device: rt2800usb-phy0::assoc
Oct 27 23:41:43 v0x kernel: [ 2094.698039] Registered led device: rt2800usb-phy0::quality
Oct 27 23:41:43 v0x kernel: [ 2094.698455] usbcore: registered new interface driver rt2800usb
```

although being automatically detected:

```

Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

```

```

$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

it is not able to scan:
```

$ iwlist wlan0 scan
wlan0     No scan results

```

and neither work with wpa_supplicant:
```

$ sudo wpa_supplicant -Dwext -i wlan0 -c ~/confs/wpa-psk-tkip.conf 
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.

```

What must one do in order to have this dongle working properly?

Thanks.

---

### Post by mluis on 2013-09-30
It seems that AWUS036NEH was working in kernel version 2.6.35 with rt2800lib.ko and rt2800usb.ko
so I copied those compiled drivers from kernel 2.6 and pasted them under
/lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rt2x00 in kernel version 3.8.0.

It's working.

---

### Post by mörgæs on 2013-09-30
Good, then please mark the thread 'solved' using Thread Tools.

---

