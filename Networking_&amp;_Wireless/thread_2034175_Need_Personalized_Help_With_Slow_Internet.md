---
title: "Need Personalized Help With Slow Internet"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by Matt12334 on 2012-07-28
Hi, this is my first post, so hopefully I'm doing it correctly. I have had Ubuntu installed for a couple months, but I stopped using it because my internet speed is less than half of what I get in windows. 

I've tried (probably not successfully) to disable wireless N and change the IPV4 settings. So far, next to no luck.

I'm sure somebody here knows the necessary commands, tweaks, etc. that will get my computer from the current <10 Mbps to the usual 30 Mbps. Any help is appreciated.

Edit: I guess I should add what details I know. I'm running 12.04 64 bit on my acer aspire 5742, and I'm pretty clueless about my wireless components.

---

### Post by praseodym on 2012-07-28
Hi there,

please show the terminal (CTRL+ALT+T) outputs of the commands:
```

lspci -nnk
lsusb
lsmod
iwconfig
ifconfig -a
rfkill list
sudo iwlist scan
```

---

### Post by Matt12334 on 2012-07-28
> **praseodym said:**
> Hi there,

please show the terminal (CTRL+ALT+T) outputs of the commands:
```

lspci -nnk
lsusb
lsmod
iwconfig
ifconfig -a
rfkill list
sudo iwlist scan
```

Thanks for replying!  Let's see if I can do this right...

```

lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6603]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]

``````

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:c21c Suyin Corp. 

``````

lsmod
Module                  Size  Used by
ums_realtek            18248  0 
usb_storage            49198  1 ums_realtek
uas                    18180  0 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
arc4                   12529  2 
parport_pc             32866  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ppdev                  17113  0 
lp                     17799  0 
ath9k                 132390  0 
bnep                   18281  2 
rfcomm                 47604  0 
mac80211              506816  1 ath9k
snd_hwdep              13668  1 snd_hda_codec
bluetooth             180104  10 bnep,rfcomm
parport                46562  3 parport_pc,ppdev,lp
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
binfmt_misc            17540  1 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           14053  1 ath9k
i915                  472897  8 
ath9k_hw              411112  2 ath9k,ath9k_common
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
snd_timer              29990  2 snd_pcm,snd_seq
drm_kms_helper         46978  1 i915
videodev               98259  1 uvcvideo
drm                   242038  4 i915,drm_kms_helper
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
v4l2_compat_ioctl32    17128  1 videodev
mei                    41616  0 
cfg80211              205544  3 ath9k,mac80211,ath
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
psmouse                87692  0 
intel_ips              18089  0 
serio_raw              13211  0 
mxm_wmi                12979  0 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
wmi                    19256  2 mxm_wmi,acer_wmi
video                  19596  1 i915
mac_hid                13253  0 
tg3                   152032  0 

``````

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Virus"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:9D:4A:E9:C5   
          Bit Rate=130 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:90   Missed beacon:0

eth0      no wireless extensions.

``````

ifconfig -a
eth0      Link encap:Ethernet  HWaddr b8:70:f4:72:9d:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70111 (70.1 KB)  TX bytes:70111 (70.1 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:fe:27:6a  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:44e4:58a7:1234:1e65:9dff:fefe:276a/64 Scope:Global
          inet6 addr: fe80::1e65:9dff:fefe:276a/64 Scope:Link
          inet6 addr: 2002:44e4:58a7:1234:453c:b82a:e76d:85ea/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4008479 (4.0 MB)  TX bytes:649442 (649.4 KB)

``````

rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:9D:4A:E9:C5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Virus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025993ecd14
                    Extra: Last beacon: 796ms ago
                    IE: Unknown: 00055669727573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010000000199D4AE9C600000000000000001021000556495A494F10230006585752313030102400065857523130301042000F57474B4F4945414C333332313934351054000800060050F204000110110006585752313030100800020086103C000103104900140024E26002000101600000020001600100020001

eth0      Interface doesn't support scanning.

```I'll just assume that most of this makes some amount of sense to you. :D

---

### Post by Matt12334 on 2012-07-29
Now my connection speed has gone up to 28 Mbps, which is pretty close to what I get in Windows.  This has happened before, but it usually goes away once I reboot.  What might cause this?

---

### Post by virgodave61 on 2012-07-29
I had the same problem, now its faster than Windows, using terminal

sudo gedit /etc/pm/power.d/wireless

and add these lines, then save and reboot.

#!/bin/sh

/sbin/iwconfig wlan0 power off

That worked for me. Apparently new Power Management settings in Ubuntu that cause less power to be supplied to the wireless Internet device there by considerably slowing down the Internet speed in many wireless devices!

You can also try

sudo gedit  /etc/nsswitch.conf

and edit the line

files mdns4_minimal [NOTFOUND=return] dns mdns4

and change it to.

files dns

---

### Post by praseodym on 2012-07-29
Disable the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Router firmware is up-to-date? IMHO there is no WPA(1) with CCMP, check the router settings and change to WPA2-AES if possible.
> ```

wlan0     Scan completed :
          Cell 01 - Address: 00:19:9D:4A:E9:C5
...
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : [COLOR="Red"]CCMP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="Red"]CCMP[/COLOR]
                        Authentication Suites (1) : PSK
```

---

### Post by virgodave61 on 2012-07-29
I had the same problem and power management kept coming on everytime I rebooted then found the following forum and it worked.

_[http://ubuntuforums.org/showpost.php?p=11254836&postcount=12](http://ubuntuforums.org/showpost.php?p=11254836&postcount=12)_

---

### Post by Matt12334 on 2012-07-29
Thank you all for the replies!

> **virgodave61 said:**
> I had the same problem, now its faster than Windows, using terminal

sudo gedit /etc/pm/power.d/wireless

and add these lines, then save and reboot.

#!/bin/sh

/sbin/iwconfig wlan0 power off

That worked for me. Apparently new Power Management settings in Ubuntu that cause less power to be supplied to the wireless Internet device there by considerably slowing down the Internet speed in many wireless devices!

You can also try

sudo gedit  /etc/nsswitch.conf

and edit the line

files mdns4_minimal [NOTFOUND=return] dns mdns4

and change it to.

files dns

This seems to have had the most significant impact on my speeds, boosting me to around 16 Mbps while on battery.

> **praseodym said:**
> Disable the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```Router firmware is up-to-date? IMHO there is no WPA(1) with CCMP, check the router settings and change to WPA2-AES if possible.

I just checked the router settings, and it is on WPA1, not WPA2.  I intend to change it soon.  Will I still need to disable the hardware encryption if I do this?

> **virgodave61 said:**
> I had the same problem and power management kept coming on everytime I rebooted then found the following forum and it worked.

_[http://ubuntuforums.org/showpost.php?p=11254836&postcount=12](http://ubuntuforums.org/showpost.php?p=11254836&postcount=12)_

I had high hopes for this one, but it didn't do much, if anything.

---

### Post by Matt12334 on 2012-07-29
I just thought I'd share the little speedtest.net glitch that made my connection appear to skyrocket to ~138 Mbps for a split second.  My reaction was pretty funny...

---

