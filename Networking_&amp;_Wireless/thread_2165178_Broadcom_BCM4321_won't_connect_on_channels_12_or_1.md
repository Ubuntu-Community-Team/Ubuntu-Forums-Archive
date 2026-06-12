---
title: "Broadcom BCM4321 won't connect on channels 12 or 13"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by peterx14 on 2013-08-03
Hi all,

This is all on a MacBook that was running Ubuntu 12.04 and has just been upgraded to 12.10 and then 13.04. Each of those Ubuntu versions had the same problem:

Wifi on my MacBook 3,1 works perfectly **except** not on channels > 11. I've added my country code, GB, to /etc/default/crda and whilst it appears to have those frequencies working, a scan never picks up my local network (which is on ch.13).

```

$ lspci -vvnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
```

```

$ sudo iw list 
Wiphy phy0
	Band 1:
		Frequencies:
			* 2412 MHz [1] (20.0 dBm)
			* 2417 MHz [2] (20.0 dBm)
			* 2422 MHz [3] (20.0 dBm)
			* 2427 MHz [4] (20.0 dBm)
			* 2432 MHz [5] (20.0 dBm)
			* 2437 MHz [6] (20.0 dBm)
			* 2442 MHz [7] (20.0 dBm)
			* 2447 MHz [8] (20.0 dBm)
			* 2452 MHz [9] (20.0 dBm)
			* 2457 MHz [10] (20.0 dBm)
			* 2462 MHz [11] (20.0 dBm)
			* 2467 MHz [12] (20.0 dBm)
			* 2472 MHz [13] (20.0 dBm)
			* 2484 MHz [14] (disabled)
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	Band 2:
		Frequencies:
			* 5160 MHz [32] (30.0 dBm)
			* 5170 MHz [34] (30.0 dBm)
			* 5180 MHz [36] (30.0 dBm)
			* 5190 MHz [38] (30.0 dBm)
			* 5200 MHz [40] (30.0 dBm)
			* 5210 MHz [42] (30.0 dBm)
			* 5220 MHz [44] (30.0 dBm)
			* 5230 MHz [46] (30.0 dBm)
			* 5240 MHz [48] (30.0 dBm)
			* 5250 MHz [50] (30.0 dBm)
			* 5260 MHz [52] (30.0 dBm)
			* 5270 MHz [54] (30.0 dBm)
			* 5280 MHz [56] (30.0 dBm)
			* 5290 MHz [58] (30.0 dBm)
			* 5300 MHz [60] (30.0 dBm)
			* 5310 MHz [62] (30.0 dBm)
			* 5320 MHz [64] (30.0 dBm)
			* 5330 MHz [66] (30.0 dBm)
			* 5340 MHz [68] (30.0 dBm)
			* 5350 MHz [70] (30.0 dBm)
			* 5360 MHz [72] (30.0 dBm)
			* 5370 MHz [74] (30.0 dBm)
			* 5380 MHz [76] (30.0 dBm)
			* 5390 MHz [78] (30.0 dBm)
			* 5400 MHz [80] (30.0 dBm)
			* 5410 MHz [82] (30.0 dBm)
			* 5420 MHz [84] (30.0 dBm)
			* 5430 MHz [86] (30.0 dBm)
			* 5440 MHz [88] (30.0 dBm)
			* 5450 MHz [90] (30.0 dBm)
			* 5460 MHz [92] (30.0 dBm)
			* 5470 MHz [94] (30.0 dBm)
			* 5480 MHz [96] (30.0 dBm)
			* 5490 MHz [98] (30.0 dBm)
			* 5500 MHz [100] (30.0 dBm)
			* 5510 MHz [102] (30.0 dBm)
			* 5520 MHz [104] (30.0 dBm)
			* 5530 MHz [106] (30.0 dBm)
			* 5540 MHz [108] (30.0 dBm)
			* 5550 MHz [110] (30.0 dBm)
			* 5560 MHz [112] (30.0 dBm)
			* 5570 MHz [114] (30.0 dBm)
			* 5580 MHz [116] (30.0 dBm)
			* 5590 MHz [118] (30.0 dBm)
			* 5600 MHz [120] (30.0 dBm)
			* 5610 MHz [122] (30.0 dBm)
			* 5620 MHz [124] (30.0 dBm)
			* 5630 MHz [126] (30.0 dBm)
			* 5640 MHz [128] (30.0 dBm)
			* 5650 MHz [130] (30.0 dBm)
			* 5660 MHz [132] (30.0 dBm)
			* 5670 MHz [134] (30.0 dBm)
			* 5680 MHz [136] (30.0 dBm)
			* 5690 MHz [138] (30.0 dBm)
			* 5700 MHz [140] (30.0 dBm)
			* 5710 MHz [142] (30.0 dBm)
			* 5720 MHz [144] (30.0 dBm)
			* 5725 MHz [145] (30.0 dBm)
			* 5730 MHz [146] (30.0 dBm)
			* 5735 MHz [147] (30.0 dBm)
			* 5740 MHz [148] (30.0 dBm)
			* 5745 MHz [149] (30.0 dBm)
			* 5750 MHz [150] (30.0 dBm)
			* 5755 MHz [151] (30.0 dBm)
			* 5760 MHz [152] (30.0 dBm)
			* 5765 MHz [153] (30.0 dBm)
			* 5770 MHz [154] (30.0 dBm)
			* 5775 MHz [155] (30.0 dBm)
			* 5780 MHz [156] (30.0 dBm)
			* 5785 MHz [157] (30.0 dBm)
			* 5790 MHz [158] (30.0 dBm)
			* 5795 MHz [159] (30.0 dBm)
			* 5800 MHz [160] (30.0 dBm)
			* 5805 MHz [161] (30.0 dBm)
			* 5810 MHz [162] (30.0 dBm)
			* 5815 MHz [163] (30.0 dBm)
			* 5820 MHz [164] (30.0 dBm)
			* 5825 MHz [165] (30.0 dBm)
			* 5830 MHz [166] (30.0 dBm)
			* 5840 MHz [168] (30.0 dBm)
			* 5850 MHz [170] (30.0 dBm)
			* 5860 MHz [172] (30.0 dBm)
			* 5870 MHz [174] (30.0 dBm)
			* 5880 MHz [176] (30.0 dBm)
			* 5890 MHz [178] (30.0 dBm)
			* 5900 MHz [180] (30.0 dBm)
			* 5910 MHz [182] (30.0 dBm)
			* 5920 MHz [184] (30.0 dBm)
			* 5930 MHz [186] (30.0 dBm)
			* 5940 MHz [188] (30.0 dBm)
			* 5950 MHz [190] (30.0 dBm)
			* 5960 MHz [192] (30.0 dBm)
			* 5970 MHz [194] (30.0 dBm)
			* 5980 MHz [196] (30.0 dBm)
			* 5990 MHz [198] (30.0 dBm)
			* 6000 MHz [200] (30.0 dBm)
			* 6010 MHz [202] (30.0 dBm)
			* 6020 MHz [204] (30.0 dBm)
			* 6030 MHz [206] (30.0 dBm)
			* 6040 MHz [208] (30.0 dBm)
			* 6050 MHz [210] (30.0 dBm)
			* 6060 MHz [212] (30.0 dBm)
			* 6070 MHz [214] (30.0 dBm)
			* 6080 MHz [216] (30.0 dBm)
			* 6090 MHz [218] (30.0 dBm)
			* 6100 MHz [220] (30.0 dBm)
			* 6110 MHz [222] (30.0 dBm)
			* 6120 MHz [224] (30.0 dBm)
			* 6130 MHz [226] (30.0 dBm)
			* 6140 MHz [228] (30.0 dBm)
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	max # scan SSIDs: 1
	max scan IEs length: 0 bytes
	Coverage class: 0 (up to 0m)
	Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP (00-0f-ac:4)
		* CMAC (00-0f-ac:6)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * IBSS
		 * managed
	software interface modes (can always be added):
	interface combinations are not supported
	Supported commands:
		 * set_interface
		 * new_key
		 * join_ibss
		 * set_pmksa
		 * del_pmksa
		 * flush_pmksa
		 * connect
		 * disconnect

```

