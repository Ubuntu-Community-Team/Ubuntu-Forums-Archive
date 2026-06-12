---
title: "wireless lost suddenly"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by holier on 2013-03-05
hello, i'm newbie
i have hp 620 with ubuntu 12.10 quantal quetzal
my wireless is gone! 
my rtl8192se module is loaded fine, but no wireless
please help

---

### Post by holier on 2013-03-05
uname -a:
```
Linux smail-HP-620 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 05:32:22 UTC 2013 i686 i686 i686 GNU/Linux
```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
85:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

lsusb:
```
Bus 001 Device 002: ID 04f2:b1ac Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

iwconfig:
```
wlan2     IEEE 802.11bgn  ESSID:"HG520"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:63:29:68:45   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:2169   Missed beacon:0



lo        no wireless extensions.

eth0      no wireless extensions
```

rfkill:
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lsmod:
```
Module                  Size  Used by
arc4                   12474  0 
ath9k_htc              85559  0 
ath9k_common           13784  1 ath9k_htc
ath9k_hw              376228  2 ath9k_htc,ath9k_common
ath                    19188  3 ath9k_htc,ath9k_common,ath9k_hw
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
joydev                 17162  0 
coretemp               13169  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
microcode              18210  0 
bnep                   17708  2 
lpc_ich                16926  0 
psmouse                84878  0 
serio_raw              13032  0 
rfcomm                 37277  0 
snd_hda_intel          32516  3 
parport_pc             31969  0 
bluetooth             183270  10 bnep,rfcomm
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
ppdev                  12818  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           192684  0 
binfmt_misc            17261  1 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
wmi                    18591  1 hp_wmi
i915                  457241  4 
drm_kms_helper         47304  1 i915
mac_hid                13038  0 
drm                   238811  5 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
mac80211              461261  1 ath9k_htc
cfg80211              175574  3 ath9k_htc,ath,mac80211
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 
```

iwlist:
```
wlan2     Scan completed :
          Cell 01 - Address: 00:21:63:29:68:45
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HG520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000287d3b824c
                    Extra: Last beacon: 9660ms ago
                    IE: Unknown: 00054847353230
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning
```

---

### Post by varunendra on 2013-03-05
> **holier said:**
> my **rtl8192se module is loaded fine**, but no wireless
..I can't see that module in your lsmod output -
> **holier said:**
> 
lsmod:
```
Module                  Size  Used by
arc4                   12474  0 
ath9k_htc              85559  0 
ath9k_common           13784  1 ath9k_htc
ath9k_hw              376228  2 ath9k_htc,ath9k_common
ath                    19188  3 ath9k_htc,ath9k_common,ath9k_hw
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
joydev                 17162  0 
coretemp               13169  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
microcode              18210  0 
bnep                   17708  2 
lpc_ich                16926  0 
psmouse                84878  0 
serio_raw              13032  0 
rfcomm                 37277  0 
snd_hda_intel          32516  3 
parport_pc             31969  0 
bluetooth             183270  10 bnep,rfcomm
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
ppdev                  12818  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
**[COLOR="#FF0000"]ndiswrapper           192684  0 [/COLOR]**
binfmt_misc            17261  1 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
wmi                    18591  1 hp_wmi
i915                  457241  4 
drm_kms_helper         47304  1 i915
mac_hid                13038  0 
drm                   238811  5 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
mac80211              461261  1 ath9k_htc
cfg80211              175574  3 ath9k_htc,ath,mac80211
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 
```
..on the other hand, I do see ndiswrapper in it as highlighted in red.

Please explain in detail what was the original problem you were having and what all you have tried so far.

Also, post the outputs of -
```
lspci -nnk | grep -iA2 net
cat /etc/modprobe.d/blacklist.conf | tail
```

---

### Post by holier on 2013-03-05
thanx varunendra 
my problem is that i can't find any wifi network in network manager and my wifi button stays orange (off)

```
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel modules: rtl8192se
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: r8169
```


```
cat /etc/modprobe.d/blacklist.conf | tail
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
blacklist uvcvideo
blacklist brcmsmac
blacklist bcma
```

---

### Post by varunendra on 2013-03-06
Hmm... You didn't say what all have you tried so far. By your outputs it seems to me that you may have a long story to tell me. :)

For example the earlier output showed no rtl8192se module while the current one does. Earlier one had ndiswrapper in it which means you tried it.

The blacklisting of broadcom drivers indicates you also fiddled with broadcom drivers, while your system doesn't have any bcm cards.

Although not related, I also don't understand why you needed to blacklist the uvcvideo driver. It's just a poor innocent driver used by webcams :)

So please tell me in detail what all have you tried so far. If you followed any guides, a link to them would also help a lot.

As of now, I need a detailed diagnostic report of your wireless setup. To create and post that, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the contents of "netinfo.txt" file as mentioned there.

**PS:**
Please use 'Code' tags while posting outputs. It preserves its formatting and makes it more readable. Follow the "Code Tags example" link in my signature to see how to do it.

---

### Post by holier on 2013-03-06
hey varun,
 sorry for the post. i'm 1st degree newbie:)

code:
```


