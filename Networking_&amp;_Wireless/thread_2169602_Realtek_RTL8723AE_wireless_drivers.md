---
title: "Realtek RTL8723AE wireless drivers"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by Andrew_Lucas on 2013-08-22
[B]EDIT: Argh, now I've no connection at all. I've left home, and am trying to connect to my grandparents WiFi, but it just won't take it. The password box keeps appearing as though I've made a typo. I've checked and rechecked the password, and my phone (from which I'm posting this) seems to be having no trouble whatsoever. Any suggestions? The module seems to be loading still (i.e.it's still appearing  when lsmod is issued), but I've no idea what to do to actually troubleshoot the driver :(

UPDATE: Still suffering. My only internet access is through my phone (which is able to connect using the wifi password the PC refuses to take) - enabling USB tethering and then plugging it into the laptop (after Bluetooth tethering seemed to be more trouble than it's worth). Help needed fairly urgently, I want to have all computer problems ironed out before September (if possible, with the community's help).
[/B]
Hi all,

Out of the box, the wireless drivers *do* work, but there are a few issues:

1) Not long after installing, wireless networking was completely disabled because of a "hardware switch". The settings hadn't changed (the computer had just been rebooted, possibly following the standard package upgrade i ran after a fresh install). I tried rebooting and it fixed itself, and I forgot about it.

2) Yesterday, the same thing happened again (after an upgrade of packages). The reboot didn't work, so I started researching it. I found some threads here which gave a terminal command which confirmed what the GUI was telling me - that apparently a hardware block was in place. I continued tried issuing commands probing the issue (I didn't get as far as changing anything) and rebooting - trying the function keys, BIOS etc. On the 3rd/4th reboot the issue solved itself.

3) Wireless strength displayed is unreliable. At the moment it is regularly flipping between the lowest possible (whilst still connected) and full bars - without me moving position.

I've tried messing with ndiswrapper in the past, and honestly, it was a nightmare - I'd rather stick with the native Linux driver, buggy as it seems to be. Does anyone have any fixes for the bugs outlined? Or could someone at least guide me through how to locate the package acting as a driver, and then it's maintainer - so I can raise the issue with them? Would launchpad be the place to file a bug report?

Some basic information:
```

andy@ZoostormLinuxLaptop:~$ lspci | grep Network
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

``````

andy@ZoostormLinuxLaptop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp.

``````

andy@ZoostormLinuxLaptop:~$ lsmod
Module                  Size  Used by
rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
cdc_ether              13453  1 rndis_host
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
usb_storage            57204  0 
dm_crypt               22820  1 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  16 
joydev                 17377  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_via      51018  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
binfmt_misc            17500  1 
snd_hwdep              13602  1 snd_hda_codec
arc4                   12615  2 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rtl8723ae              86459  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13355  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
kvm_intel             132891  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   443165  1 kvm_intel
btusb                  22474  0 
snd_rawmidi            30180  1 snd_seq_midi
cfg80211              510937  3 mac80211,rndis_wlan,rtlwifi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
bluetooth             228667  22 bnep,btusb,rfcomm
lp                     17759  0 
mac_hid                13205  0 
microcode              22881  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
rtsx_pci_ms            13011  0 
mei                    41158  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
parport                46345  3 lp,ppdev,parport_pc
psmouse                95905  0 
memstick               16554  1 rtsx_pci_ms
soundcore              12680  1 snd
serio_raw              13215  0 
lpc_ich                17061  0 
rtsx_pci_sdmmc         17475  0 
wmi                    19070  0 
i915                  600396  2 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
ahci                   25731  3 
libahci                31364  1 ahci
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
r8169                  67466  0 
drm_kms_helper         49394  1 i915
drm                   286028  3 i915,drm_kms_helper
rtsx_pci               33988  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

---

### Post by Andrew_Lucas on 2013-08-23
BUMPing (as advised, edits non-withstanding).

---

### Post by varunendra on 2013-08-24
Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the report the script generates.
Thanks !

---

### Post by Andrew_Lucas on 2013-08-24
> **varunendra said:**
> Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the report the script generates.
Thanks !

Here:

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 0bb4:0fb4 HTC (High Tech Computer Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  3 mac80211,rndis_wlan,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.217
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


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


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    millers network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    virginmedia8829612: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2
    NETGEAR38:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA2
    virginmedia6871641: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    DAZ:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    virginmedia2191909: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ZyXEL_6286sil:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8829612"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016d2b9c6a8
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696138383239363132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2191909"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e88d4e9195
                    Extra: Last beacon: 904ms ago
                    IE: Unknown: 001276697267696E6D6564696132313931393039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"millers network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002879b800174
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 000F6D696C6C657273206E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"DAZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000036f67b75183
                    Extra: Last beacon: 932ms ago
                    IE: Unknown: 000344415A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1197043093752E03A00CA5B
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   18.554002] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   19.023718] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.023903] rtlwifi: wireless switch is on
[   22.260918] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.261233] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

---

### Post by varunendra on 2013-08-24
Is "virginmedia8829612" your wifi access point (guessing by its signal strength)? If yes, and if you can, please try changing the channel from 6 to 1 or 11.

If it is one of those which are using WPA/WPA2 mixed mode encryption, it is 'Strongly' recommended to change the encryption type in the router/access-point to pure WPA-PSK(AES) only, no mixed mode.

In your laptop, please try the following -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y
```
Do Not Reboot after running above commands. The above is a temporary change and will be lost at next boot. If it seems to help, we'll make it permanent.


