---
title: "ubuntu 10.04 wireless not connecting."
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by Sorrow7 on 2012-02-26
Ok so ive started a new thread from [this one]("http://ubuntuforums.org/showthread.php?t=1931845") as its a new problem.

I am using ubuntu 10.04 (recently upgraded from 8.04) and my wireless is run by 'network manager applet 8.0'.


The problem is, i click connect, it tries to connect for around a minute and then brings up the connection screen again. It does connect sometimes for around 30secs but is useless and drops out. 

any help is greatly appreciated.

---

### Post by Bucky Ball on 2012-02-26
Have you plugged in an ethernet cable and gotten all updates? Try that then check 'Additional Drivers' (or possibly 'Hardware Drivers').

---

### Post by Sorrow7 on 2012-02-26
Ive done all the updates. How do i check for hardware or additional drivers?

---

### Post by Bucky Ball on 2012-02-27
System>Administration>Additional Drivers (or could be 'Hardware Drivers').

---

### Post by Sorrow7 on 2012-02-27
ok found it and it came up as not activte, i plugged in my ethernet cable and activated it. its now active and in use, however wireless networks is just showing as disconnected and not giving me any local networks to connect to. 

I have tried rebooting etc.

mark@mark-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

signal level:0  << is this the problem?

---

### Post by Bucky Ball on 2012-02-27
Have you tried putting the router details into Network Manager directly? E.g. ESSID (router or access point name) DNS servers and static IP address if you are using one? Then reboot ...

---

### Post by Sorrow7 on 2012-02-27
just tried, doesnt do anything.

---

### Post by Sorrow7 on 2012-03-01
Bumping this in the response for more possible help. 

Most recent readouts. 

```
mark@mark-netbook:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl, ssb
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169


mark@mark-netbook:~$ lsusb
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 002: ID 0c45:63e4 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


mark@mark-netbook:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            40033  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33453  4 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
sco                     7949  2 
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
bridge                 45646  0 
stp                     1655  1 bridge
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
dell_wmi                1793  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bnep                    9436  2 
i915                  289715  3 
l2cap                  30656  16 rfcomm,bnep
lib80211_crypt_tkip     7596  0 
compal_laptop           2034  0 
uvcvideo               57438  0 
jmb38x_ms               7311  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 i915
dcdbas                  5422  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
wl                   1959598  0 
drm                   163747  4 i915,drm_kms_helper
soundcore               6620  1 snd
intel_agp              24375  2 i915
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
memstick                8237  1 jmb38x_ms
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  1 sdhci
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169


mark@mark-netbook:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: compal-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: compal-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


mark@mark-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.


mark@mark-netbook:~$ sudo iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0B:0E:37:88:08
                    ESSID:"isrc"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0B:0E:37:88:0A
                    ESSID:"Student"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:0B:0E:37:88:0C
                    ESSID:"Staff"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-65 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:0B:0E:37:88:0E
                    ESSID:"Visitor"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-76 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:0B:0E:37:88:00
                    ESSID:"dmz"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-65 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:0B:0E:37:88:02
                    ESSID:"eng_j"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:0B:0E:37:88:06
                    ESSID:"bio-register"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-76 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:0B:0E:37:B0:4A
                    ESSID:"Student"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-76 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 09 - Address: 02:28:78:F3:95:EF
                    ESSID:"HP4F8202"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-60 dBm  Noise level:-88 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 10 - Address: 00:0B:0E:37:88:04
                    ESSID:""
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 11 - Address: 00:0B:0E:61:D8:00
                    ESSID:"dmz"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-88 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:0B:0E:61:D8:04
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 13 - Address: 00:0B:0E:61:D8:08
                    ESSID:"isrc"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 14 - Address: 00:0B:0E:61:D8:0C
                    ESSID:"Staff"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 15 - Address: 00:0B:0E:37:9F:82
                    ESSID:"eng_j"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 16 - Address: 00:0B:0E:37:9F:86
                    ESSID:"bio-register"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 17 - Address: 00:0B:0E:37:85:00
                    ESSID:"dmz"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-34 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 18 - Address: 00:0B:0E:37:85:02
                    ESSID:"eng_j"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-33 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 19 - Address: 00:0B:0E:37:85:06
                    ESSID:"bio-register"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-32 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 20 - Address: 00:0B:0E:37:85:08
                    ESSID:"isrc"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-33 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 21 - Address: 00:0B:0E:37:85:0A
                    ESSID:"Student"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 22 - Address: 00:0B:0E:37:85:0C
                    ESSID:"Staff"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 23 - Address: 00:0B:0E:37:85:0E
                    ESSID:"Visitor"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s

pan0      Interface doesn't support scanning.

```

---