*************** info trace ****************



**** uname -a ****


Linux smail-HP-620 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 05:32:22 UTC 2013 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel modules: rtl8192se
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 002: ID 04f2:b1ac Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan2     IEEE 802.11bgn  ESSID:"HG520"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:37  Invalid misc:6420   Missed beacon:0



**** rfkill ****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
arc4                   12474  2 
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
joydev                 17162  0 
coretemp               13169  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
bnep                   17708  2 
parport_pc             31969  0 
ppdev                  12818  0 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
binfmt_misc            17261  1 
microcode              18210  0 
ath9k_htc              85559  0 
ath9k_common           13784  1 ath9k_htc
ath9k_hw              376228  2 ath9k_htc,ath9k_common
ath                    19188  3 ath9k_htc,ath9k_common,ath9k_hw
psmouse                84878  0 
serio_raw              13032  0 
lpc_ich                16926  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18591  1 hp_wmi
mac_hid                13038  0 
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457241  4 
ndiswrapper           192684  0 
drm_kms_helper         47304  1 i915
drm                   238811  5 i915,drm_kms_helper
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
mac80211              461261  1 ath9k_htc
cfg80211              175574  3 ath9k_htc,ath,mac80211
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan2  [HG520 2] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *HG520:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP

  IPv4 Settings:
    Address:         192.168.1.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


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


auto lo
iface lo inet loopback



**** iwlist ****