**PS:**
As for filing a bug report, yes, launchpad is the appropriate place to do so.
Also, as you can see in the modinfo part of the script output, the authors of the driver and their email IDs are mentioned-
```
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
*<snip>*
author:         Larry Finger    <**Larry.Finger@lwfinger.net**>
author:         Realtek WlanFAE    <**wlanfae@realtek.com**>
author:         lizhaoming    <**chaoming_li@realsil.com.cn**>
```
If you wish, you may use these emails to directly report the bug to them. Although I can't say whether or not you'd get a response.

---

### Post by Andrew_Lucas on 2013-08-24
> **varunendra said:**
> Is "virginmedia8829612" your wifi access point (guessing by its signal strength)? If yes, and if you can, please try changing the channel from 6 to 1 or 11.

If it is one of those which are using WPA/WPA2 mixed mode encryption, it is 'Strongly' recommended to change the encryption type in the router/access-point to pure WPA-PSK(AES) only, no mixed mode.

In your laptop, please try the following -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y
```
Do Not Reboot after running above commands. The above is a temporary change and will be lost at next boot. If it seems to help, we'll make it permanent.


**PS:**
As for filing a bug report, yes, launchpad is the appropriate place to do so.
Also, as you can see in the modinfo part of the script output, the authors of the driver and their email IDs are mentioned-
```
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
*<snip>*
author:         Larry Finger    <**Larry.Finger@lwfinger.net**>
author:         Realtek WlanFAE    <**wlanfae@realtek.com**>
author:         lizhaoming    <**chaoming_li@realsil.com.cn**>
```
If you wish, you may use these emails to directly report the bug to them. Although I can't say whether or not you'd get a response.

Issued the modprobe commands, to no avail. I'm a bit reluctant to mess with the router since it's not mine and I don't know what other devices may need to connect to it after I leave (and my grandparents are relatively technophobic, so wouldn't be able to sort anything themselves). I'm running Xfce, and there doesn't *seem* to be any option through the GUI to change the channel...is there a CLI I could access to attempt that?

Since we're discounting the modprobe commands, should I reboot to undo the changes? Also, for my own curiosity, can you explain what the commands are seeking to do, and where you think the problem might be?

I'll look into filing a bug report in the mean time, and/or emailing the authors. I'll post back here when that's done, thanks for the help.

---

### Post by varunendra on 2013-08-24
> **Andrew_Lucas said:**
> I'm running Xfce, and there doesn't *seem* to be any option through the GUI to change the channel...is there a CLI I could access to attempt that?
That was something to be done in the router itself, not in the laptop. Since you can't (or won't) do that, there's nothing else that can be done regarding that.

> Also, for my own curiosity, can you explain what the commands are seeking to do, and where you think the problem might be?
The first modprobe command, due to the "-r" switch, removes the driver. The next one loads it again with the parameter "swenc=1". This parameter (swenc=1) shifts the burden of packet encryption from the adapter hardware to the software (OS/driver).

It helps when the data stream is too fast for the adapter's hardware based encryption to keep up with (thus resulting in corrupt packets, causing fluctuating speeds or intermittent connection), since the computer's processing power is relatively much higher and it can easily afford that additional burden.

However, now that it doesn't seem to help, of course you can reboot (if you haven't already).

I think the problem may be driver's inefficiency. But there may be other issues as well which we may not have looked upon yet. I'm a bit short of time right now, will post back when (and if) I get time. Meanwhile, I may ask one of the senior members to look at it.

As an absolutely blind shot, with no reasonable explanation at all, you may try [Wicd]("https://help.ubuntu.com/community/WICD") instead of the default Network Manager. It does seem to help in 'some' cases.

---

### Post by varunendra on 2013-08-25
I was just suggested by Dr. Chili555, my senior most wireless guru, to ask you to run the script again 'Without' the usb adapter plugged in, as the Network Manager may not give us relevant results when two wireless devices are present at the same time.

Accordingly, could you please try that again?

Make sure the usb wifi adapter is not plugged in, let the internal card try to connect and fail, then run the script again (without the usb adapter) and post back the new result file. Thanks.

---

### Post by Andrew_Lucas on 2013-08-25
> **varunendra said:**
> I was just suggested by Dr. Chili555, my senior most wireless guru, to ask you to run the script again 'Without' the usb adapter plugged in, as the Network Manager may not give us relevant results when two wireless devices are present at the same time.

Accordingly, could you please try that again?

Make sure the usb wifi adapter is not plugged in, let the internal card try to connect and fail, then run the script again (without the usb adapter) and post back the new result file. Thanks.

My "internal" wireless adapter is going through one of it's funny periods at the moment, where it mistakenly thinks that the adapter is disabled by a hardware switch. There seems to be no reason for this: it just so happened from this particular cold start the driver decided to play up. As explained in the thread, rebooting would probably fix that, at least temporarily.

I'll run the script never the less, and post the results here.

---

### Post by Andrew_Lucas on 2013-08-25
> **Andrew_Lucas said:**
> My "internal" wireless adapter is going through one of it's funny periods at the moment, where it mistakenly thinks that the adapter is disabled by a hardware switch. There seems to be no reason for this: it just so happened from this particular cold start the driver decided to play up. As explained in the thread, rebooting would probably fix that, at least temporarily.

I'll run the script never the less, and post the results here.

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  3 mac80211,rndis_wlan,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:90:F5:E0:F6:B6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             unavailable
  Default:           no
  HW Address:        20:16:D8:D3:FB:6B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****


***** blacklist *****


```

