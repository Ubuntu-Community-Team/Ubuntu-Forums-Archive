---
title: "Wireless Issues"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by Frankaz on 2013-05-04
So... I'm still having problems with wireless on Kubuntu 13.04 (note worked fine on 12.10). It simply won't connect... It says configuring interface for a few moments and then gives up.
The following is the output of varunendra's wireless script:
```

*************** info trace ****************



**** uname -a ****


Linux GA-890XA-UD3 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


**** lspci ****


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


**** lsusb ****


Bus 002 Device 003: ID 0c45:6270 Microdia PC Camera (SN9C201 + MI0360/MT9V011 or MI0360SOC/MT9V111) U-CAM PC Camera NE878, Whitcom WHC017, ...
**Bus 003 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]**
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 007 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  16 
arc4                   12615  2 
joydev                 17377  0 
hid_logitech           26585  0 
ff_memless             13013  1 hid_logitech
rt2800usb              26854  0 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
usbhid                 47074  1 hid_logitech
hid                   101002  2 hid_logitech,usbhid
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
gspca_sn9c20x          35233  0 
gspca_main             28365  1 gspca_sn9c20x
videodev              129260  2 gspca_sn9c20x,gspca_main
kvm_amd                59717  0 
snd_hda_codec_hdmi     36913  1 
kvm                   443165  1 kvm_amd
snd_usb_audio         140685  1 
microcode              22881  0 
snd_usbmidi_lib        24938  1 snd_usb_audio
serio_raw              13215  0 
btusb                  22474  0 
bluetooth             228619  22 bnep,btusb,rfcomm
snd_hda_codec_realtek    78399  1 
edac_core              62003  0 
k10temp                13126  0 
edac_mce_amd           23114  0 
snd_hda_intel          39619  2 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
sp5100_tco             13735  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              13266  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
fglrx                5201161  99 
snd                    68876  18 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
amd_iommu_v2           19068  1 fglrx
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
vesafb                 13828  1 
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13242  0 
wmi                    19070  0 
pata_acpi              13038  0 
r8169                  67446  0 
pata_jmicron           12758  0 
ahci                   25731  3 
libahci                31364  1 ahci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SKY17122:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    RANDOM:          Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100




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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKY17122"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018e8d65183
                    Extra: Last beacon: 1384ms ago
                    IE: Unknown: 0008534B593137313232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"RANDOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002a7236186
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000652414E444F4D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



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


[    2.154064] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4fb521df0b0fa81f775431361b8076d5d0f1869a'
[    2.202414] wmi: Mapper loaded
[    5.584183] usbcore: registered new interface driver rt2800usb
[    9.307883] type=1400 audit(1367670274.646:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1219 comm="apparmor_parser"
[    9.308739] type=1400 audit(1367670274.646:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1219 comm="apparmor_parser"
[    9.682624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.682920] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.171656] wlan0: authenticate with <MAC address removed>
[   39.234514] wlan0: direct probe to <MAC address removed> (try 1/3)
[   39.434726] wlan0: direct probe to <MAC address removed> (try 2/3)
[   39.638685] wlan0: direct probe to <MAC address removed> (try 3/3)
[   39.842672] wlan0: authentication with <MAC address removed> timed out
[   54.097610] wlan0: authenticate with <MAC address removed>
[   54.158488] wlan0: direct probe to <MAC address removed> (try 1/3)
[   54.360685] wlan0: direct probe to <MAC address removed> (try 2/3)
[   54.564688] wlan0: direct probe to <MAC address removed> (try 3/3)
[   54.768660] wlan0: authentication with <MAC address removed> timed out
[   56.273330] wlan0: authenticate with <MAC address removed>
[   56.334286] wlan0: direct probe to <MAC address removed> (try 1/3)
[   56.536389] wlan0: direct probe to <MAC address removed> (try 2/3)
[   56.740346] wlan0: direct probe to <MAC address removed> (try 3/3)
[   56.944330] wlan0: authentication with <MAC address removed> timed out


**************** done ********************



```

---

### Post by praseodym on 2013-05-04
Deactivate the PM:
```

sudo iwconfig wlan0 power off
```
and try pure WPA2-AES (CCMP) encryption

---

### Post by Frankaz on 2013-05-04
Already tried the power mangement solution, no effect. don't think my router does that kind of encryption, currently got WPA2-PSK[AES].

Other options are WPA Auto, WPA2 Enterprise or Disabled.

Just to test have loaded Kubuntu 12.10 CD and I am now curretly connected to the network via wireless...

script results for 12.10 cd:

