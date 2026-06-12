---
title: "rt2800usb or rt2870sta"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by Michael_BoG on 2011-09-15
Hi,

I'm running Ubuntu 11.04 and i'm wondering which driver i should use to get full n-speeds. I have tried the rt2800usb driver and that gives me 54Mbits. I have still to try to compile the rt2870sta driver with the [tutorial]("http://ubuntuforums.org/showthread.php?t=1476007")(not for the driver I have, but i guess it is the same if i swap out the names and driver versions) i found on here. I'm running kernel 3.0 (custom for gameservers). Or are there any other "tricks" to make it get full speed using the rt2800usb driver?

---

### Post by praseodym on 2011-09-15
Hi,

which device do you want to use? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

BTW: That link goes to rt2860sta, which is a driver for a PCI device.

---

### Post by Michael_BoG on 2011-09-15
Hi

I want to use a D-Link DWA-140 on it. The network is slowing down because that is the only non-N unit that's on it.

---

### Post by praseodym on 2011-09-15
Check the device ID with

```
lsusb

```
if it is **07d1:3c09** or **07d1:3c0a**

---

### Post by Michael_BoG on 2011-09-15
07d1:3c0a

---

### Post by praseodym on 2011-09-15
For this device you should use the rt2800usb, blacklist the other one. You need the newest firmware for that one, too. Install the package **linux-firmware**

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)

---

### Post by Michael_BoG on 2011-09-15
Hi. The problem isn't that I can't achieve internetconnectivity. The problem is the speed of the connection. I am using the rt2800usb driver because i'm on kernel 3.0.0.

---

### Post by praseodym on 2011-09-15
Post the terminal outputs of my first posting.

---

### Post by Michael_BoG on 2011-09-15
lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
        Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
        Kernel driver in use: r8169
03:06.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 86)
        Subsystem: D-Link System Inc DFE-530TX rev C [1186:1403]
        Kernel driver in use: via-rhine

```

lsusb
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:0015 Razer USA, Ltd
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 003 Device 003: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Bus 003 Device 002: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```

Module                  Size  Used by
aes_x86_64              7380  2
aes_generic            26170  1 aes_x86_64
loop                   15978  0
tda1004x               14287  1
saa7134_dvb            23980  0
videobuf_dvb            4442  1 saa7134_dvb
dvb_core               86603  1 videobuf_dvb
tda827x                 9178  2
tda8290                12959  1
tuner                  15969  1
ir_lirc_codec           3995  0
lirc_dev                8711  1 ir_lirc_codec
ir_sony_decoder         2059  0
ir_jvc_decoder          2153  0
adt7475                19902  0
hwmon_vid               2684  1 adt7475
ir_rc6_decoder          2697  0
ir_rc5_decoder          2185  0
arc4                    1282  2
ir_nec_decoder          2601  0
rt2800usb              11353  0
rt2800lib              37142  1 rt2800usb
crc_ccitt               1267  1 rt2800lib
saa7134               161231  1 saa7134_dvb
rc_core                14645  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,saa7134
rt2x00usb               9012  1 rt2800usb
rt2x00lib              32616  3 rt2800usb,rt2800lib,rt2x00usb
nouveau               686385  1
videobuf_dma_sg         7424  2 saa7134_dvb,saa7134
ttm                    52880  1 nouveau
mac80211              210423  3 rt2800lib,rt2x00usb,rt2x00lib
evdev                   9342  5
videobuf_core          15538  3 videobuf_dvb,saa7134,videobuf_dma_sg
joydev                  9709  0
drm_kms_helper         24450  1 nouveau
v4l2_common             5747  2 tuner,saa7134
usb_storage            43449  0
cfg80211              156894  2 rt2x00lib,mac80211
videodev               75880  3 tuner,saa7134,v4l2_common
rfkill                 15116  1 cfg80211
drm                   169550  3 nouveau,ttm,drm_kms_helper
v4l2_compat_ioctl32     7556  1 videodev
i2c_algo_bit            4904  1 nouveau
i2c_piix4               7872  0
tveeprom               13585  1 saa7134
serio_raw               4048  0
processor              17737  0
mxm_wmi                 1297  1 nouveau
edac_core              34246  0
i2c_core               18752  15 tda1004x,saa7134_dvb,tda827x,tda8290,tuner,adt7475,saa7134,nouveau,drm_kms_helper,v4l2_common,videodev,drm,i2c_algo_bit,i2c_piix4,tveeprom
pcspkr                  1723  0
video                  10531  1 nouveau
edac_mce_amd           13087  0
k10temp                 2723  0
parport_pc             20183  0
parport                28131  1 parport_pc
thermal_sys            13981  2 processor,video
wmi                     8242  1 mxm_wmi
button                  4143  1 nouveau
ext3                  124411  1
jbd                    40810  1 ext3
mbcache                 5378  1 ext3
usbhid                 34445  0
hid                    55122  1 usbhid
sg                     27070  0
sr_mod                 14728  0
cdrom                  35455  1 sr_mod
sd_mod                 35061  3
crc_t10dif              1236  1 sd_mod
ata_generic             3391  0
ohci_hcd               20410  0
via_rhine              22311  0
ehci_hcd               37589  0
r8169                  39700  0
mii                     3803  2 via_rhine,r8169
pata_atiixp             3729  0
ahci                   20513  2
libahci                18591  1 ahci
usbcore               131494  7 rt2800usb,rt2x00usb,usb_storage,usbhid,ohci_hcd,ehci_hcd
floppy                 55882  0
libata                169318  4 ata_generic,pata_atiixp,ahci,libahci
scsi_mod              144369  5 usb_storage,sg,sr_mod,sd_mod,libata

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Johansen_Nett"
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:AE:C5:B0:2D:1E
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9223  Invalid misc:41   Missed beacon:0