That's with the "WiFi disabled by hardware switch" bug in the GUI. I'm going to reboot and see if I can get rid of that, and then I'll post again the output from the script.

Btw, I also tried Wicd, I was getting some DBUS error, and couldn't get it to function at all. It ended up being purged, I'm back to using network-manager and network-manager-gnome now.

I'm going to file a bug report too, and send an email to the authors - any suggestions on exactly what info I should send them?

---

### Post by Andrew_Lucas on 2013-08-25
> **Andrew_Lucas said:**
> ```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

rndis_wlan             36998  0 
rndis_host             13855  1 rndis_wlan
usbnet                 31879  3 rndis_host,rndis_wlan,cdc_ether
rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  3 mac80211,rndis_wlan,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:90:F5:E0:F6:B6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             unavailable
  Default:           no
  HW Address:        20:16:D8:D3:FB:6B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****


***** blacklist *****


```

That's with the "WiFi disabled by hardware switch" bug in the GUI. I'm going to reboot and see if I can get rid of that, and then I'll post again the output from the script.

Btw, I also tried Wicd, I was getting some DBUS error, and couldn't get it to function at all. It ended up being purged, I'm back to using network-manager and network-manager-gnome now.

I'm going to file a bug report too, and send an email to the authors - any suggestions on exactly what info I should send them?

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:90:F5:E0:F6:B6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        20:16:D8:D3:FB:6B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia6871641: Infra, 00:8E:F2:C9:E1:BC, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    NETGEAR38:       Infra, 28:C6:8E:B2:74:2D, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
    virginmedia2191909: Infra, A0:21:B7:D5:DE:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    millers network: Infra, 00:1C:DF:E4:03:3B, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    ZyXEL_6286sil:   Infra, 40:4A:03:CE:8A:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    virginmedia8829612: Infra, 84:1B:5E:A0:DD:56, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:90:F5:E0:F6:B6,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: 84:1B:5E:A0:DD:56
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8829612"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d106b5375
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696138383239363132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:8E:F2:C9:E1:BC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6871641"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017d0daa6d3
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696136383731363431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010D4A0FBB0A670984D0851E3C453996B9A102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343835100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: A0:21:B7:D5:DE:8C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2191909"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000feca48219f
                    Extra: Last beacon: 14520ms ago
                    IE: Unknown: 001276697267696E6D6564696132313931393039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:1C:DF:E4:03:3B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"millers network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029dd92ed16e
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000F6D696C6C657273206E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000


