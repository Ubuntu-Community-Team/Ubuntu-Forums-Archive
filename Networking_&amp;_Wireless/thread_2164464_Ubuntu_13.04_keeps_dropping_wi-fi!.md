---
title: "Ubuntu 13.04 keeps dropping wi-fi!"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by heather-mcfar on 2013-07-31
Hi all
First time post here... I am running Ubuntu 13.04 on a Toshiba laptop. After two or so updates, the wi-fi continually drops! I can disconnect and reconnect but this happens at least 10 times an hour. What do I need to check? 
Any help would be greatly appreciated! 
I am semi-new to Ubuntu but have worked on previous linux versions...

---

### Post by praseodym on 2013-07-31
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by heather-mcfar on 2013-07-31
Here you go:
heather@librede-laptop:~```
$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Toshiba America Info Systems Device [1179:fb46]
Kernel driver in use: r8169
heather@librede-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Toshiba America Info Systems Device [1179:fb46]
Kernel driver in use: r8169
heather@librede-laptop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 003: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd 
heather@librede-laptop:~$ lsmod
Module Size Used by
vboxpci 23194 0 
vboxnetadp 25670 0 
vboxnetflt 23479 0 
vboxdrv 320372 3 vboxnetadp,vboxnetflt,vboxpci
btrfs 785967 0 
zlib_deflate 26885 1 btrfs
ufs 74597 0 
qnx4 13317 0 
hfsplus 88539 0 
hfs 54503 0 
minix 36072 0 
ntfs 96967 0 
msdos 17332 0 
jfs 185045 0 
xfs 869166 0 
libcrc32c 12615 2 xfs,btrfs
reiserfs 241608 0 
ext2 72837 0 
ums_realtek 17949 0 
usb_storage 57204 1 ums_realtek
pci_stub 12622 1 
parport_pc 28152 0 
ppdev 17073 0 
binfmt_misc 17500 1 
bnep 18036 2 
rfcomm 42641 0 
bluetooth 228619 10 bnep,rfcomm
snd_hda_codec_hdmi 36913 1 
snd_hda_codec_realtek 78399 1 
coretemp 13355 0 
kvm_intel 132891 0 
arc4 12615 2 
kvm 443165 1 kvm_intel
snd_hda_intel 39619 3 
rtl8192ce 53594 0 
ghash_clmulni_intel 13259 0 
rtlwifi 79673 1 rtl8192ce
snd_hda_codec 136453 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
i915 600396 4 
cryptd 20373 1 ghash_clmulni_intel
rtl8192c_common 48779 1 rtl8192ce
snd_hwdep 13602 1 snd_hda_codec
mac80211 606457 3 rtlwifi,rtl8192c_common,rtl8192ce
snd_pcm 97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
cfg80211 510937 2 mac80211,rtlwifi
snd_seq_midi 13324 0 
snd_seq_midi_event 14899 1 snd_seq_midi
snd_rawmidi 30180 1 snd_seq_midi
snd_seq 61554 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper 49394 1 i915
psmouse 95870 0 
drm 286028 5 i915,drm_kms_helper
sparse_keymap 13890 0 
snd_timer 29425 2 snd_pcm,snd_seq
serio_raw 13215 0 
joydev 17377 0 
snd 68876 16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
uvcvideo 80847 0 
lpc_ich 17061 0 
lp 17759 0 
videobuf2_vmalloc 13056 1 uvcvideo
videobuf2_memops 13202 1 videobuf2_vmalloc
videobuf2_core 40513 1 uvcvideo
hid_generic 12540 0 
mac_hid 13205 0 
soundcore 12680 1 snd
i2c_algo_bit 13413 1 i915
mei 41158 0 
videodev 129260 2 uvcvideo,videobuf2_core
usbhid 47074 0 
hid 101002 2 hid_generic,usbhid
parport 46345 3 lp,ppdev,parport_pc
wmi 19070 0 
microcode 22881 0 
video 19390 1 i915
r8169 67446 0 
ahci 25731 2 
libahci 31364 1 ahci
heather@librede-laptop:~$ iwconfig
eth0 no wireless extensions.


lo no wireless extensions.


wlan0 IEEE 802.11bgn ESSID:"UCLA_WEB" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:1A:1E:1E:1C:42 
Bit Rate=72.2 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr=2347 B Fragment thr:off
Power Management:off
Link Quality=58/70 Signal level=-52 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:38 Missed beacon:0


heather@librede-laptop:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
heather@librede-laptop:~$ sudo iwlist scan
[sudo] password for heather: 
eth0 Interface doesn't support scanning.


lo Interface doesn't support scanning.


wlan0 Scan completed :
Cell 01 - Address: 00:1A:1E:1E:1C:42
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=48/70 Signal level=-62 dBm 
Encryption key:off
ESSID:"UCLA_WEB"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000a4d9d262ba
Extra: Last beacon: 8288ms ago
IE: Unknown: 000855434C415F574542
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 02 - Address: 00:1A:1E:1F:34:A1
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=48/70 Signal level=-62 dBm 
Encryption key:off
ESSID:"UCLA_WIFI"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374b7cdb8e
Extra: Last beacon: 8288ms ago
IE: Unknown: 000955434C415F57494649
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 03 - Address: 00:1A:1E:1F:34:A2
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=50/70 Signal level=-60 dBm 
Encryption key:off
ESSID:"UCLA_WEB"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374bf2bc7e
Extra: Last beacon: 1456ms ago
IE: Unknown: 000855434C415F574542
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 04 - Address: 00:1A:1E:1F:34:A4
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=50/70 Signal level=-60 dBm 
Encryption key:off
ESSID:"MEDPDA"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374bf2be06
Extra: Last beacon: 1456ms ago
IE: Unknown: 00064D4544504441
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 05 - Address: 00:1A:1E:1F:34:A5
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=47/70 Signal level=-63 dBm 
Encryption key:off
ESSID:""
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374b7cb592
Extra: Last beacon: 9192ms ago
IE: Unknown: 0000
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030101
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 06 - Address: 00:1A:1E:1F:34:A6
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=51/70 Signal level=-59 dBm 
Encryption key:on
ESSID:"UCLA_VOIP"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374bf2bf8f
Extra: Last beacon: 1452ms ago
IE: Unknown: 000955434C415F564F4950
IE: Unknown: 010882840B0C12161824
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : 802.1x
IE: Unknown: DD0A00037F04010000000000
Cell 07 - Address: 00:1A:1E:1F:34:A7
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=51/70 Signal level=-59 dBm 
Encryption key:on
ESSID:"eduroam"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000374bf2c4ff
Extra: Last beacon: 1452ms ago
IE: Unknown: 0007656475726F616D
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : 802.1x
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 08 - Address: 00:1A:1E:1E:1C:46
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=51/70 Signal level=-59 dBm 
Encryption key:on
ESSID:"UCLA_VOIP"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000a4da4cb812
Extra: Last beacon: 812ms ago
IE: Unknown: 000955434C415F564F4950
IE: Unknown: 010882840B0C12161824
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : 802.1x
IE: Unknown: DD0A00037F04010000000000
Cell 09 - Address: 00:1A:1E:1E:1C:44
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=48/70 Signal level=-62 dBm 
Encryption key:off
ESSID:"MEDPDA"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000a4d9d26444
Extra: Last beacon: 8288ms ago
IE: Unknown: 00064D4544504441
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 10 - Address: 00:1A:1E:1E:1C:47
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=48/70 Signal level=-62 dBm 
Encryption key:on
ESSID:"eduroam"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000a4d9d26a36
Extra: Last beacon: 8288ms ago
IE: Unknown: 0007656475726F616D
IE: Unknown: 01088C1298243048606C
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : 802.1x
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD0A00037F04010000000000
Cell 11 - Address: 00:11:50:64:51:31
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=50/70 Signal level=-60 dBm 
Encryption key:on
ESSID:"EICN"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000012355977ee
Extra: Last beacon: 172ms ago
IE: Unknown: 00044549434E
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: Unknown: 32040C121860
IE: Unknown: DD06001018020004
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
```
Thanks!