```

iwlist chan
```

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: BC:AE:C5:B0:2D:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm
                    Encryption key:on
                    ESSID:"Johansen_Nett"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000154a3e1f32
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 000D4A6F68616E73656E5F4E657474
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F0010000
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 02 - Address: 00:03:6F:96:9D:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm
                    Encryption key:on
                    ESSID:"anitahammer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001aecc160913
                    Extra: Last beacon: 1190ms ago
                    IE: Unknown: 000B616E69746168616D6D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4

```

Thanks alot for the help so far! :)

---

### Post by jawilljr on 2011-09-15
Also what is the output of:

```
lshw -C network
```

What I am looking for is this line:

```
configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-30-generic [color=red]firmware=0.29[/color] ip=192.168.1.118 multicast=yes wireless=IEEE 802.11abgn
```

Firmware version  29 is the latest version.

Below is my iwconfig:

```
wlan2     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:38:4F:32   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0
```

Jerry

---

### Post by praseodym on 2011-09-15
Shut off the power management and set the bit rate:

```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
```

---

### Post by Michael_BoG on 2011-09-15
```

configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-ub-100hz firmware=0.29 ip=192.168.1.200 link=yes multicast=yes wireless=IEEE 802.11bgn                                                                                                                                                         

```

The rate setting didn't do anything.

---

### Post by Michael_BoG on 2011-09-16
Does not having a file in /etc/Wireless cause the problem? I have not compiled the drivers my self, and I don't know how the file that maybe should be there should be configured. And what the name of it is.

---

### Post by praseodym on 2011-09-16
Take the file from the driver to compile and copy it to the right place. Create folders if needed

---

### Post by Michael_BoG on 2011-09-16
Hi. I don't know what I should rename the file to. Should it be the name of the chipset, name of the driver..?

---

### Post by praseodym on 2011-09-16
Oh, sorry, the rt2800usb doesnt use this file, only rt2870sta does. You can try the other one with the file

---

### Post by Michael_BoG on 2011-09-16
Hi. What other driver? The rt2870sta? And the dir structure should be: 
/etc
/etc/Wireless
/etc/Wireless/rt*
/etc/Wireless/rt*/rt*

?

---

### Post by praseodym on 2011-09-16
The structure should be (for rt2870sta):

**/etc/Wireless/RT2870STA.dat**
For Draft-N you should adjust some settings, see [here]("http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N") in the grey box. Adjust your country settings, ESSID, key, etc.

Alternatively you may try another driver:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wir-nicht-erkannt/3/#post-2388926](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wir-nicht-erkannt/3/#post-2388926)

---

### Post by Michael_BoG on 2011-09-16
Hi. Ok. I'll do a re-format of Ubuntu 11.04 and use the kernel that shipped with it. However, isn't kernel 3.0 actually 2.6.* something, just that they changed version numbers? If so, why did they add the rt2800usb drivers when the sta version worked just as well + it had draft-n included just by changing a file? 

Edit: Anyone know how far Kernel.org has gotten in their maintenance?

---

### Post by Michael_BoG on 2011-09-16
Just tried to add the file in its designated location, it didn't even register it. Using the 11.04 stock install now.

iwlist scan now reports 300mb/s in bit rate on my wlan. Howver iwconfig still reports 54mbits

---

### Post by praseodym on 2011-09-16
The number in iwconfig is most of the time not "real", check some downloads

---

### Post by Michael_BoG on 2011-09-16
Well, how come everyone else's say 100+ mbs?

---

### Post by jawilljr on 2011-09-16
> **Michael_BoG said:**
> Hi. Ok. I'll do a re-format of Ubuntu 11.04 and use the kernel that shipped with it. However, isn't kernel 3.0 actually 2.6.* something, just that they changed version numbers? If so, why did they add the rt2800usb drivers when the sta version worked just as well + it had draft-n included just by changing a file? 

Edit: Anyone know how far Kernel.org has gotten in their maintenance?

They took out the sta version because they have been deprecated. rt2800usb are the official drivers for ralink usb devices.

Another reason is because the devs want users to begin using them so they can hopefully fix bugs quicker. How can they find bugs when everybody is using the legacy staging drivers.

You can try and post your [question here](http://rt2x00.serialmonkey.com/mailman/listinfo/users_rt2x00.serialmonkey.com).

Maybe there is a bug with your particular chipset.

Jerry

---

### Post by Michael_BoG on 2011-09-16
Ok. Well, anyways, I have ran all the kernel upgrades and all those things, and still only 54Mbit reported in iwconfig. Any other way except downloads I can check the speed? Also, all the commands have changed. For example now it only shows in the configuration thing i was told to post: driver: usb.

Also, how would I update the kernel on the server (installed Ubuntu 11.04 server) using the Ubuntu kernel-ppa?

---

### Post by pdc on 2011-09-17
> Also, how would I update the kernel on the server

You want to update theirs, or your own?

If you want to update your own, how about this

[http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html](http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html)

the parent repository from that in the above post is 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

so you may want to choose a newer kernel than the 3.0.0- in this post

---

### Post by Michael_BoG on 2011-09-17
Think i explained myself wrong. The ubuntu installation is Server 11.04, i do not see a kernel version in that respository. Only generic, and all.

---

### Post by pdc on 2011-09-17
> Ubuntu Server is a server-oriented OS and as such it doesn’t use a GUI by default. 

[http://www.linuxnewstoday.org/linux-news-apr-2011-archives/1322-apr-21-2011-linux-news.shtml](http://www.linuxnewstoday.org/linux-news-apr-2011-archives/1322-apr-21-2011-linux-news.shtml)

enjoy

---