***** resolv.conf *****


***** blacklist *****


```

I executed the script using the sh command, after entering the password and having it return as failed (or, rather, just having it returned without any output at all - as if I'd made a typo, which checking and rechecking showed I hadn't).

---

### Post by varunendra on 2013-08-25
> **Andrew_Lucas said:**
> I executed the script **using the [COLOR="#FF0000"]sh command[/COLOR]**, after entering the password and having it return as failed...

Please run it without '**[COLOR="#FF0000"]sh[/COLOR]**'. If you must use an interpreter command (for example if you are running the script from a FAT partition), use '**bash**' instead of 'sh'. That is, either -
```
./wireless_script
```
or
```
bash wireless_script
```

The script contains code that is not compatible with 'sh' shell, so it terminates at the blacklist part, thus not giving us a full report.

Oh, and the previous result contained the rndis_wlan driver. We (yeah, some very good people are watching it) are suspecting that it may be conflicting with rtl8723ae/rtlwifi, especially over the cfg80211 driver. These drivers will be loaded as soon as you plug in the USB adapter and will remain loaded until next boot (or until being manually unloaded).

So make sure to run the script after a fresh boot, without plugging in the USB adapter (like you did the 2nd time).

---

### Post by Andrew_Lucas on 2013-08-25
> **varunendra said:**
> Please run it without '**[COLOR=#FF0000]sh[/COLOR]**'. If you must use an interpreter command (for example if you are running the script from a FAT partition), use '**bash**' instead of 'sh'. That is, either -
```
./wireless_script
```
or
```
bash wireless_script
```

The script contains code that is not compatible with 'sh' shell, so it terminates at the blacklist part, thus not giving us a full report.

Oh, and the previous result contained the rndis_wlan driver. We (yeah, some very good people are watching it) are suspecting that it may be conflicting with rtl8723ae/rtlwifi, especially over the cfg80211 driver. These drivers will be loaded as soon as you plug in the USB adapter and will remain loaded until next boot (or until being manually unloaded).

So make sure to run the script after a fresh boot, without plugging in the USB adapter (like you did the 2nd time).

Does the "hardware switch disabled" make any difference?

Thanks for the support! I'll generate a report now, with bash (it didn't seem to do anything through the GUI, i.e. just by clicking)?

---

### Post by varunendra on 2013-08-25
> **Andrew_Lucas said:**
> Does the "hardware switch disabled" make any difference?

Thanks for the support! I'll generate a report now, with bash (it didn't seem to do anything through the GUI, i.e. just by clicking)?

Yes it does make a big difference. There may be quite a few reasons for the hardware switch issue, like a dodgy switch, buggy BIOS, probably a lose card, a BIOS setting to disable the internal card when another interface is working etc.

For now, please try whatever you do to enable it again, then run the script when it is "attempting to connect" (and failing).

The GUI method should have worked if the script is on your desktop or home. It will fail if it has not been made executable (you won't get the "Run" option after double-clicking it). [s]However, the nautilus settings in 13.04 have been changed a bit, so "nothing happening just by double-clicking" may be a result of such a change[/s] *[COLOR="#000080"]**EDIT :** You are on Xubuntu, so you must be using Thunar instead of Nautilus file manager. I'm not sure about its behaviour..[/COLOR]*. I'll take a look at it and will update my Wireless Script Instructions post as and if required. Thanks for pointing that out. :)

---

### Post by Andrew_Lucas on 2013-08-25
> **varunendra said:**
> Yes it does make a big difference. There may be quite a few reasons for the hardware switch issue, like a dodgy switch, buggy BIOS, probably a lose card, a BIOS setting to disable the internal card when another interface is working etc.

For now, please try whatever you do to enable it again, then run the script when it is "attempting to connect" (and failing).

The GUI method should have worked if the script is on your desktop or home. It will fail if it has not been made executable (you won't get the "Run" option after double-clicking it). [s]However, the nautilus settings in 13.04 have been changed a bit, so "nothing happening just by double-clicking" may be a result of such a change[/s] *[COLOR=#000080]**EDIT :** You are on Xubuntu, so you must be using Thunar instead of Nautilus file manager. I'm not sure about its behaviour..[/COLOR]*. I'll take a look at it and will update my Wireless Script Instructions post as and if required. Thanks for pointing that out. :)

Just a note: my computer is certainly capable (decent dual core Pentium, 8GB RAM etc) of running KDE/Gnome/Unity, but I decided on Xubuntu because I liked the interface. :D It doesn't have any of KDE's clunkiness and is much more intuitive than GNOME. I migrated from KDE, after a year or more using that, and I do miss the "everything is configurable" approach, though. Tabbed browsing is a must for me, too, so I use PCManFM rather than Thunar (which without tabbed browsing I find *incredibly* irritating).

Right, this first output is from *before* attempting to connect to any network (wireless network, in both cases, I executed the script before connecting my phone for the USB tethering).

I'm a little alarmed you mentioned a loose card, since the laptop is only a few weeks old - I just assumed that it was a bug, since rebooting (or, rather, shutting down completely and starting from cold) seems to fix it? I've checked in the BIOS (since that's what some threads I found suggested) and there's no option to either disable or enable the wireless adapter. All there is is an option to boot from the network (I sometimes find trying that, waiting for it to give up looking for a network device, and then letting it boot from the HDD fixed the "hardware switch disabled" issue). 

I don't know if it is relevant, but I should probably mention that when I got the computer, I put the BIOS in "legacy mode" (to disable that security feature - the name of which has escaped me for the moment D; ). I'm unlikely to install Windows on this computer, but if down the line I decided to, I thought it would be better to avoid the conflict that can occur if both your Linux and Windows installations don't have that security feature enabled. (Vague, I know, but the name has completely escaped me...E something possibly?).

Anyway, output 1:

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

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


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia8829612: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ZyXEL_6286sil:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    DAZ:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    millers network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    virginmedia2191909: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    virginmedia6871641: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8829612"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030cd3ae818
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696138383239363132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2191909"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010287ead187
                    Extra: Last beacon: 952ms ago
                    IE: Unknown: 001276697267696E6D6564696132313931393039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6871641"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b8dae0bcf
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696136383731363431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010D4A0FBB0A670984D0851E3C453996B9A102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343835100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180206F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1197043093752E03A00CA5B
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.945612] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   13.087462] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.087638] rtlwifi: wireless switch is on
[   17.390293] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.390624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

Output 2 (remember, taken *after* attempting to connect):

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

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


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ZyXEL_6286sil:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 16 WPA
    DAZ:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    millers network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    virginmedia2191909: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    virginmedia6871641: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    virginmedia8829612: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    NETGEAR38:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    virginmedia2731249: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8829612"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000310c79f71b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001276697267696E6D6564696138383239363132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6871641"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bccef5beb
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001276697267696E6D6564696136383731363431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010D4A0FBB0A670984D0851E3C453996B9A102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343835100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1197043093752E03A00CA5B
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.945612] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   13.087462] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.087638] rtlwifi: wireless switch is on
[   17.390293] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.390624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  152.580001] wlan0: authenticate with <MAC address removed>
[  152.608779] wlan0: send auth to <MAC address removed> (try 1/3)
[  152.610381] wlan0: authenticated
[  152.611801] wlan0: associate with <MAC address removed> (try 1/3)
[  152.614796] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  152.614918] wlan0: associated
[  152.614925] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  160.347715] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  166.399369] wlan0: authenticate with <MAC address removed>
[  166.424987] wlan0: send auth to <MAC address removed> (try 1/3)
[  166.426615] wlan0: authenticated
[  166.430587] wlan0: associate with <MAC address removed> (try 1/3)
[  166.433688] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  166.433819] wlan0: associated
[  174.227434] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

****************** done ******************


```

