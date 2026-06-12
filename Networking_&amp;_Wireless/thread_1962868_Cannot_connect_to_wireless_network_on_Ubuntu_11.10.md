---
title: "Cannot connect to wireless network on Ubuntu 11.10"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by reznorsoft on 2012-04-21
I need some help please. I've recently installed Ubuntu 11.10 on my Dell Studio 1537. As yet I've been unable to connect to the internet. I've tried some of the suggestions mentioned in other threads on this forum but without any success. 
From what I can tell, mind you I'm new to Linux, my wireless card is detected and working fine, I can see my network from a list of available networks, but I simply cannot connect to it to get online. 
My wireless card is a .. Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
 
I'm posting the output of 'iwconfig' below. I'm not sure what to make of the "access point not associated", but maybe that is the problem.
 
reznorsoft@Studio-1537:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
eth2 IEEE 802.11 **Access Point: Not-Associated** 
Link Quality:5 Signal level:0 Noise level:234
Rx invalid nwid:0 invalid crypt:0 invalid misc:0
 
Your help would be greatly appreciated.
Thanks.

---

### Post by wildmanne39 on 2012-04-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by reznorsoft on 2012-04-21
Hi wildmanne39, thank you for taking the time to lend your assistance.
 
```

reznorsoft@Studio-1537:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Studio-1537 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```
 
```

reznorsoft@Studio-1537:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
Kernel driver in use: wl
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
Subsystem: Dell Device [1028:029f]
Kernel driver in use: tg3

```
 
```

reznorsoft@Studio-1537:~$ rfkill list all
0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no

```
 
```

reznorsoft@Studio-1537:~$ lsmod
Module Size Used by
parport_pc 32114 0 
ppdev 12849 0 
bnep 17923 2 
rfcomm 38408 0 
bluetooth 148839 10 bnep,rfcomm
snd_hda_codec_hdmi 31426 1 
snd_hda_codec_idt 60049 1 
joydev 17393 0 
dell_wmi 12601 0 
sparse_keymap 13658 1 dell_wmi
uvcvideo 67271 0 
snd_hda_intel 24262 2 
snd_hda_codec 91754 3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep 13276 1 snd_hda_codec
snd_pcm 80468 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev 85626 1 uvcvideo
snd_seq_midi 13132 0 
snd_rawmidi 25241 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
dell_laptop 13519 0 
dcdbas 14098 1 dell_laptop
lib80211_crypt_tkip 17240 0 
wl 2646601 0 
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
r852 17901 0 
sm_common 16737 1 r852
nand 49707 2 r852,sm_common
nand_ids 8547 1 nand
nand_bch 13003 1 nand
bch 21757 1 nand_bch
nand_ecc 13070 1 nand
snd 55902 14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse 73673 0 
serio_raw 12990 0 
mtd 35852 2 sm_common,nand
binfmt_misc 17292 1 
i915 505108 3 
ir_lirc_codec 12770 0 
lirc_dev 18700 1 ir_lirc_codec
lib80211 14570 2 lib80211_crypt_tkip,wl
soundcore 12600 1 snd
snd_page_alloc 14115 2 snd_hda_intel,snd_pcm
ir_sony_decoder 12493 0 
drm_kms_helper 32889 1 i915
drm 192226 4 i915,drm_kms_helper
ir_jvc_decoder 12490 0 
wmi 18744 1 dell_wmi
i2c_algo_bit 13199 1 i915
ir_rc6_decoder 12490 0 
ir_rc5_decoder 12490 0 
rc_rc6_mce 12454 0 
ir_nec_decoder 12490 0 
ite_cir 24743 0 
rc_core 25797 9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
video 18908 1 i915
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp
firewire_ohci 35854 0 
firewire_core 56937 1 firewire_ohci
crc_itu_t 12627 1 firewire_core
sdhci_pci 13658 0 
sdhci 27360 1 sdhci_pci
ahci 21634 3 
libahci 25727 1 ahci
tg3 132972 0 

```

---

### Post by wildmanne39 on 2012-04-21
Hi, please post the output from:
```
nm-tool
sudo iwlist scan
lsmod | grep wl
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth2 -e etork | tail -n55
```
Thanks

---