wlan2     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HG520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013566428fc
                    Extra: Last beacon: 63120ms ago
                    IE: Unknown: 00054847353230
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C



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
blacklist uvcvideo
blacklist brcmsmac
blacklist bcma


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard HP 620/1526, BIOS 68PVI Ver. F.00 02/25/2010
[   29.801494] iwlwifi: `1' invalid for parameter `11_ndisable'
[   29.853365] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   29.902765] wmi: Mapper loaded
[   30.066643] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMCreateLog'
[   30.066815] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net8192se'
[   30.067364] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net8192se'
[   30.085914] usbcore: registered new interface driver ndiswrapper
[   30.109879] usb 2-6: ath9k_htc: Firmware htc_9271.fw requested
[   30.109962] usbcore: registered new interface driver ath9k_htc
[   30.962709] usb 2-6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   31.197587] ath9k_htc 2-6:1.0: ath9k_htc: HTC initialized with 33 credits
[   31.386080] ath9k_htc 2-6:1.0: ath9k_htc: FW Version: 1.3
[   31.386085] ath: EEPROM regdomain: 0x809c
[   31.386086] ath: EEPROM indicates we should expect a country code
[   31.386088] ath: doing EEPROM country->regdmn map search
[   31.386089] ath: country maps to regdmn code: 0x52
[   31.386091] ath: Country alpha2 being used: CN
[   31.386092] ath: Regpair used: 0x52
[   31.396043] Registered led device: ath9k_htc-phy0
[   31.562396] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   31.562719] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   39.068629] wlan2: authenticate with <MAC address removed>
[   39.161392] wlan2: direct probe to <MAC address removed> (try 1/3)
[   39.364029] wlan2: direct probe to <MAC address removed> (try 2/3)
[   39.531469] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   39.879273] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   40.243204] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   40.553422] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   42.777202] wlan2: authenticate with <MAC address removed>
[   42.824142] wlan2: direct probe to <MAC address removed> (try 1/3)
[   43.028032] wlan2: direct probe to <MAC address removed> (try 2/3)
[   43.232030] wlan2: direct probe to <MAC address removed> (try 3/3)
[   43.436031] wlan2: authentication with <MAC address removed> timed out
[   44.508514] wlan2: authenticate with <MAC address removed>
[   44.598509] wlan2: direct probe to <MAC address removed> (try 1/3)
[   44.800033] wlan2: direct probe to <MAC address removed> (try 2/3)
[   45.004041] wlan2: direct probe to <MAC address removed> (try 3/3)
[   45.208032] wlan2: authentication with <MAC address removed> timed out
[   52.240480] wlan2: authenticate with <MAC address removed>
[   52.330133] wlan2: direct probe to <MAC address removed> (try 1/3)
[   52.532031] wlan2: direct probe to <MAC address removed> (try 2/3)
[   52.736030] wlan2: direct probe to <MAC address removed> (try 3/3)
[   52.940026] wlan2: authentication with <MAC address removed> timed out
[   54.008477] wlan2: authenticate with <MAC address removed>
[   54.098758] wlan2: direct probe to <MAC address removed> (try 1/3)
[   54.300025] wlan2: direct probe to <MAC address removed> (try 2/3)
[   54.504023] wlan2: direct probe to <MAC address removed> (try 3/3)
[   54.708021] wlan2: authentication with <MAC address removed> timed out
[   79.712505] wlan2: authenticate with <MAC address removed>
[   79.810144] wlan2: direct probe to <MAC address removed> (try 1/3)
[   80.012034] wlan2: direct probe to <MAC address removed> (try 2/3)
[   80.216035] wlan2: direct probe to <MAC address removed> (try 3/3)
[   80.420022] wlan2: authentication with <MAC address removed> timed out
[   87.004445] wlan2: authenticate with <MAC address removed>
[   87.096889] wlan2: direct probe to <MAC address removed> (try 1/3)
[   87.339206] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   87.420563] wlan2: authenticate with <MAC address removed>
[   87.472765] wlan2: direct probe to <MAC address removed> (try 1/3)
[   87.707921] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   88.181583] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   88.477027] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   89.194418] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   89.272447] wlan2: authenticate with <MAC address removed>
[   89.319137] wlan2: direct probe to <MAC address removed> (try 1/3)
[  100.148338] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  100.642004] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  100.720479] wlan2: authenticate with <MAC address removed>
[  100.768650] wlan2: direct probe to <MAC address removed> (try 1/3)
[  100.992194] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  102.104604] wlan2: authenticate with <MAC address removed>
[  102.195895] wlan2: direct probe to <MAC address removed> (try 1/3)
[  102.396042] wlan2: direct probe to <MAC address removed> (try 2/3)
[  102.600035] wlan2: direct probe to <MAC address removed> (try 3/3)
[  102.804031] wlan2: authentication with <MAC address removed> timed out
[  103.880526] wlan2: authenticate with <MAC address removed>
[  103.974394] wlan2: direct probe to <MAC address removed> (try 1/3)
[  104.176032] wlan2: direct probe to <MAC address removed> (try 2/3)
[  104.380036] wlan2: direct probe to <MAC address removed> (try 3/3)
[  104.584031] wlan2: authentication with <MAC address removed> timed out
[  111.652530] wlan2: authenticate with <MAC address removed>
[  111.746271] wlan2: direct probe to <MAC address removed> (try 1/3)
[  111.948032] wlan2: direct probe to <MAC address removed> (try 2/3)
[  112.152038] wlan2: direct probe to <MAC address removed> (try 3/3)
[  112.356027] wlan2: authentication with <MAC address removed> timed out
[  125.400714] wlan2: authenticate with <MAC address removed>
[  125.492943] wlan2: direct probe to <MAC address removed> (try 1/3)
[  125.696039] wlan2: direct probe to <MAC address removed> (try 2/3)
[  125.900040] wlan2: direct probe to <MAC address removed> (try 3/3)
[  126.104049] wlan2: authentication with <MAC address removed> timed out
[  131.768734] wlan2: authenticate with <MAC address removed>
[  131.872569] wlan2: direct probe to <MAC address removed> (try 1/3)
[  132.076038] wlan2: direct probe to <MAC address removed> (try 2/3)
[  132.280040] wlan2: direct probe to <MAC address removed> (try 3/3)
[  132.484038] wlan2: authentication with <MAC address removed> timed out
[  139.544733] wlan2: authenticate with <MAC address removed>
[  139.643537] wlan2: direct probe to <MAC address removed> (try 1/3)
[  139.844039] wlan2: direct probe to <MAC address removed> (try 2/3)
[  140.048042] wlan2: direct probe to <MAC address removed> (try 3/3)
[  140.252040] wlan2: authentication with <MAC address removed> timed out
[  147.308737] wlan2: authenticate with <MAC address removed>
[  147.406446] wlan2: direct probe to <MAC address removed> (try 1/3)
[  147.608052] wlan2: direct probe to <MAC address removed> (try 2/3)
[  147.812036] wlan2: direct probe to <MAC address removed> (try 3/3)
[  148.016040] wlan2: authentication with <MAC address removed> timed out
[  155.080678] wlan2: authenticate with <MAC address removed>
[  155.175058] wlan2: direct probe to <MAC address removed> (try 1/3)
[  155.376041] wlan2: direct probe to <MAC address removed> (try 2/3)
[  155.580090] wlan2: direct probe to <MAC address removed> (try 3/3)
[  155.784039] wlan2: authentication with <MAC address removed> timed out
[  167.784893] wlan2: authenticate with <MAC address removed>
[  167.881666] wlan2: direct probe to <MAC address removed> (try 1/3)
[  168.084028] wlan2: direct probe to <MAC address removed> (try 2/3)
[  168.288041] wlan2: direct probe to <MAC address removed> (try 3/3)
[  168.492040] wlan2: authentication with <MAC address removed> timed out
[  169.572733] wlan2: authenticate with <MAC address removed>
[  169.666320] wlan2: direct probe to <MAC address removed> (try 1/3)
[  169.868059] wlan2: direct probe to <MAC address removed> (try 2/3)
[  170.072059] wlan2: direct probe to <MAC address removed> (try 3/3)
[  170.276146] wlan2: authentication with <MAC address removed> timed out
[  171.364757] wlan2: authenticate with <MAC address removed>
[  171.460554] wlan2: direct probe to <MAC address removed> (try 1/3)
[  171.664040] wlan2: direct probe to <MAC address removed> (try 2/3)
[  171.868027] wlan2: direct probe to <MAC address removed> (try 3/3)
[  172.072035] wlan2: authentication with <MAC address removed> timed out
[  173.168749] wlan2: authenticate with <MAC address removed>
[  173.262949] wlan2: direct probe to <MAC address removed> (try 1/3)
[  173.464034] wlan2: direct probe to <MAC address removed> (try 2/3)
[  173.668041] wlan2: direct probe to <MAC address removed> (try 3/3)
[  173.872037] wlan2: authentication with <MAC address removed> timed out
[  174.948693] wlan2: authenticate with <MAC address removed>
[  175.048168] wlan2: direct probe to <MAC address removed> (try 1/3)
[  175.252037] wlan2: direct probe to <MAC address removed> (try 2/3)
[  175.456029] wlan2: direct probe to <MAC address removed> (try 3/3)
[  175.660038] wlan2: authentication with <MAC address removed> timed out
[  176.728490] wlan2: authenticate with <MAC address removed>
[  176.824797] wlan2: direct probe to <MAC address removed> (try 1/3)
[  177.028041] wlan2: direct probe to <MAC address removed> (try 2/3)
[  177.232040] wlan2: direct probe to <MAC address removed> (try 3/3)
[  177.436023] wlan2: authentication with <MAC address removed> timed out
[  184.492684] wlan2: authenticate with <MAC address removed>
[  184.582945] wlan2: direct probe to <MAC address removed> (try 1/3)
[  184.784051] wlan2: direct probe to <MAC address removed> (try 2/3)
[  184.988059] wlan2: direct probe to <MAC address removed> (try 3/3)
[  185.192061] wlan2: authentication with <MAC address removed> timed out
[  311.308491] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  311.636291] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  312.010228] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  312.324626] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  353.264578] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  353.598609] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  502.953002] wlan2: authenticate with <MAC address removed>
[  503.049981] wlan2: direct probe to <MAC address removed> (try 1/3)
[  503.252029] wlan2: direct probe to <MAC address removed> (try 2/3)
[  503.456017] wlan2: direct probe to <MAC address removed> (try 3/3)
[  503.660036] wlan2: authentication with <MAC address removed> timed out
[  504.732719] wlan2: authenticate with <MAC address removed>
[  504.829359] wlan2: send auth to <MAC address removed> (try 1/3)
[  504.831083] wlan2: authenticated
[  504.880029] wlan2: associate with <MAC address removed> (try 1/3)
[  504.883095] wlan2: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  504.888075] wlan2: associated
[  504.888395] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready


**************** done ********************




```

---

### Post by varunendra on 2013-03-07
You still did not tell me anything about what all you have tried so far and what guides/suggestions, if any, you have followed.

If I have to guess and decide by command outputs alone, my best suggestion is to simply reinstall and start fresh. For the following reasons -
> **holier said:**
> 
code:
```

**** lsmod ****

Module                  Size  Used by
**[COLOR="#FF0000"]ndiswrapper[/COLOR]**           192684  0 

**** blacklist.conf ****

blacklist uvcvideo[B][COLOR="#FF0000"]
blacklist brcmsmac
blacklist bcma[/COLOR][/B]


**** dmesg ****

[   29.801494] iwlwifi: `1' **[COLOR="#FF0000"]invalid for parameter `11_ndisable'[/COLOR]**
[   29.853365] **[COLOR="#FF0000"]ndiswrapper version 1.58 loaded[/COLOR]** (smp=yes, preempt=no)
....
[   30.066643] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMCreateLog'
[   30.066815] **[COLOR="#FF0000"]ndiswrapper[/COLOR]** (load_sys_files:199): **[COLOR="#FF0000"]couldn't prepare driver 'net8192se'[/COLOR]**
[   30.067364] **[COLOR="#FF0000"]ndiswrapper[/COLOR]** (load_wrap_driver:121): **[COLOR="#FF0000"]couldn't load driver 'net8192se'[/COLOR]**