It appears to scan all the channel 1 to 11 access points fine, but refuses to look at anything else!

Any help appreciated!!

Peter.

---

### Post by praseodym on 2013-08-04
Which driver is in use? Is the package "linux-firmware-nonfree" installed?

Check
```

iwlist chan
```
Have you tried the Broadcom-STA driver?

---

### Post by peterx14 on 2013-08-04
> **praseodym said:**
> Which driver is in use? Is the package "linux-firmware-nonfree" installed?
I'm not sure which driver is installed! It appears to be the "iw" module that's loaded... does that help?
The "linux-firmware-nonfree" package is **not** installed.

iwlist chan says:
```

$ iwlist chan
eth0      no frequency information.

eth1      32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz
lo        no frequency information.

```

> **praseodym said:**
> 
Have you tried the Broadcom-STA driver?
Not sure... I suspect not! Oddly, I don't appear to have an "Additional Drivers" icon in System Settings. Is there a way I can launch it from the command line?

---

### Post by praseodym on 2013-08-04
Broadcom-STA is in use, it renames the interface name from default "wlan0" to "eth1". Install this package:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

and deactivate the STA driver. Reboot.

---

### Post by peterx14 on 2013-08-04
That fixed it - thank you loads Praseodym!! :D

It took me a bit of time to figure out how to deactivate the STA driver because I didn't realise the ["Additional Drivers" stuff has been moved from System Settings and into Software Centre.]("http://askubuntu.com/questions/234799/i-installed-jockey-gtk-but-how-do-i-run-it")Whoops!

So are the Broadcom STA drivers a bit buggy with regard to regional settings?

---

### Post by praseodym on 2013-08-04
Maybe this driver only works on channels 1-11 (bug or purpose)

---

