---
title: "Strange problem in just one wifi cafe ..."
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2013-04-06
Kubuntu 12.04, acer d270 netbook with broadcom 4313 wireless card.  No windows partition anymore.

This is very strange to me, and I don't know if this may be beyond the scope of this forum, but my wireless does very strange things in just one hotspot cafe in the four ones I go to.  Not only is it just in one place, my netbook is apparently the only machine that causes this problem.

I thought I  had it solved.  I had mint 13 (ubuntu 12.04 based) installed with the patched older generic non-pae kernel to run the cedarview graphics drivers.  As it turns out, that method solves the video problem but can introduce other problems due to holding an older kernel/headers.

Then I discovered the right way to do that and installed kubuntu 12.04 and installed the drivers through additional drivers after updating the kernel.  It worked fine in this place a couple of times.  Then yesterday it did it again.

What happens is that generally it takes forever to configure the network address when I boot kubuntu.

Then, the network goes dead for everyone else.  Of course, they think I'm downloading massive amounts of data (they haven't set up their network very much so it isn't blocked), but I was just browsing with firefox.  And I'm not getting decent response either.  

Then I lost connection and when I clicked the network management widget on the panel it couldn't even find their router.

Like many cafes, their network isn't maintained a whole lot.  If at all.  If it stopped working it'd take them a week to get someone to look at it.  And their baristas aren't any more technically literate than the average one.  So not  much help there.

I'm clueless at this point.  My other laptops never caused this problem there.  Maybe my wireless card just doesn't like poorly configured networks.  I'm weak with this sort of thing anyway.

I haven't set up a firewall yet because I'm still in the process of figuring it out.  That could very well be a problem here, but in that case why does it take forever to configure the address in the first place?  Everywhere else I go, it's almost always connected by the time boot is complete.

---

### Post by praseodym on 2013-04-06
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Plus the outputs when connected there:
```
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
route -n
```

---

### Post by Rob Sayer on 2013-04-07
Thanks for the response.  I'll get back to you next time I go there.

---

### Post by Rob Sayer on 2013-04-08
OK, here's what you requested. The first part I was connected to a network that hasn't caused problems. I'll delete their names for privacy.

~$ lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Acer Incorporated [ALI] Device [1025:061f]
Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Foxconn International, Inc. Device [105b:e042]
Kernel driver in use: wl
```

~$ lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1bcf:288a Sunplus Innovation Technology Inc.
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. Cruzer
```

$ lsmod
```
Module Size Used by
nls_iso8859_1 12617 1
nls_cp437 12751 1
vfat 17308 1
fat 55605 1 vfat
usb_storage 39683 1
usbhid 41937 0
hid 77428 1 usbhid
snd_hrtimer 12648 1
snd_hda_codec_realtek 174313 1
bnep 17830 2
rfcomm 38139 0
bluetooth 158479 10 bnep,rfcomm
snd_hda_codec_hdmi 31775 1
parport_pc 32114 0
ppdev 12849 0
joydev 17393 0
acer_wmi 23612 0
sparse_keymap 13658 1 acer_wmi
binfmt_misc 17292 1
snd_hda_intel 32719 3
snd_hda_codec 109562 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo 67203 0
snd_hwdep 13276 1 snd_hda_codec
videodev 86588 1 uvcvideo
snd_pcm 80916 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse 86520 0
serio_raw 13027 0
snd_seq_midi 13132 0
lib80211_crypt_tkip 17275 0
snd_rawmidi 25424 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51592 3 snd_seq_midi,snd_seq_midi_event
wl 2906597 0
snd_timer 28931 3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
cedarview_gfx 381372 4
snd 62218 17 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm 64734 1 cedarview_gfx
drm_kms_helper 32561 1 cedarview_gfx
rts_pstor 353252 0
drm 196391 6 cedarview_gfx,ttm,drm_kms_helper
cfg80211 178877 1 wl
lib80211 14040 2 lib80211_crypt_tkip,wl
mac_hid 13077 0
soundcore 14635 1 snd
snd_page_alloc 14108 2 snd_hda_intel,snd_pcm
i2c_algo_bit 13199 1 cedarview_gfx
lp 17455 0
parport 40930 3 parport_pc,ppdev,lp
wmi 18744 1 acer_wmi
video 19115 1 cedarview_gfx
r8169 56368 0 
```

$ iwconfig
```
lo no wireless extensions.

eth1 IEEE 802.11abg ESSID:"*** Name deleted ***"
Mode:Managed Frequency:2.437 GHz Access Point: 54:04:A6:CA:4E:0D
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

eth0 no wireless extensions.
```

$ cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

$ cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
```

Okay. Now this was while connected to the problematic network.

Their network worked fine a couple of times before last Friday, and I was the only one there at the time this morning. It seemed slow, but I'm not actually 100% sure it (or me) was malfunctioning. But here goes:

$ iwconfig
```
lo no wireless extensions.

eth1 IEEE 802.11abg ESSID:"*** name deleted ***"
Mode:Managed Frequency:2.412 GHz Access Point: 00:26:82:F5:AF:7C
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn

eth0 no wireless extensions.
```

~$ ifconfig -a
```
eth0 Link encap:Ethernet HWaddr 04:7d:7b:50:97:53
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:44 Base address:0xc000

eth1 Link encap:Ethernet HWaddr c0:18:85:0e:f5:ac
inet addr:192.168.0.74 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::c218:85ff:fe0e:f5ac/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1849 errors:0 dropped:0 overruns:0 frame:2356
TX packets:1485 errors:16 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2158947 (2.1 MB) TX bytes:197123 (197.1 KB)
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:522 errors:0 dropped:0 overruns:0 frame:0
TX packets:522 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:43838 (43.8 KB) TX bytes:43838 (43.8 KB)
```

~$ iwlist chan
```
lo no frequency information.

