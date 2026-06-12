---
title: "Broadcom BCM4313 keeps disconnecting"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by strelok_evil on 2013-04-29
Hello,

I have a problem with this wireless card. I had this problem on ubuntu 12.10 and 13.04. Every 5-10 minutes my internet connection hang for approximetly 1 minute. When I type sudo iwconfig i got something like "black screen of death" and my system resets. It's very annoying because I can't download larger files and also can't chat on skype.

---

### Post by varunendra on 2013-04-29
Please follow the "Wireless Script" link in my signature and post back the contents of "netinfo.txt" file it generates.

---

### Post by strelok_evil on 2013-04-29
Here are the file contents:

```

*************** info trace ****************



**** uname -a ****


Linux damian-Lenovo-B560 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


**** lspci ****


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Lenovo Device [17aa:3956]
    Kernel driver in use: atl1c
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: wl


**** lsusb ****


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 001 Device 004: ID 064e:f219 Suyin Corp. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. Digital Media Card Reader


**** iwconfig ****


eth1      IEEE 802.11abg  ESSID:"Pogodna 8a"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12617  1 
michael_mic            12540  4 
arc4                   12543  2 
bbswitch               13347  0 
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_realtek    63791  1 
coretemp               13131  0 
mxm_wmi                12893  0 
acer_wmi               27592  0 
ideapad_laptop         18018  0 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
snd_hda_intel          38307  3 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
lib80211_crypt_tkip    17160  0 
snd_hwdep              13272  1 snd_hda_codec
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
joydev                 17097  0 
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_core         39161  1 uvcvideo
wl                   2902185  0 
videodev               95806  2 uvcvideo,videobuf2_core
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
lib80211               14040  2 wl,lib80211_crypt_tkip
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  535507  3 
snd_rawmidi            25114  1 snd_seq_midi
video                  18894  2 i915,acer_wmi
mac_hid                13037  0 
drm_kms_helper         47545  1 i915
wmi                    18590  2 acer_wmi,mxm_wmi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm                   228750  4 i915,drm_kms_helper
mei                    36197  0 
intel_ips              17666  0 
i2c_algo_bit           13197  1 i915
lpc_ich                16925  0 
psmouse                81038  0 
microcode              18286  0 
cfg80211              436177  1 wl
serio_raw              13031  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ums_realtek            17669  0 
usb_storage            47684  2 ums_realtek
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
atl1c                  36175  0 
ahci                   25507  3 
libahci                26108  1 ahci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth1  [Pogodna 8a] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WiFi-Repeater:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Wisnia:          Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Dom 4:           Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Pogodna 9:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    Pogodna 9 2:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    SUPERRAFCIO:     Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 12 WEP
    *Pogodna 8a:     Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 73 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.1.1
    DNS:             88.199.125.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Pogodna 8a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000A506F676F646E61203861
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WiFi-Repeater"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000D576946692D5265706561746572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Pogodna 9 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000B506F676F646E6120392032
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020300
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Pogodna 9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009506F676F646E612039
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020100
          Cell 05 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Wisnia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00065769736E6961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706504C20010D14
                    IE: Unknown: 200100
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
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
          Cell 06 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SUPERRAFCIO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000B535550455252414643494F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD050050F20500
          Cell 07 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Dom 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0005446F6D2034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405051900000000000000000000000000000000000000
                    IE: Unknown: 3D1605051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD0E0050F204104A0001101044000102



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


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


[    0.269143] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.897896] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fceb9fd088cf158e29d83343e1c98bf8ab23d94a'
[   15.610070] wmi: Mapper loaded
[   15.665200] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.734583] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   15.814930] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   16.004632] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.033305] acer_wmi: Brightness must be controlled by acpi video driver
[  546.553593] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  546.553603] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  546.553613] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  546.553617] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  546.553626] ERROR @wl_dev_intvar_get : error (-1)
[  546.553630] ERROR @wl_cfg80211_get_tx_power : error (-1)


**************** done ********************


```

---

### Post by varunendra on 2013-04-29
Are your gateway and DNS server two different machines? (192.168.0.1 and 192.168.1.1)

I am looking up the error messages in your dmesg outputs, seem to be the culprits. Meanwhile, please post the outputs of -
```
ping -c4 192.168.1.1
ping -c4 192.168.0.1
ping -c4 88.199.125.1
modinfo wl
```

---

### Post by strelok_evil on 2013-04-29
> **varunendra said:**
> Are your gateway and DNS server two different machines? (192.168.0.1 and 192.168.1.1)