```
So as we can see, you have been trying on ndiswrapper which is usually our last resort. In most cases the native linux drivers work just fine, much better than ndiswrapper.
You have also tried intel driver with a driver parameter, which by the way is both wrong in syntax and not required as you don't have an intel card at all.
You have also tried something with broadcom drivers which again I have no idea why.

So it appears that you have been trying _everything you found on the net, regardless of whether or not it was applicable to your system_. Accordingly, the best advice is - reinstall if possible and start fresh.

If you don't want to do that for some reason, then the first step would be to '[completely remove]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo")' ndiswrapper, then try the following for a test -
```
sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se swenc=1
```
Just copy-paste it in terminal to avoid typos.

Post back the result.

But I would once again suggest that starting fresh by reinstalling Ubuntu would be the quickest way for you. Let me know if you wish to do that.

---

### Post by holier on 2013-03-07
hey varun,
the two lines of code did the trick !
thank you very much for your help .i apperciate it

---

### Post by holier on 2013-03-07
hey again varun,
i lost my wireless again after reboot . i retype the two lines of code and it's back again
how to make it permanent ?

---

### Post by varunendra on 2013-03-08
> **holier said:**
> hey again varun,
i lost my wireless again after reboot . i retype the two lines of code and it's back again
how to make it permanent ?

Make sure you have properly removed ndiswrapper first. Run the command -
```
lsmod
```
..and make sure ndiswrapper no more appears in the output.

Then open your /etc/modules file with root access -
```
gksu gedit /etc/modules
```
and add **rtl8192se** at the end of it. Proofread, save and close the file.

You can also do it with a single command -
```
echo "rtl8192se" | sudo tee -a /etc/modules
```

Then reboot and run **lsmod** to see if **rtl8192se** is loaded automatically. Moreover, if your wireless is working.

If it is, there is no need for the "swenc=1" parameter. But if it has difficulty in connecting or has speed problems, then make this parameter permanent as well by creating a configuration file for it -
```
echo "options rtl8192se swenc=1" | sudo tee rtl8192se.conf
```

Reboot, try to connect and let us know the result.

---

### Post by holier on 2013-03-10
hey varun, it worked!! thank you very much

---

### Post by varunendra on 2013-03-10
> **holier said:**
> it worked!!

So sweet to the ears !! You're welcome ! :popcorn:

---

### Post by holier on 2013-03-10
hey varun, it worked!! thank you very much

---