---

### Post by Andrew_Lucas on 2013-08-25
When Googling surrounding the "hardware switch disabled" bug, I came across rfkill, and it was describing the adapter as being "hard blocked". The GUI wasn't lying. I don't know if that gives any greater insight into the problem?

---

### Post by varunendra on 2013-08-25
Hmm.. let's address things in the order you posted, including the offtopics ;)
> **Andrew_Lucas said:**
> Tabbed browsing is a must for me, too, so I use PCManFM rather than Thunar (which without tabbed browsing I find *incredibly* irritating).
It seems the current versions of Thunar do have the tabbed browsing feature. I don't have an XFCE based distro ISO to verify that, but I just downloaded a screenshot for Thunar from Synaptic Package Manager and it shows tabs in it. ;)

> .....I put the BIOS in "legacy mode" (to disable that security feature - the name of which has escaped me for the moment D; )..... the name has completely escaped me...**[COLOR="#B22222"]E [/COLOR]**something possibly?).**[COLOR="#B22222"]..FI[/COLOR]**.
It is EFI or [UEFI]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface") (Unified Extensible Firmware Interface), and the security feature you are afraid of is called "Secure Boot", which in itself is not a bad thing, just its implementation by Microsoft is a bit controversial. :)

Now onto the real business -

> ```

***** dmesg *****

[  152.610381] wlan0: authenticated
[  152.611801] wlan0: associate with <MAC address removed> (try 1/3)
[  152.614796] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  **152.614918**] wlan0: associated
[  152.614925] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  **160.347715] wlan0: deauthenticated from <MAC address removed> ([COLOR="#FF0000"]Reason: 15[/COLOR])**
....
[  166.426615] wlan0: authenticated
[  166.430587] wlan0: associate with <MAC address removed> (try 1/3)
[  166.433688] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  **166.433819**] wlan0: associated
[  **174.227434] wlan0: deauthenticated from <MAC address removed> (Reason: 15)**

****************** done ******************

```
Everything in the report looks good to me (except the WPA/WPA2 mixed mode in some of the access points, which isn't necessarily a problem, but sometimes adds to a problem..). I did some research on "[deauthentication Reason 15]("http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/")" highlighted above and it turned out to be failure to complete a complex authentication process, namely - "[Four-way Handshake]("https://en.wikipedia.org/wiki/IEEE_802.11i-2004#The_Four-Way_Handshake") Timed Out".

As per the timings highlighted above, it happened in about 8 seconds both times, which is (including overheads and message display delays) plenty of time to complete such an authentication.

For now, the only thing I can suggest is to try the swenc=Y parameter once again, this time the "driver conflict" possibility being ruled out. So, reboot, try again -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y
```
..and see if it does the miracle. If it doesn't, I'm more and more inclined towards trying out the proprietary driver from realtek, although I have no evidence so far that suggests it may perform any better. In fact, I'm not even sure it is a driver issue at all, but we'll see..

**PS:**
The "**rfkill list all**" command only lists the current block state of all radio devices present.
The "**sudo rfkill unblock all**" command is meant to unblock only the "soft block" state, but it sometimes also unblocks the "hard block" state of the devices, I don't know how and why, but as long as it helps, who cares.

---

### Post by Andrew_Lucas on 2013-08-26
> **varunendra said:**
> Hmm.. let's address things in the order you posted, including the offtopics ;)

It seems the current versions of Thunar do have the tabbed browsing feature. I don't have an XFCE based distro ISO to verify that, but I just downloaded a screenshot for Thunar from Synaptic Package Manager and it shows tabs in it. ;)


Thanks for this! I got into the habit of just installing PCManFM, so haven't seen the latest version of Thunar. I'm going to try using it for a little while.

> **varunendra said:**
> 
**[COLOR=#B22222]..FI[/COLOR]**.
It is EFI or [UEFI]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface") (Unified Extensible Firmware Interface), and the security feature you are afraid of is called "Secure Boot", which in itself is not a bad thing, just its implementation by Microsoft is a bit controversial. :)
[/QUOTE[

Yeah, I read something about this a while back, after having boot trouble. When I saw there was the option to disable it, I thought it would be best to do that, and save myself any trouble down the line. Disk encryption and a BIOS/boot password are enough security for me.

[QUOTE=varunendra;12769299]
Now onto the real business -


Everything in the report looks good to me (except the WPA/WPA2 mixed mode in some of the access points, which isn't necessarily a problem, but sometimes adds to a problem..). I did some research on "[deauthentication Reason 15]("http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/")" highlighted above and it turned out to be failure to complete a complex authentication process, namely - "[Four-way Handshake]("https://en.wikipedia.org/wiki/IEEE_802.11i-2004#The_Four-Way_Handshake") Timed Out".

As per the timings highlighted above, it happened in about 8 seconds both times, which is (including overheads and message display delays) plenty of time to complete such an authentication.

For now, the only thing I can suggest is to try the swenc=Y parameter once again, this time the "driver conflict" possibility being ruled out. So, reboot, try again -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y
```
..and see if it does the miracle. If it doesn't, I'm more and more inclined towards trying out the proprietary driver from realtek, although I have no evidence so far that suggests it may perform any better. In fact, I'm not even sure it is a driver issue at all, but we'll see..


No luck. Output from the terminal here:

```
andy@ZoostormLinuxLaptop:~$ sudo modprobe -rfv rtl8723ae
[sudo] password for andy: 
rmmod rtl8723ae
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
andy@ZoostormLinuxLaptop:~$ sudo modprobe -v rtl8723ae swenc=Y
insmod /lib/modules/3.8.0-29-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko swenc=Y
```

After attempting to connect, and having no luck, I ran the script (I don't know if the output will be useful):

```

*************** info trace ***************

***** uname -a *****

Linux ZoostormLinuxLaptop 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b34c Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    millers network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    ZyXEL_6286sil:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA
    BTHub3-4Q8S:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    virginmedia2191909: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26
    BTWiFi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    virginmedia8829612: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2


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



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2191909"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011736025195
                    Extra: Last beacon: 952ms ago
                    IE: Unknown: 001276697267696E6D6564696132313931393039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8829612"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000457b428f7a
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001276697267696E6D6564696138383239363132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"millers network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000161fb9de7c
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000F6D696C6C657273206E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDFE4033B1021001242656C6B696E20436F72706F726174696F6E1023000C463544383633362D3420763110240007312E30302E30331042000E31323834343836333630313136381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070600000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001143db2279
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-4Q8S"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001143db0e3b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000B4254487562332D34513853
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010FCFE3471FF0584975810C54041BAF98B1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020080103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001143dd8279
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL_6286sil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000064e3c7541ca
                    Extra: Last beacon: 7772ms ago
                    IE: Unknown: 000D5A7958454C5F3632383673696C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1197043093752E03A00CA5B
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   14.053903] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   14.276437] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.276607] rtlwifi: wireless switch is on
[   26.151499] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.156086] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  755.304626] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[  755.306110] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  755.307423] rtlwifi: wireless switch is on
[  755.691792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  755.692055] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  764.335184] wlan0: authenticate with <MAC address removed>
[  764.363765] wlan0: send auth to <MAC address removed> (try 1/3)
[  764.365832] wlan0: authenticated
[  764.366438] wlan0: associate with <MAC address removed> (try 1/3)
[  764.369497] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  764.369612] wlan0: associated
[  764.369639] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  774.372258] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  774.413651] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  797.246889] wlan0: authenticate with <MAC address removed>
[  797.268588] wlan0: send auth to <MAC address removed> (try 1/3)
[  797.270160] wlan0: authenticated
[  797.274264] wlan0: associate with <MAC address removed> (try 1/3)
[  797.277330] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  797.277442] wlan0: associated
[  805.028061] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

****************** done ******************


```

"Reason 15" still seems to be causing trouble. I suppose trying the proprietry driver couldn't hurt, could you take me through that?

> **varunendra said:**
> 
**PS:**
The "**rfkill list all**" command only lists the current block state of all radio devices present.
The "**sudo rfkill unblock all**" command is meant to unblock only the "soft block" state, but it sometimes also unblocks the "hard block" state of the devices, I don't know how and why, but as long as it helps, who cares.

Thanks for this, too. I'll probably end up learning this command, since the "hard block" seems to be pretty unpredictable and occurs fairly frequently.

---

### Post by Andrew_Lucas on 2013-08-26
Btw, does the script tell you what driver is in use when the USB tethering is used to get a connection? Would it just be the USB driver?

---

### Post by varunendra on 2013-08-27
> **Andrew_Lucas said:**
> I suppose trying the proprietry driver couldn't hurt, could you take me through that?
Sure. The default package from realtek has not been adapted for the latest kernel versions yet, so we shall need to do some modifications manually (step 3 below) in order to be able to compile it successfully (source of proposed modifications [here]("http://ubuntuforums.org/showthread.php?t=2146803&p=12662928#post12662928")).

Here are the instructions to download and compile the driver on Ubuntu 13.04 -

First, make sure the components required for compiling a package are installed on the system. To ensure that, get connected to internet > Open terminal (Ctrl+Alt+T) > run the following command -
```
sudo apt-get install linux-headers-generic build-essential
```

Now the steps for the driver -

[INDENT]1) Download the RTL8188CE driver package for Linux from here : [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722) and copy it to your desktop (it's about 12 MB download).

2) Right-click the downloaded file (linux_mac80211_0012.0207.2013.tar.bz2) > click "Extract here". This will extract a folder named "rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211 _001 2.0207.2013" on your desktop.

3) Now open the "pci.h" file from the extracted directory above, and add following lines below the line #31 (that says - "#define __RTL_PCI_H__")-
```
#ifndef __devinit
#define __devinit
#define __devinitdata
#endif
```
Proofread, save and close the file.