### Post by reznorsoft on 2012-04-21
Hi, wildmanne39. Thanks for your continued support.
 
```

reznorsoft@Studio-1537:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: eth2 -----------------------------------------------------------------
Type: 802.11 WiFi
Driver: wl
State: disconnected
Default: no
HW Address: 00:24:2B:3F:D5:7E
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
DD-Infected: Infra, 78:CD:8E:6E:24:31, Freq 2462 MHz, Rate 0 Mb/s, Strength 20 WPA WPA2
Aeon's Network: Infra, 10:9A:DD:85:D6:55, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA2
CoM-S: Infra, B4:14:89:F5:46:00, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
SmallWillow-guest: Infra, 3A:60:77:07:3B:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
grimshouse1: Infra, 00:26:5A:F7:0F:C8, Freq 2462 MHz, Rate 0 Mb/s, Strength 19 WPA
Dogfight: Infra, 00:26:F3:26:94:C9, Freq 2442 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
rehatta: Infra, 00:1C:F0:F6:37:E2, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
Annabelle: Infra, 00:22:2D:16:4F:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
linksys: Infra, C0:C1:C0:01:99:5A, Freq 2447 MHz, Rate 54 Mb/s, Strength 30
BELL518: Infra, 3C:EA:4F:BC:A1:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
BELL227: Infra, 00:25:3C:51:FF:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
BELL098: Infra, 00:24:56:B4:B8:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WEP
Hilltop: Infra, 00:22:2D:1C:D6:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA
starwars: Infra, 68:7F:74:09:37:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
Bell999: Infra, 00:22:2D:18:52:A1, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA
WLAN: Infra, 00:13:F7:F2:4D:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
402: Infra, 00:22:2D:1C:CC:C3, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
&#12288;
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: tg3
State: unavailable
Default: no
HW Address: 00:22:19:DF:C9:FC
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off

```
 
```

reznorsoft@Studio-1537:~$ sudo iwlist scan
[sudo] password for reznorsoft: 
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
eth2 Scan completed :
Cell 01 - Address: 00:1C:F0:F6:37:E2
ESSID:"rehatta"
Mode:Managed
Frequency:2.417 GHz (Channel 2)
Quality:1/5 Signal level:-88 dBm Noise level:-92 dBm
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD0E0050F204104A0001101044000102
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Cell 02 - Address: 00:25:3C:51:FF:B9
ESSID:"BELL227"
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:2/5 Signal level:-72 dBm Noise level:-92 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Cell 03 - Address: 00:24:56:B4:B8:89
ESSID:"BELL098"
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:2/5 Signal level:-70 dBm Noise level:-92 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Cell 04 - Address: C0:C1:C0:01:99:5A
ESSID:"linksys"
Mode:Managed
Frequency:2.447 GHz (Channel 8)
Quality:2/5 Signal level:-78 dBm Noise level:-92 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Cell 05 - Address: 78:CD:8E:6E:24:31
ESSID:"DD-Infected"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:1/5 Signal level:-88 dBm Noise level:-88 dBm
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
24 Mb/s; 48 Mb/s
Cell 06 - Address: 00:22:2D:1C:CC:C3
ESSID:"402"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:5/5 Signal level:-37 dBm Noise level:-89 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Cell 07 - Address: B4:14:89:F5:96:00
ESSID:"CoM-S"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:1/5 Signal level:-88 dBm Noise level:-92 dBm
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : 802.1x
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Cell 08 - Address: 00:22:2D:1C:D6:35
ESSID:"Hilltop"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:4/5 Signal level:-58 dBm Noise level:-89 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Cell 09 - Address: 00:26:5A:F7:0F:C8
ESSID:"grimshouse1"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:1/5 Signal level:-88 dBm Noise level:-89 dBm
IE: Unknown: DD0E0050F204104A0001101044000102
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s

```
 
```

reznorsoft@Studio-1537:~$ lsmod | grep wl
wl 2646601 0 
lib80211 14570 2 lib80211_crypt_tkip,wl

```
 
