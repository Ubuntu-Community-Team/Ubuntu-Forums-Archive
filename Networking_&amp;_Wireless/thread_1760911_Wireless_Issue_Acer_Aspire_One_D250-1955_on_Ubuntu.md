---
title: "Wireless Issue: Acer Aspire One D250-1955 on Ubuntu Netbook Remix, partial wireless"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by metamyth on 2011-05-17
I've been searching around for a way to fix this, but I can't find anything, so I've decided to register and post.

The problem: I have an Acer Aspire D250-1955 that currently runs Ubuntu Netbook Remix 11.04 and Windows XP. Ever since this netbook had 9.x on it, though, I've had constant, flipflopping trouble with the wireless card when in Linux. Most of the time, it will start up fine, the wireless will work long enough for me to type something into the URL of Google Chrome, and then it will cease to be.

When it stops working, it announces that I am disconnected, but seems to be making efforts to reconnect. I let it sit once and all it did was constantly ask for a network password. I put in the proper password and wait, but to no avail; it asks me again some few minutes later. Every time I've updated the version of Linux, it does not change (though I do seem to remember the problem being more frequent when Unity debuted).

Every search I've done for a similar topic lands me with old questions that were about the wireless just not working; my works, but only half the time. Anyone have any pointers?

---

### Post by metamyth on 2011-05-31
UPDATE:

I have reinstalled Natty Narwhal to no effect. Driver updates did nothing. The most frustrating thing is that my other OS (XP Home 32 bit) still has wireless support with no fluctuation in having or not having wireless. I've decided to prod the thread to try and get some kind of advice here. Please help; I am a major noob when it comes to fixing things in Linux.

I will be editing this post momentarily, to post the codes that I have been told to post by [this thread.]("http://ubuntuforums.org/showthread.php?p=6183681")

EDIT:

1 ) Machine Brand and Model (PC/Laptop):
```
Acer Aspire One D250-1955
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
```

3 ) check interface:
```
wlan0     Link encap:Ethernet  HWaddr 0c:60:76:54:2e:d2  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe54:2ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31935494 (31.9 MB)  TX bytes:1338525 (1.3 MB)
```
```
wlan0     IEEE 802.11bg  ESSID:"Jamie and Troy's Awesome Wi-Fi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:01:4A:D6:42   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:6939   Missed beacon:0
```

4 ) Check for modules:
```
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
b43                   296610  0 
snd_seq_midi           13132  0 
i915                  450944  4 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
mac80211              257001  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  5 i915,drm_kms_helper
cfg80211              156212  2 b43,mac80211
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 
ssb                    45942  1 b43

```
5 ) Kernel boot messages
```
[   33.565678] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.471039] wlan0: authenticate with 00:16:01:4a:d6:42 (try 1)
[   96.475592] wlan0: authenticated
[   96.476446] wlan0: associate with 00:16:01:4a:d6:42 (try 1)
[   96.480879] wlan0: RX AssocResp from 00:16:01:4a:d6:42 (capab=0x431 status=0 aid=2)
[   96.480890] wlan0: associated
[   96.483467] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  106.872118] wlan0: no IPv6 routers present

```
6 ) Network configuration
```
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:97100000-97103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:50:6d:49
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:95000000-9503ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 0c:60:76:54:2e:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=478.104 ip=192.168.1.138 link=yes multicast=yes wireless=IEEE 802.11bg

```
7 ) Scan for networks:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:16:01:4A:D6:42
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"Jamie and Troy's Awesome Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002bf78fcb7cb
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 001E4A616D696520616E642054726F79277320417765736F6D652057692D4669
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```
8 ) Ubuntu Version: 
```
Description:	Ubuntu 11.04

```
9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
2.6.38-8-generic i686

```
10 ) Restarting the network:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

And of course, through all of this, my wireless worked perfectly.

---

### Post by metamyth on 2011-06-29
I'm still having issues with this. If there's not enough information, could someone please tell me? This question is turning more into me talking to myself.

More info: It is a Broadcom Wireless card, and I know that they have problems with Linux support, but I have found no other questions on the internet with similar symptoms as to what I have. I have reinstalled Ubuntu and the drivers for the Broadcom several times and the problem does not change. It has happened on multiple wireless connections, though I suspect it would be possible on all of them.

---