---

### Post by wildmanne39 on 2013-07-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2013-08-01
> ```
wlan0 IEEE 802.11bgn ESSID:"[COLOR="#FF0000"]UCLA_WEB[/COLOR]" 
```
There are more than one APs with UCLA_WEB, one on channel 6 (Cell 01) and one on channel 1 (Cell 03). Add the respective MAC-address of the cell into the field BSSID of the network-manager profile

---

### Post by heather-mcfar on 2013-08-02
So I made those changes and it seemed to last about a day. This morning it started the nasty wi-fi dropping again. I went to check the system settings and noticed that the BSSID field was empty. I went back and made the same changes as before. Is there a permanent fix for this?

Thanks

---

### Post by mchid2 on 2013-08-27
I have a Toshiba Satellite with the same problem in 13.04. 13.10 seems to be a whole lot better. You can download here [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) if you want to check it out. I did a clean install with the Gnome variant and I installed Unity using the apt-get ubuntu-desktop. Gnome is here [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/).
To get more of a permanent setting, you can edit the network configuration file found in the  /etc/NetworkManager/system-connections directory. 
Using . . .
```
gksudo nautilus /etc/NetworkManager/system-connections
```
If you see more than one instance of the same file, this may be your problem; It's best to only have one.
However, right click on the file named after the connection you are using and choose to open it with "gedit". 

The BEGINING of my file is set up like this (so you know where to insert the BSSID). The BSSID is listed twice.

[connection] 
id=
uuid=
type=802-11-wireless
timestamp=


[802-11-wireless]
ssid=
mode=infrastructure
**bssid**=
mac-address=
**seen-bssids**=    ;
security=

Just insert your . . . 
```
bssid=
```
and
```
seen-bssids=   ;
```
in the file, with a semicolon after the last one. Click save before you close gedit.
```
sudo service network-manager restart
``` will restart network manager



Good Luck!

---