4) Open a terminal (Ctrl+Alt+T) and run following commands :
```
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install
```
5) Reboot or manually load the driver with -
```
sudo modprobe -v rtl8723e
```
Watch out for errors during the whole process, post back if there are any.[/INDENT]

If you still can not connect after a reboot, run the script again and post back its fresh output.

> **Andrew_Lucas said:**
> Btw, does the script tell you what driver is in use when the USB tethering is used to get a connection? Would it just be the USB driver?
The "nm-tool" part of the script output tells you the currently available connections and drivers in use. You can use the command "nm-tool" independently to get that.

---

### Post by actionmystique on 2014-03-04
Hello @varunendra,

I experience the same prtoblems with my Realtek RTL8723AE NIC as many other people on Ubuntu 13.10.
I tried to download the proprietary driver package "RTL8188CE-VAU" from Realtek site and extracted it, but the reference to "RTL8723AE" is gone.

Any hint about where we could locate the correct package?

---

### Post by varunendra on 2014-03-04
> **actionmystique said:**
> I tried to download the proprietary driver package "**[COLOR="#FF0000"]RTL8188CE-VAU[/COLOR]**" from Realtek site
Wrong package! The correct one is **RTL8188CE**, the section ABOVE RTL8192CE-VAU or RTL8192CE-VA4 sections. If you clicked at the link I gave in my previous post, the table opens right at the top of screen, you'll have to scroll up a bit to see the section name.

---