eth1 26 channels in total; available frequencies :
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
Channel 14 : 2.484 GHz
Channel 36 : 5.18 GHz
Channel 38 : 5.19 GHz
Channel 40 : 5.2 GHz
Channel 42 : 5.21 GHz
Channel 44 : 5.22 GHz
Channel 46 : 5.23 GHz
Channel 48 : 5.24 GHz
Channel 149 : 5.745 GHz
Channel 153 : 5.765 GHz
Channel 157 : 5.785 GHz
Channel 161 : 5.805 GHz
Channel 165 : 5.825 GHz
Current Frequency=2.412 GHz (Channel 1)

eth0 no frequency information.
```

~$ sudo iwlist scan
```
lo Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:26:82:F5:AF:7C
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=70/70 Signal level=-40 dBm
Encryption keyn
ESSID:"T.A.N."
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 0006542E412E4E2E
IE: Unknown: 010882848B962430486C
IE: Unknown: 030101
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001700000000000000000000000000000000000000
IE: Unknown: DD090010180225F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 02 - Address: AC:81:12:C4:A9:52
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=22/70 Signal level=-88 dBm
Encryption keyn
ESSID:"Web Waves"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 0009576562205761766573
IE: Unknown: 010882848B962430486C
IE: Unknown: 030101
IE: Unknown: 050400010000
IE: Unknown: 2A0102
IE: Unknown: 2F0102
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001700000000000000000000000000000000000000
IE: Unknown: DD090010180201F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 03 - Address: 00:20:A6:6E:78:B1
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=36/70 Signal level=-74 dBm
Encryption keyn
ESSID:"MRE-Wolfville"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s
Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 000D4D52452D576F6C6676696C6C65
IE: Unknown: 010882848B960C183048
IE: Unknown: 030101
IE: Unknown: 050400010000
IE: Unknown: 0706434120010B1B
IE: Unknown: 2A0102
IE: Unknown: 32041224606C
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD0900037F01010006FF7F
IE: Unknown: DD0C00037F020101000002A44000
Cell 04 - Address: 1C:AF:F7A:F93
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=20/70 Signal level=-90 dBm
Encryption keyn
ESSID:"Harvest"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 000748617276657374
IE: Unknown: 010882848B960C121824
IE: Unknown: 030102
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
IE: Unknown: 3D1602080800000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000004000
Cell 05 - Address: 20:10:7A:95:43:B5
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=25/70 Signal level=-85 dBm
Encryption keyn
ESSID:"MOTOROLA-C260C"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 000E4D4F544F524F4C412D4332363043
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606080000000000000000000000000000000000000000
IE: Unknown: DD090010180200F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 06 - Address: 00:26:82:C7:BA:7F
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=20/70 Signal level=-90 dBm
Encryption keyn
ESSID:"meow"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 00046D656F77
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606081500000000000000000000000000000000000000
IE: Unknown: DD090010180201F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 07 - Address: 00:22:3F:E5:CC8
Channel:7
Frequency:2.442 GHz (Channel 7)
Quality=21/70 Signal level=-89 dBm
Encryption keyn
ESSID:"TOW SECURE"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 88ms ago
IE: Unknown: 000A544F5720534543555245
IE: Unknown: 010882848B0C12961824
IE: Unknown: 030107
IE: Unknown: 050400010000
IE: Unknown: 0706555320010B1B
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: Unknown: DD0A0002BC0100223FE5CCD8

eth0 Interface doesn't support scanning.
```

~$ route -n
```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 0 0 0 eth1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth1
192.168.0.0 0.0.0.0 255.255.255.0 U 2 0 0 eth1
```

Hope that makes sense to semebody ....

---

### Post by praseodym on 2013-04-08
Same as here:

[http://ubuntuforums.org/showthread.php?t=2132515&p=12590901#post12590901](http://ubuntuforums.org/showthread.php?t=2132515&p=12590901#post12590901)

If your kernel is 3.5 that enough. If it is 3.2 you need to install the 3.6-backport-modules

---

### Post by Rob Sayer on 2013-04-09
Thanks for the response.

Kernel is 3.2.0-40-generic-pae.  I didn't think cedarview graphics worked with ubuntu (kubuntu actually) 12.10 so no kernel 3.5.

sudo apt-get install 3.6-backport-modules didn't find any package by that name.

On top of that, I just did a system update which updated the kernel to 3.2.0-40 and the screen brightness control no longer works!!!!  At least it still recognizes the refresh rate.  But that's another thread.  Maybe it overwrote a config file I had to modify before.  This just happened.

So do I do what your link suggests?  I don't know how to clean up the old config either.

Or should I just upgrade to 12.10?  Will the cedarview proprietary drivers still work?

---

### Post by Rob Sayer on 2013-04-09
I just tried more searching for 3.6-backport-module.

I'm led to something that strongly recommended I use apt or synaptic instead, but didn't name anything I could find on synaptic except for something described as an "empty package" for compatibility on kernel updates.  That doesn't sound useful.

Never had this much trouble with synaptic before, and I'm even more confused.

---

### Post by Rob Sayer on 2013-04-09
OK, I've calmed down slightly.  Losing my screen brightness control as well a couple of hours ago has me more discombobulated.

I found this and installed it: linux-backports-modules-cw-3.6-precise-generic.  Seemed like the right one.

The wireless worked on reboot, but I'm not hooked into the network I had problems with.  Hopefully it works.

---

### Post by Rob Sayer on 2013-04-10
I'm connected to the problematic network.  There's another guy here playing an online mmrpg game, and it's working for him.  Before I was knocking people pretty much clear off the wireless.

I'll give it another try or two and mark this solved.

Thanks for the responses.

---