```

reznorsoft@Studio-1537:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth2 -e etork | tail -n55
Apr 21 17:36:59 Studio-1537 kernel: [ 14.179483] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 21 17:36:59 Studio-1537 kernel: [ 14.374342] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 21 17:36:59 Studio-1537 kernel: [ 14.374354] wl 0000:04:00.0: setting latency timer to 64
Apr 21 17:37:00 Studio-1537 NetworkManager[614]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 21 17:37:00 Studio-1537 NetworkManager[614]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr 21 17:37:00 Studio-1537 dbus[545]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Apr 21 17:37:00 Studio-1537 dbus[545]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Apr 21 17:37:00 Studio-1537 wpa_supplicant[766]: nl80211: 'nl80211' generic netlink not found
Apr 21 17:37:00 Studio-1537 udevd[383]: error changing net interface name eth1 to eth2: Device or resource busy
Apr 21 17:37:00 Studio-1537 NetworkManager[614]: <info> wpa_supplicant started
Apr 21 18:50:18 Studio-1537 kernel: [ 13.911035] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 21 18:50:18 Studio-1537 kernel: [ 13.960771] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 21 18:50:18 Studio-1537 kernel: [ 13.960782] wl 0000:04:00.0: setting latency timer to 64
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/eth2/rfkill0) (driver (unknown))
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <error> [1335048619.141336] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (eth2): unable to read permanent MAC address (error 0)
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): driver supports SSID scans (scan_capa 0x01).
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): now managed
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): bringing up device.
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): preparing device.
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): deactivating device (reason 'managed') [2]
Apr 21 18:50:19 Studio-1537 dbus[642]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Apr 21 18:50:19 Studio-1537 dbus[642]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Apr 21 18:50:19 Studio-1537 wpa_supplicant[893]: nl80211: 'nl80211' generic netlink not found
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/eth2, iface: eth2)
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/eth2, iface: eth2): no ifupdown configuration found.
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> wpa_supplicant started
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): supplicant interface state: starting -> ready
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 21 18:50:19 Studio-1537 NetworkManager[700]: <info> (eth2): supplicant interface state: ready -> inactive
Apr 21 18:50:20 Studio-1537 avahi-daemon[657]: Joining mDNS multicast group on interface eth2.IPv6 with address fe80::224:2bff:fe3f:d57e.
Apr 21 18:50:20 Studio-1537 avahi-daemon[657]: New relevant interface eth2.IPv6 for mDNS.
Apr 21 18:50:20 Studio-1537 avahi-daemon[657]: Registering new address record for fe80::224:2bff:fe3f:d57e on eth2.*.
Apr 21 18:50:29 Studio-1537 kernel: [ 25.040035] eth2: no IPv6 routers present

```
 
Thanks again.

---

### Post by wildmanne39 on 2012-04-21
Hi, is 402 the network you are trying to connect too? network manager can not connect to just numbers as a network name it needs to be changed.

If this is the network I recommend changing your encryption in your router to wpa2 if possible it works better.
Thanks

---

### Post by reznorsoft on 2012-04-21
Correct, the network which I'm trying to connect to is 402. Is that all it would take, simply renaming it?
 
> If this is the network I recommend changing your encryption in your router to wpa2 if possible it works better.
Is there a guide in these forums that would tell me how to do that?

---

### Post by wildmanne39 on 2012-04-21
Hi, that is one problem for sure.

Did you set up your wireless manually instead of letting network manager do it for you?

Did you make a permanent mac address?

> Is there a guide in these forums that would tell me how to do that? No, do as I said in my last post and when you are in your router settings just look around and you will find the place to change your encryption and you network name for your wireless in wireless settings.
Thanks

I recommend clicking on internet icon in the top right corner and delete your wireless connection then reboot and let network manager find your connection then just enter your encryption key.

---

### Post by reznorsoft on 2012-04-21
> **wildmanne39 said:**
> Hi, is 402 the network you are trying to connect too? network manager can not connect to just numbers as a network name it needs to be changed.

If this is the network I recommend changing your encryption in your router to wpa2 if possible it works better.
Thanks
Never in my life would it have occurred to me that having just numbers in my network name could cause connection problems. I've renamed it and it now works like a charm.

I'll look into changing the encryption to wpa2. You are a lifesaver, wildmanne39. Thank you so much.

---

### Post by wildmanne39 on 2012-04-21
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