Yes, my ISP gave me a TP-Link router and a nanostation loco m5. On Windows it works perfectly fine. On Ubuntu 12.04 also.


ping -c4 192.168.1.1
```
damian@damian-Lenovo-B560:~$ ping -c4 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=63 time=1.29 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=63 time=1.27 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=63 time=1.25 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=63 time=1.28 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.257/1.278/1.298/0.015 ms


```


ping -c4 192.168.0.1
```
damian@damian-Lenovo-B560:~$ ping -c4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms


```


ping -c4 88.199.125.1
```
damian@damian-Lenovo-B560:~$ ping -c4 88.199.125.1
PING 88.199.125.1 (88.199.125.1) 56(84) bytes of data.
64 bytes from 88.199.125.1: icmp_req=1 ttl=62 time=4.18 ms
64 bytes from 88.199.125.1: icmp_req=2 ttl=62 time=4.00 ms
64 bytes from 88.199.125.1: icmp_req=3 ttl=62 time=6.09 ms
64 bytes from 88.199.125.1: icmp_req=4 ttl=62 time=6.90 ms

--- 88.199.125.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 4.002/5.296/6.906/1.237 ms


```

modinfo wl
```
damian@damian-Lenovo-B560:~$ modinfo wl
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


```

---

### Post by varunendra on 2013-04-29
[SIZE=4][SIZE=3][COLOR="#FF0000"]**EDIT 1 : Attention users with Kernel versions 3.4-rc1~54 and later** (Ubuntu 12.10 and later) :[/SIZE][/SIZE]
Please see **post #31** in this thread : [http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619)
....for a possible solution (still under test, although the version build there has been reported to be working better).

The methods discussed here may fail to build the older version of wl driver due to some changes in newer kernels.[/COLOR]

> **strelok_evil said:**
> ping -c4 192.168.0.1
```
damian@damian-Lenovo-B560:~$ ping -c4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

```

Being unable to ping the gateway seems a bit odd to me, although it is quite possible that an inbuilt firewall may be blocking it, which is not abnormal.

The thing I'm more concerned about is this bug : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1114281)

Accordingly, please try installing an older version of bcmwl-kernel-source, completely purging the current one. To check which versions are available :
```
apt-cache show bcmwl-kernel-source | grep -i version
```
Output will be something like -
> Version: 6.20.155.1+bdcom-0ubuntu0.0.1
Version: 5.100.82.38+bdcom-0ubuntu6
By default, the newer version would have been installed. You can check it with '**dpkg -s bcmwl-kernel-source | grep -i version**' command. We have to remove it and install the older one (*5.100.82.38+bdcom-0ubuntu6* in above example).