```


*************** info trace ****************



**** uname -a ****


Linux kubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard [1458:e000]
	Kernel driver in use: r8169


**** lsusb ****


Bus 002 Device 003: ID 0c45:6270 Microdia PC Camera (SN9C201 + MI0360/MT9V011 or MI0360SOC/MT9V111) U-CAM PC Camera NE878, Whitcom WHC017, ...
**Bus 003 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]**
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 007 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"RANDOM"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC address removed>   
          Bit Rate=14.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:224  Invalid misc:62   Missed beacon:0



**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
dm_crypt               23011  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  5 
arc4                   12529  2 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         130279  1 
snd_hwdep              13602  2 snd_hda_codec,snd_usb_audio
rt2800usb              22661  0 
snd_usbmidi_lib        24953  1 snd_usb_audio
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
rt2800lib              58685  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
snd_seq_midi           13324  0 
rt2x00usb              20618  1 rt2800usb
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi
rt2x00lib              54891  3 rt2800usb,rt2800lib,rt2x00usb
gspca_sn9c20x          35233  0 
parport_pc             32688  0 
gspca_main             28322  1 gspca_sn9c20x
snd_seq_midi_event     14899  1 snd_seq_midi
videodev              120309  2 gspca_sn9c20x,gspca_main
ppdev                  17073  0 
dm_multipath           22828  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
lp                     17759  0 
mac80211              539908  3 rt2800lib,rt2x00usb,rt2x00lib
joydev                 17457  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13215  0 
kvm_amd                55604  0 
kvm                   414070  1 kvm_amd
cfg80211              206566  2 rt2x00lib,mac80211
k10temp                13126  0 
btusb                  18334  0 
snd                    78734  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13697  0 
mac_hid                13205  0 
bnep                   18140  2 
rfcomm                 46619  16 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
parport                46345  3 parport_pc,ppdev,lp
microcode              22803  0 
scsi_dh                14554  1 dm_multipath
i2c_piix4              13167  0 
bluetooth             209199  22 btusb,bnep,rfcomm
edac_core              52451  0 
edac_mce_amd           23303  0 
squashfs               36522  1 
overlayfs              28007  1 
nls_utf8               12557  1 
isofs                  39842  1 
dm_raid45              76812  0 
xor                    17152  1 dm_raid45
dm_mirror              22028  0 
dm_region_hash         20806  1 dm_mirror
dm_log                 18529  3 dm_raid45,dm_mirror,dm_region_hash
hid_logitech           26585  0 
ff_memless             13013  1 hid_logitech
usbhid                 46947  1 hid_logitech
hid                   100366  2 hid_logitech,usbhid
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
radeon                895653  2 
pata_atiixp            13204  1 
r8169                  61650  0 
ttm                    83595  1 radeon
wmi                    19070  0 
drm_kms_helper         46784  1 radeon
pata_jmicron           12747  0 
drm                   275528  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [RANDOM] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           104 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKY17122:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    *RANDOM:         Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 55 WPA2

  IPv4 Settings:
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"RANDOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000007be85186
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 000652414E444F4D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKY17122"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a07f70183
                    Extra: Last beacon: 1816ms ago
                    IE: Unknown: 0008534B593137313232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



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


[    4.545457] wmi: Mapper loaded
[   78.777733] device-mapper: multipath: version 1.4.0 loaded
[   84.951627] Registered led device: rt2800usb-phy0::radio
[   84.951643] Registered led device: rt2800usb-phy0::assoc
[   84.951657] Registered led device: rt2800usb-phy0::quality
[   84.951689] usbcore: registered new interface driver rt2800usb
[   99.268201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.269182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  306.320778] wlan0: authenticate with <MAC address removed>
[  306.381057] wlan0: send auth to <MAC address removed> (try 1/3)
[  306.382808] wlan0: authenticated
[  306.419380] wlan0: associate with <MAC address removed> (try 1/3)
[  306.422429] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  306.430460] wlan0: associated
[  306.432909] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************

```

---

### Post by praseodym on 2013-05-04
This is the right encryption mode. Obviously, the driver rt2800usb works better in 12.10.

---

### Post by meldroc on 2013-05-04
I also have an Asus USB-N13. It does not work with the kernel provided with 13.04. I'm working around this problem by booting an older 3.5 kernel from 12.10.

---

### Post by Frankaz on 2013-05-04
> **meldroc said:**
> I also have an Asus USB-N13. It does not work with the kernel provided with 13.04. I'm working around this problem by booting an older 3.5 kernel from 12.10.

How do you go about doing that? Would at least be a temp fix until the driver or kernel issue is fixed...

---

### Post by Frankaz on 2013-05-06
Solved. Downloaded this 3.5 kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.1-quantal/)

and then removed the latest one so would always boot. Thanks meldroc!

---

### Post by meldroc on 2013-05-07
Any new news on fixes for this bug? I just saw an updated kernel today when I did my apt updates, but the new one doesn't work either. I'm still stuck on 3.5 until this bug is fixed.

---

