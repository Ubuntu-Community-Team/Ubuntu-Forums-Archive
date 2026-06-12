---
title: "Atheros ar9462 WIFI/BT not working correctly"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by tehwizardd on 2013-03-02
1. Bluetooth not working at all
2. WIFI working, but unstable. 

WIFI connection slows down and sometimes downloads stop totally.  When it's working, the speed is great. I have N standard WLAN and 100 Mbps link.

I bought USB BT adapter, working well. It is also atheros, but different model.

Should I just get USB wifi adapter and wait for kernel to support this?

---

### Post by tehwizardd on 2013-03-03
Anyone?

---

### Post by soulnet1 on 2013-03-07
FWIW, I'm having the exact same problem in 12.04. Read somewhere it would be fixed upgrading to 12.10, but I'm unable to upgrade either because of some held packages problem I'm still trying to figure out. I have an acer aspire s5 and everything else is working great.

---

### Post by soulnet1 on 2013-03-10
Update: After doing ppa-purge I was able to upgrade to 12.10 (although it took like 12 retries due to the wifi being disconnected while fetching) and now the wifi problem seems to be solved completely. Bluetooth is still not working though.

---

### Post by louis3d on 2013-04-02
I have the exact same problem, but solution proposed in [this thread]("http://ubuntuforums.org/showthread.php?t=2124592&highlight=atheros+AR9462") doesn't work. I will try upragding as well to 12.10.
```

*************** info trace ****************



**** uname -a ****


Linux louis-Aspire 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e052]
	Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0742]
	Kernel driver in use: tg3
--
04:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0742]
	Kernel driver in use: sdhci-pci


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 004: ID 064e:d251 Suyin Corp. 


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
usb_storage            49243  0 
usblp                  18307  0 
ath9k                 132428  0 
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205774  3 ath9k,mac80211,ath
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
joydev                 17693  0 
uvcvideo               72627  0 
btusb                  18332  2 
videodev               98259  1 uvcvideo
bluetooth             180153  23 rfcomm,bnep,btusb
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33719  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 acer_wmi
i915                  477626  3 
psmouse                97485  0 
drm_kms_helper         46978  1 i915
mac_hid                13253  0 
snd                    79041  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
tg3                   152085  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FreeWifi_secure: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    FREEBOX_SEBASTIEN_2W: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA
    FreeWifi_secure: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    FreeWifi:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39
    Livebox-17D0:    Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 63 WPA
    FreeWifi:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64


- Device: eth0  [Ethernet automatique] -----------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Livebox-17D0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000146b86e189
                    Extra: Last beacon: 4016ms ago
                    IE: Unknown: 000C4C697665626F782D31374430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FREEBOX_SEBASTIEN_2W"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9c80c0160
                    Extra: Last beacon: 4228ms ago
                    IE: Unknown: 001446524545424F585F53454241535449454E5F3257
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9c80a8160
                    Extra: Last beacon: 4296ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9c80a8160
                    Extra: Last beacon: 4264ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


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


**** dmesg ****


[    1.602988] tg3.c:v3.121 (November 2, 2011)
[    1.603047] tg3 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.603100] tg3 0000:04:00.0: setting latency timer to 64
[    1.638170] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address <MAC address removed>
[    1.638177] tg3 0000:04:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.638182] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.638186] tg3 0000:04:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[   14.793568] wmi: Mapper loaded
[   14.998390] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.998408] ath9k 0000:03:00.0: setting latency timer to 64
[   15.160172] ath: EEPROM regdomain: 0x6c
[   15.160175] ath: EEPROM indicates we should expect a direct regpair map
[   15.160180] ath: Country alpha2 being used: 00
[   15.160182] ath: Regpair used: 0x6c
[   15.203745] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.205133] Registered led device: ath9k-phy0
[   15.241096] acer_wmi: Acer Laptop ACPI-WMI Extras
[   15.241112] acer_wmi: Function bitmap for Communication Button: 0x801
[   15.241246] acer_wmi: Brightness must be controlled by generic video driver
[   15.281307] acer_wmi: Get 0x1 Device Status failed: 0xe2 - 0x0
[   15.283396] acer_wmi: Get 0x800 Device Status failed: 0xe2 - 0x0
[   15.284808] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[   15.871931] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[   15.880485] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[   16.946808] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.951938] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.962422] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[   16.962431] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[   16.962439] tg3 0000:04:00.0: irq 46 for MSI/MSI-X
[   26.106493] wlan0: authenticate with <MAC address removed> (try 1)
[   26.108695] wlan0: authenticated
[   26.109121] wlan0: associate with <MAC address removed> (try 1)
[   26.111986] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   26.111992] wlan0: associated
[   26.112646] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.814200] wlan0: no IPv6 routers present
[  434.337542] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  438.348268] wlan0: authenticate with <MAC address removed> (try 1)
[  438.350551] wlan0: authenticated
[  438.363216] wlan0: associate with <MAC address removed> (try 1)
[  438.366155] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  438.366161] wlan0: associated
[  448.957177] wlan0: no IPv6 routers present
[  640.870968] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  644.876555] wlan0: authenticate with <MAC address removed> (try 1)
[  644.878761] wlan0: authenticated
[  644.892088] wlan0: associate with <MAC address removed> (try 1)
[  644.895094] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  644.895101] wlan0: associated
[  655.774358] wlan0: no IPv6 routers present
[  798.240968] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  798.363754] ath9k 0000:03:00.0: PCI INT A disabled
[  798.363789] ath9k: Driver unloaded
[  817.198682] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  817.198810] ath9k 0000:03:00.0: setting latency timer to 64
[  817.209469] ath: EEPROM regdomain: 0x6c
[  817.209471] ath: EEPROM indicates we should expect a direct regpair map
[  817.209475] ath: Country alpha2 being used: 00
[  817.209477] ath: Regpair used: 0x6c
[  817.212070] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  817.212955] Registered led device: ath9k-phy0
[  817.265343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  817.269100] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  825.852032] wlan0: authenticate with <MAC address removed> (try 1)
[  825.855507] wlan0: authenticated
[  825.855855] wlan0: associate with <MAC address removed> (try 1)
[  825.861134] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  825.861140] wlan0: associated
[  825.861901] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  836.593838] wlan0: no IPv6 routers present
[ 5464.552791] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5468.550867] wlan0: authenticate with <MAC address removed> (try 1)
[ 5468.553190] wlan0: authenticated
[ 5468.566214] wlan0: associate with <MAC address removed> (try 1)
[ 5468.569111] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 5468.569117] wlan0: associated
[ 5478.967586] wlan0: no IPv6 routers present
[ 7082.704268] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7086.730860] wlan0: authenticate with <MAC address removed> (try 1)
[ 7086.733082] wlan0: authenticated
[ 7086.746016] wlan0: associate with <MAC address removed> (try 1)
[ 7086.748931] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 7086.748939] wlan0: associated
[ 7096.749547] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[ 7096.769512] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7100.667267] wlan0: authenticate with <MAC address removed> (try 1)
[ 7100.669613] wlan0: authenticated
[ 7100.682223] wlan0: associate with <MAC address removed> (try 1)
[ 7100.685190] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 7100.685196] wlan0: associated
[ 7111.063818] wlan0: no IPv6 routers present
[ 8323.674130] tg3 0000:04:00.0: PME# enabled
[ 8323.674148] tg3 0000:04:00.0: wake-up capability enabled by ACPI
[ 8323.981598] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8327.274388] ath9k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8327.274400] ath9k 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 8327.274543] tg3 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8327.274556] tg3 0000:04:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfffff800)
[ 8327.285540] tg3 0000:04:00.0: wake-up capability disabled by ACPI
[ 8327.285585] tg3 0000:04:00.0: PME# disabled
[ 8329.951187] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 8329.952650] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 8330.879263] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[ 8330.879280] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[ 8330.879292] tg3 0000:04:00.0: irq 46 for MSI/MSI-X
[ 8331.518858] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8333.873552] tg3 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 8333.873561] tg3 0000:04:00.0: eth0: Flow control is off for TX and off for RX
[ 8333.873567] tg3 0000:04:00.0: eth0: EEE is disabled
[ 8340.145202] wlan0: authenticate with <MAC address removed> (try 1)
[ 8340.147795] wlan0: authenticated
[ 8340.148126] wlan0: associate with <MAC address removed> (try 1)
[ 8340.154316] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 8340.154322] wlan0: associated
[ 8340.154958] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8343.667435] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8759.571035] tg3 0000:04:00.0: PME# enabled
[ 8759.571052] tg3 0000:04:00.0: wake-up capability enabled by ACPI
[ 8762.624536] ath9k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8762.624552] ath9k 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 8762.624701] tg3 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8762.624717] tg3 0000:04:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfffff800)
[ 8762.636143] tg3 0000:04:00.0: wake-up capability disabled by ACPI
[ 8762.636192] tg3 0000:04:00.0: PME# disabled
[ 8765.294735] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 8765.297250] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 8766.725843] tg3 0000:04:00.0: irq 44 for MSI/MSI-X
[ 8766.725860] tg3 0000:04:00.0: irq 45 for MSI/MSI-X
[ 8766.725873] tg3 0000:04:00.0: irq 46 for MSI/MSI-X
[ 8766.960899] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8768.735543] tg3 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 8768.735552] tg3 0000:04:00.0: eth0: Flow control is off for TX and off for RX
[ 8768.735557] tg3 0000:04:00.0: eth0: EEE is disabled
[ 8775.597988] wlan0: authenticate with <MAC address removed> (try 1)
[ 8775.600339] wlan0: authenticated
[ 8775.614427] wlan0: associate with <MAC address removed> (try 1)
[ 8775.617316] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 8775.617326] wlan0: associated
[ 8775.618313] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8786.248369] wlan0: no IPv6 routers present


**************** done ********************



```

---