[COLOR="#800000"]**[EDIT 2 :**[s]If you don't see an older version available in the above output, please take a look at post #8 below. Although I haven't tested it myself yet on 12.10 or later, so suggestions & corrections, if any, are most welcome. Thanks![/s]
Forget it. It seems that the method discussed here will only work for 12.04. Follow the link in **EDIT 1** above if you don't see an older version by default.**]**[/COLOR]

While being connected via cable, remove the current (newer) one and install the older version (noted as per previous command above) -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source=*5.100.82.38+bdcom-0ubuntu6*
```
Please change the version (the number after the equal sign) as per what is available on your system.

Once finished, recheck the installed version with:
```
dpkg -s bcmwl-kernel-source | grep -i version
```
It should return the older version now. Reboot and see if situation improves. Post back the results.

---

### Post by strelok_evil on 2013-04-30
It seems I don't have any other version in my software repositories. 
```
damian@damian-Lenovo-B560:~$ apt-cache show bcmwl-kernel-source | grep -i version
Version: 6.20.155.1+bdcom-0ubuntu6
damian@damian-Lenovo-B560:~$
```

But I tried to purge this package and reinstall it, hope it may make any differenece. Sometimes silly things just helps. I'll edit this post and tell if it helps or not.

---

### Post by varunendra on 2013-04-30
> **strelok_evil said:**
> It seems I don't have any other version in my software repositories..

**EDIT :** Please discard. See this post : [http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619)
[s]Hmm.. I should have anticipated this. Maybe the older version that I gave example of is only available in Precise repositories. You may try adding this repository to your software sources :
```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu precise main universe restricted"
```
then -
```
sudo apt-get update
```
then recheck -
```
apt-cache show bcmwl-kernel-source | grep -i version
```
If the older version appears now, proceed as mentioned in my previous post.[/s]

---

### Post by strelok_evil on 2013-05-03
It works! Thank you very much. (:

---

### Post by varunendra on 2013-05-03
> **strelok_evil said:**
> It works! Thank you very much. (:

Wow! That makes at least two happy clients so far :)

Test the connection stability to your satisfaction, then if satisfactory, please consider marking the thread as [SOLVED] (follow the 'see how' link in my signature to see how).

---

### Post by strelok_evil on 2013-05-03
I can't mark thread as solved (I don't have a prefix listbox) same issue as in the link in your signature

[ATTACH=CONFIG]242138[/ATTACH]

---

### Post by varunendra on 2013-05-03
> **strelok_evil said:**
> I can't mark thread as solved (I don't have a prefix listbox) same issue as in the link in your signature

[ATTACH=CONFIG]242138[/ATTACH]

Hmm.. looks like something has changed again. Issue under discussion here at the right place : [http://ubuntuforums.org/showthread.php?t=2141000](http://ubuntuforums.org/showthread.php?t=2141000)

I had to request the mods twice to mark [this one]("http://ubuntuforums.org/showthread.php?t=2140063&p=12629078#post12629078") as [Solved] as the OP had same problem as you. Going to do the same here too..

---

### Post by Hadaka on 2013-05-03
Here ya go..
[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads

YOUR prefix box currently says Ubuntu
[/URL]

---

### Post by Old_Grey_Wolf on 2013-05-03
I marked thread as solved.

---

### Post by jcobban on 2013-05-03
I do not consider any suggestion that requires that I modify vendor code to be a solution.  This proposal scares me silly.  I do not think that the problem should be markes SOLVED until there is a resolution that mere mortals can use.

---

### Post by Old_Grey_Wolf on 2013-05-03
> **jcobban said:**
> I do not consider any suggestion that requires that I modify vendor code to be a solution.  This proposal scares me silly.  I do not think that the problem should be markes SOLVED until there is a resolution that mere mortals can use.

The original poster considered their problem solved. 

Some people are having difficulty marking threads they started as SOLVED; therefore, I did it for them. 

If you are having a similar problem and don't like the solution offered in this thread then you should start your own thread describing your problem.

---

### Post by varunendra on 2013-05-04
Not to argue, but just to clarify why the change is safe and officially recommended -
> **jcobban said:**
> I do not consider any suggestion that requires that I modify vendor code to be a solution. This proposal scares me silly.
If the change or modification is undisclosed or suspicious, then you are right, one should try it only if they fully understand what they are doing.

However, if you follow the second link in the very first sentence of the linked post (the suggestion), you will reach this page : [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0195c002)

If you are using Linux and 'trust' it, then I hope you may know who Linus Torvalds is or at least a rough idea of what 'Open Source' means or how it works. The above page is a [git hub]("http://en.wikipedia.org/wiki/Git_(software)") for the changes in the kernel itself. Although most of the language on the above page may be cryptic for non-geeks, it is mentioned in the very initial paragraphs, before the real cryptic part -
> Delete all instances of asm/system.h
  Remove all #inclusions of asm/system.h
  Add #includes needed to permit the removal of asm/system.h

Those who really care may go further down, and will find infinite instances of -
> [COLOR="#FF0000"]-#include <asm/system.h>[/COLOR]
Compared with the other lines around these instances, it does not need us to be programmers ourselves to decipher the meaning of the 'minus' (-) sign before the term.

I have only recommended what has already been done at the very core of the OS you are using. And have posted it as a series of openly viewable commands that can be viewed and objected, if objectionable, by those who understand the effects. That's how open source works in general.

In fact the newer versions of the driver already contain similar fix that we are doing here manually.

What would have been really scary is that if I would have uploaded the whole procedure as a single script, using which would have been as easy as running ./autorun.sh for 'mere mortals'. Because then the chances of the included code being watched by those-who-can-understand would have been really thin, and the script might contain some harmful code, included intentionally or unintentionally.

> I do not think that the problem should be markes SOLVED until there is a resolution that mere mortals can use.
For those who find such solutions too difficult to implement, despite the quality of help we offer here, the simpler solution is to stick with LTS releases (which currently is 12.04) or wait until a patched driver is released in the forthcoming updates (which only happens when someone like us reports issues in correct places like bugzilla or launchpad, and then it takes time).

Hope it helps clearing some doubts regarding the fix, and I am glad you raised the question. :)

---

