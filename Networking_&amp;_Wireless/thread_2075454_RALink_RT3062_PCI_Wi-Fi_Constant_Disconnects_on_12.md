---
title: "RALink RT3062 PCI Wi-Fi Constant Disconnects on 12.04"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by ddomain1 on 2012-10-23
This is a follow-up to this thread - > [COLOR="Navy"]http://ubuntuforums.org/showthread.php?p=12284691#post12284691[/COLOR]
It's the same system, but had to replace the HDD. Istalled 12.04 32-bit Server again, noGUI, complied the RT3062 drivers from RALink site., now I'm back to the point in above thread where:
> However, the card only stays connected for 1-2mins to a max of ~5mins, then it disconnects everytime, and only a shutdown/restart will make it re-connect....Most times not even a good minute - really annoying!!

I attached the output of:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

Any help with troubleshooting appreciated. Thanks;)

---

### Post by ddomain1 on 2012-12-19
Still looking for a troubleshooting solution to this problem.
Re-installed 12.04 Server, still having disconnects with PCI card. See info below for very short time the card is connected (maybe < 20-30s). About to replace with USB adapter, but for now any help is appreciated.
```

*************** info trace ****************



**** uname -a ****


Linux ubuntubox 3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7596]
	Kernel driver in use: r8169
--
03:06.0 Network controller [0280]: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]
	Subsystem: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]
	Kernel driver in use: rt2860


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse


**** iwconfig ****


ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-60 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**** rfkill ****




**** lsmod ****


Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
radeon                737926  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  0 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ttm                    65344  1 radeon
snd_hwdep              13276  1 snd_hda_codec
drm_kms_helper         45466  1 radeon
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
drm                   197599  3 radeon,ttm,drm_kms_helper
snd_timer              28931  1 snd_pcm
rt3562sta             882339  1 
sp5100_tco             13495  0 
snd                    62064  7 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
ppdev                  12849  0 
k10temp                12990  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
parport_pc             32114  1 
wmi                    18744  0 
i2c_piix4              13093  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77392  1 usbhid
pata_atiixp            12999  0 
r8169                  56321  0 


**** nm-tool ****




**** NetworkManager.state ****




**** NetworkManager.conf ****




**** NetworkManager.conf-10.04 ****




**** interfaces ****


# This file describes the network interfaces available on your system xc
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# auto eth0
# iface eth0 inet static
#	 address 192.168.0.6
#	 netmask 255.255.255.0
#	 network 192.168.0.0
#	 broadcast 192.168.0.255
#	 gateway 192.168.0.254
# dns-* options are implemented by the resolvconf package, if installed
#	 dns-nameservers 8.8.8.8 8.8.8.4
#	 dns-search sr.local

auto ra0
iface ra0 inet dhcp
         # address 192.168.0.7
         # netmask 255.255.255.0
         # network 192.168.0.0
         # broadcast 192.168.0.255
         # gateway 192.168.0.254
         # dns-nameservers 8.8.8.8 8.8.8.4
         # Begin Needed
         wpa-ssid linksys
         wpa-psk <WPA key removed>
         # wpa-ap-scan 1
         # wpa-proto WPA
         # wpa-pairwise TKIP
         # wpa-group TKIP
         # wpa-key-mgmt WPA-PSK
         # End Needed

# Not needed        pre-up wpa_supplicant -Bw -Dwext -ira0 -c/etc/wpa_supplicant.conf
# Not needed        post-down killall -q wpa_supplicant


**** iwlist ****


ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-61 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"ARRIS-D752"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-61 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11g/n
                    ESSID:"championdiver"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-86 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.8.4


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
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2x00usb



**** dmesg ****


[   11.296496] wmi: Mapper loaded
[   11.922584] rt3562sta: module license 'unspecified' taints kernel.
[   11.925408] ===> rt2860_probe
[   11.925431] rt2860 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.926343] @rt2860_probe MAC address: <MAC address removed>
[   11.926344] <=== rt2860_probe
[   12.201237] NICReadEEPROMParameters: RxPath = 2, TxPath = 2
[   12.240946] TxPath = 2, RxPath = 2, RFIC=8, Polar+LED mode=1
[   12.240973] <==== rt28xx_init, Status=0
[   12.254776] AsicRemovePairwiseKeyEntry : Wcid #1 
[   12.254792] AsicRemovePairwiseKeyEntry : Wcid #1 
[   12.254806] AsicRemovePairwiseKeyEntry : Wcid #1 
[   12.254821] AsicRemovePairwiseKeyEntry : Wcid #1 
[   12.254835] AsicRemovePairwiseKeyEntry : Wcid #1 
[   12.254851] AsicRemovePairwiseKeyEntry : Wcid #1 
[   14.023094] AsicRemovePairwiseKeyEntry : Wcid #1 
[   32.034171] rt28xx_get_wireless_stats --->
[   32.034173] <--- rt28xx_get_wireless_stats


**************** done ********************



```

---

