---
title: "D-link DWA-131 N Adapter on Ubuntu"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Atticus8631 on 2011-10-23
[LEFT] So I read Chili5555's explanation on getting this to work and it was very helpful, however it only got me so far.  My laptop has built-in wireless but I'm trying to get wireless N on my laptop so that I can stream to my  Windows HTPC in my living room.  Is there any way you could help me get  the N feature to work?  Here's some basic info about my system.  Any  help would be greatly appreciated.
Thanks so much!

kernel 2.6.32-34-generic
gnome 2.30.2

blake@Ruiner:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid
blake@Ruiner:~$ sudo modprobe r8192s_usb
[sudo] password for blake: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
blake@Ruiner:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SuperAwesome"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:grin:1:C3:44:7A   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

blake@Ruiner:~$ 




kernel 2.6.32-34-generic
gnome 2.30.2[/LEFT]

---

### Post by praseodym on 2011-10-24
Hi,

which devices are there? Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```
Do you use ndiswrapper? If not, remove it and its config completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

---

### Post by Atticus8631 on 2011-10-24
blake@Ruiner:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
    Kernel driver in use: sky2
    Kernel modules: sky2
06:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
blake@Ruiner:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3303 D-Link System 
Bus 001 Device 004: ID 0bc2:50a1 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
blake@Ruiner:~$ lsmod
Module                  Size  Used by
xt_tcpudp               2011  2 
nf_conntrack_ipv4      10346  2 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
xt_state                1098  2 
nf_conntrack           60943  2 nf_conntrack_ipv4,xt_state
xt_mark                  711  4 
xt_NFQUEUE              1832  2 
nfnetlink_queue         6820  2 
ipt_REJECT              1928  2 
nfnetlink               3266  3 nfnetlink_queue
ndiswrapper           184677  0 
nls_utf8                1069  1 
isofs                  29250  1 
usb_storage            39841  1 
aes_i586                7268  3 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          1369  1 
pcmcia                 30784  0 
ip_tables               9899  1 iptable_filter
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               14175  6 xt_tcpudp,xt_state,xt_mark,xt_NFQUEUE,ipt_REJECT,ip_tables
arc4                    1153  2 
joydev                  8740  0 
i915                  288963  3 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   163556  0 
sdhci_pci               5470  0 
yenta_socket           20408  1 
drm_kms_helper         29329  1 i915
usbhid                 36110  0 
tifm_7xx1               3690  0 
mac80211              205402  1 b43
rsrc_nonstatic         10015  1 yenta_socket
sdhci                  15494  1 sdhci_pci
intel_agp              24375  2 i915
soundcore               6620  1 snd
drm                   163651  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
hid                    67288  1 usbhid
tifm_core               6045  1 tifm_7xx1
r8192s_usb            346908  0 
psmouse                63677  0 
serio_raw               3978  0 
cfg80211              126112  2 b43,mac80211
led_class               2864  2 b43,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
sky2                   40807  0 
blake@Ruiner:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SuperAwesome"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:D1:C3:44:7A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

blake@Ruiner:~$ sudo modprobe -rf ndiswrapper
[sudo] password for blake: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
blake@Ruiner:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ndisgtk* ndiswrapper-common* ndiswrapper-utils-1.9*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 1,110kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 328472 files and directories currently installed.)
Removing ndisgtk ...
Purging configuration files for ndisgtk ...
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
blake@Ruiner:~$ sudo rm /etc/modprobe.d/ndiswrapper
blake@Ruiner:~$ 
blake@Ruiner:~$ sudo rm -r /etc/ndiswrapper/* 
blake@Ruiner:~$ sudo depmod -a


Here's what I got, I had installed ndiswrapper earlier when I first started this but don't use it aside from that.

---

### Post by praseodym on 2011-10-25
You only need to copy the firmware to the right place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
sudo modprobe r8192s_usb
```

---

### Post by Atticus8631 on 2011-10-28
blake@Ruiner:~$ sudo mkdir /lib/firmware/RTL8192SU
[sudo] password for blake: 
mkdir: cannot create directory `/lib/firmware/RTL8192SU': File exists
blake@Ruiner:~$ sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
blake@Ruiner:~$ sudo modprobe r8192s_usb
blake@Ruiner:~$

---

### Post by praseodym on 2011-10-28
Replug the stick and check:

```
iwconfig
dmesg | egrep 'rtl8|r8'
sudo iwlist scan
rfkill list
lsmod
iwlist chan
```

---

### Post by Atticus8631 on 2011-10-28
blake@Ruiner:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SuperAwesome"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:D1:C3:44:7A   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     802.11b/g/n  li  ESSID:"SuperAwesome"  
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:14:D1:C3:44:7A   
          Bit Rate=300 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

blake@Ruiner:~$

---

### Post by Atticus8631 on 2011-10-28
blake@Ruiner:~$ dmesg | egrep 'rtl8|r8'
[   21.849186] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   22.710824] usbcore: registered new interface driver rtl819xU
[21913.449726] Modules linked in: aes_i586 aes_generic nls_utf8 isofs binfmt_misc ppdev iptable_filter ip_tables x_tables fbcon tileblit font bitblit softcursor vga16fb vgastate snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss pcmcia snd_pcm arc4 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev b43 snd i915 yenta_socket mac80211 drm_kms_helper tifm_7xx1 rsrc_nonstatic r8192s_usb(C) usbhid intel_agp sdhci_pci soundcore cfg80211 drm i2c_algo_bit hid tifm_core psmouse serio_raw pcmcia_core sdhci video led_class snd_page_alloc output agpgart lp parport ohci1394 usb_storage ssb ieee1394 sky2
[21913.449877]  [<f85982af>] rtl8192_usb_disconnect+0x20/0xa7 [r8192s_usb]
[21913.450023]  [<f85982af>] rtl8192_usb_disconnect+0x20/0xa7 [r8192s_usb]
[21913.450114] rtl819xU:=============>wlan driver to be removed
[21913.474272] rtl819xU:wlan driver removed
[21919.016096] rtl819xU: --->FirmwareDownload92S()
[21919.016107] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[21919.019081] rtl819xU:signature:8192, version:703e, size:30, imemsize:b408, sram size:87c8
[21919.019151] rtl819xU:--->FirmwareDownloadCode()
[21919.019207] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[21919.024770] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[21919.024777] rtl819xU:--->FirmwareDownloadCode()
[21919.024829] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[21919.026388] rtl819xU:-->FirmwareEnableCPU()
[21919.030610] rtl819xU:IMEM Ready after CPU has refilled.
[21919.030617] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[21919.030622] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[21919.030627] rtl819xU:--->FirmwareDownloadCode()
[21919.030635] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[21919.032193] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[21919.032394] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[21919.033346] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[21919.033463] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[21919.033468] rtl819xU:Firmware Download Success!!
[21942.419857] =====>rtl8192SU_link_change 1
[21942.421181] <=====rtl8192SU_link_change 2
[21942.477636] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[21942.524113] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[21942.527615] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[21942.527630] rtl819xU:qos active process with associate response received
[21942.584895] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[21942.666990] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[21942.667006] =====>rtl8192SU_link_change 1
[21942.687617] <=====rtl8192SU_link_change 2
[21945.529483] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:4, SECR_value:c
[21945.529706] rtl819xU:====>to setKey(), dev:f34f8000, EntryNo:4, KeyIndex:0, KeyType:4, MacAddr00:14:d1:c3:44:7a
[21945.537888] rtl819xU:====>to setKey(), dev:f34f8000, EntryNo:2, KeyIndex:2, KeyType:4, MacAddrff:ff:ff:ff:ff:ff
[21972.194879] =====>rtl8192SU_link_change 1
[21972.196250] <=====rtl8192SU_link_change 2
[21972.203644] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[21972.218516] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[21973.979798] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[21974.011098] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[21974.022231] =====>rtl8192SU_link_change 1
[21974.033235] <=====rtl8192SU_link_change 2
[22012.198135] =====>rtl8192SU_link_change 1
[22012.199659] <=====rtl8192SU_link_change 2
[22012.209928] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[22012.224933] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22013.977083] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[22014.004015] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22014.019891] =====>rtl8192SU_link_change 1
[22014.031020] <=====rtl8192SU_link_change 2
[22054.428539] =====>rtl8192SU_link_change 1
[22054.430169] <=====rtl8192SU_link_change 2
[22054.440155] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[22054.454631] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22056.220185] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[22056.266914] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22056.274245] =====>rtl8192SU_link_change 1
[22056.286505] <=====rtl8192SU_link_change 2
[22072.162084] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[22072.197873] =====>rtl8192SU_link_change 1
[22072.204037] <=====rtl8192SU_link_change 2
[22072.211233] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[22072.232240] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22074.006904] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[22074.041969] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22074.048845] =====>rtl8192SU_link_change 1
[22074.059336] <=====rtl8192SU_link_change 2
[22152.193912] =====>rtl8192SU_link_change 1
[22152.195050] <=====rtl8192SU_link_change 2
[22152.203680] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[22152.220806] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22154.010101] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[22154.044278] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22154.049903] =====>rtl8192SU_link_change 1
[22154.061409] <=====rtl8192SU_link_change 2
[22194.162127] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
[22252.199592] =====>rtl8192SU_link_change 1
[22252.201213] <=====rtl8192SU_link_change 2
[22252.208722] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[22252.224351] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22254.002495] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[22254.039054] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[22254.047405] =====>rtl8192SU_link_change 1
[22254.060897] <=====rtl8192SU_link_change 2
blake@Ruiner:~$

---

### Post by Atticus8631 on 2011-10-28
F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363135100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 02 - Address: 00:1F:B3:46:19:C9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption keyn
                    ESSID:"2WIRE711"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000125af052181
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 00083257495245373131
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 00:141:C3:44:7A
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption keyn
                    ESSID:"SuperAwesome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029824d14981
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 000C5375706572417765736F6D65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340707070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160707030000000F000000000000000000000000000000
                    IE: Unknown: DD780050F204104A0001101044000102103B0001031047001037E164B8876030388D4C552AFFA4A78E102100085452454E446E65741023000A5445572D363331425250102400024131104200046E6F6E651054000800060050F204000110110013576972656C6573732031316E20526F75746572100800020004
          Cell 04 - Address: C4:3D:C7:4A:B6:39
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption keyn
                    ESSID:"palace"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f4fb55186
                    Extra: Last beacon: 1856ms ago
                    IE: Unknown: 000670616C616365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700109917A4BDE3D18067EAD7341CC3364B3A1021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 05 - Address: 00:14:A5:93:934
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption keyn
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000045250d41337
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: DD07000C4301000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 06 - Address: F8:1EF:FD:6B:65
                    Channel:8
                    Frequency:2.447 GHz (Channel 
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption keyn
                    ESSID:"Virus Upload"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bb83af0716
                    Extra: Last beacon: 1080ms ago
                    IE: Unknown: 000C56697275732055706C6F6164
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1700039301710120000EF81EDFFD6B6508F81EDFFD6B669D
                    IE: Unknown: DD070017F203020180
          Cell 07 - Address: 90:84:0D4:F4:F5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption keyn
                    ESSID:"Apple Network d4f4f5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e1b101b160
                    Extra: Last beacon: 1384ms ago
                    IE: Unknown: 00144170706C65204E6574776F726B20643466346635
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
                    IE: Unknown: DD1700039301710120000E90840DD4F4F50B90840DD4F4F695
                    IE: Unknown: DD070017F203020180
          Cell 08 - Address: 00:21:29:B0:4A:F3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption keyn
                    ESSID:"HALES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000044333a8183
                    Extra: Last beacon: 988ms ago
                    IE: Unknown: 000548414C4553
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 09 - Address: 00:1C:10:8C:6E:B7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption keyn
                    ESSID:"Vallen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d1a37b186
                    Extra: Last beacon: 948ms ago
                    IE: Unknown: 000656616C6C656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 94:44:52:A6:C7:EA
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption keyn
                    ESSID:"Belkin.47EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c0054189
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 000B42656C6B696E2E34374541
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16070F0400000000000000000000000000000000000000
                    IE: Unknown: DDA50050F204104A00011010440001021041000100103B0001031047001010C73C376FFA4108985B6C63FF941FFD1021001442656C6B696E20496E7465726E6174696F6E616C1023000A4637443733303120763110240007312E30302E30361042000E31323130333147333131333236311054000800060050F2040001101100205368617265204D6178204E33303020576972656C657373204E20526F75746572100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070F0400000000000000000000000000000000000000
          Cell 11 - Address: 2A:98:B9:82:CC:10
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption keyff
                    ESSID:"HPC310a.8CCCE8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000004117888d2df
                    Extra: Last beacon: 3280ms ago
                    IE: Unknown: 000E485043333130612E384343434538
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020001
          Cell 12 - Address: FE:1EF:FD:6B:65
                    Channel:8
                    Frequency:2.447 GHz (Channel 
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption keyn
                    ESSID:"GameStizzle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bb83982347
                    Extra: Last beacon: 2528ms ago
                    IE: Unknown: 000B47616D655374697A7A6C65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1700039301710008000EF81EDFFD6B6508F81EDFFD6B669D
                    IE: Unknown: DD070017F203020180
          Cell 13 - Address: 68:7F:74:91:28:24
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption keyn
                    ESSID:"yourmom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fc6515580
                    Extra: Last beacon: 4792ms ago
                    IE: Unknown: 0007796F75726D6F6D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001900000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A0001101044000102103B00010310470010687F74912822687F74912822022AC107102100104C696E6B73797320627920436973636F102300085752543136304E4C1024000776312E302E303210420001351054000800060050F2040001101100085752543136304E4C100800020084
                    IE: Unknown: DD0A00037F04010000000000
          Cell 14 - Address: 00:11:24:62:C0:F1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption keyn
                    ESSID:"Mocca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cc9b509a7
                    Extra: Last beacon: 5184ms ago
                    IE: Unknown: 00054D6F636361
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0700039301660000
                    IE: Unknown: DD06001018020100

wlan1     Scan completed :
          Cell 01 - Address: C4:3D:C7:4A:B6:39
                    ESSID:"palace"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption keyn
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=81/100  Signal level=-56 dBm  Noise level=-110 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 81ms ago
          Cell 02 - Address: 00:1F:B3:46:19:C9
                    ESSID:"2WIRE711"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-57 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4ms ago
          Cell 03 - Address: 5C9:98:67:3D:AA
                    ESSID:"Hook em Horns"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:5
                    Encryption keyn
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-56 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 10ms ago
          Cell 04 - Address: 00:14:D1:C3:44:7A
                    ESSID:"SuperAwesome"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:7
                    Encryption keyn
                    Bit Rates:450 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=87/100  Signal level=-57 dBm  Noise level=-113 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7ms ago
          Cell 05 - Address: C0:3F:0E:18:7D:00
                    ESSID:"PennyLane"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption keyn
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=59/100  Signal level=-54 dBm  Noise level=-99 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 213ms ago
          Cell 06 - Address: 2A:98:B9:82:CC:10
                    ESSID:"HPC310a.8CCCE8"
                    Protocol:IEEE802.11bg
                    Mode:Ad-Hoc
                    Channel:6
                    Encryption keyff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=60/100  Signal level=-56 dBm  Noise level=-100 dBm
                    Extra: Last beacon: 80ms ago
          Cell 07 - Address: 90:84:0D4:F4:F5
                    ESSID:"Apple Network d4f4f5"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption keyn
                    Bit Rates:216.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=59/100  Signal level=-56 dBm  Noise level=-99 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 22ms ago

blake@Ruiner:~$

---

### Post by Atticus8631 on 2011-10-28
blake@Ruiner:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
blake@Ruiner:~$ 
blake@Ruiner:~$ lsmod
Module                  Size  Used by
aes_i586                7268  6 
aes_generic            26863  1 aes_i586
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
iptable_filter          1369  0 
ip_tables               9899  1 iptable_filter
x_tables               14175  1 ip_tables
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 30784  0 
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
b43                   163556  0 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  288963  3 
yenta_socket           20408  1 
mac80211              205402  1 b43
drm_kms_helper         29329  1 i915
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
r8192s_usb            346908  0 
usbhid                 36110  0 
intel_agp              24375  2 i915
sdhci_pci               5470  0 
soundcore               6620  1 snd
cfg80211              126112  2 b43,mac80211
drm                   163651  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
hid                    67288  1 usbhid
tifm_core               6045  1 tifm_7xx1
psmouse                63677  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  15494  1 sdhci_pci
video                  17375  1 i915
led_class               2864  2 b43,sdhci
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
usb_storage            39841  1 
ssb                    38934  1 b43
ieee1394               81181  1 ohci1394
sky2                   40807  0 
blake@Ruiner:~$ 
blake@Ruiner:~$ lsmod
Module                  Size  Used by
aes_i586                7268  6 
aes_generic            26863  1 aes_i586
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
iptable_filter          1369  0 
ip_tables               9899  1 iptable_filter
x_tables               14175  1 ip_tables
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 30784  0 
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
b43                   163556  0 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  288963  3 
yenta_socket           20408  1 
mac80211              205402  1 b43
drm_kms_helper         29329  1 i915
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
r8192s_usb            346908  0 
usbhid                 36110  0 
intel_agp              24375  2 i915
sdhci_pci               5470  0 
soundcore               6620  1 snd
cfg80211              126112  2 b43,mac80211
drm                   163651  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
hid                    67288  1 usbhid
tifm_core               6045  1 tifm_7xx1
psmouse                63677  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  15494  1 sdhci_pci
video                  17375  1 i915
led_class               2864  2 b43,sdhci
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
usb_storage            39841  1 
ssb                    38934  1 b43
ieee1394               81181  1 ohci1394
sky2                   40807  0 
blake@Ruiner:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.442 GHz (Channel 7)

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.442 GHz (Channel 7)

blake@Ruiner:~$

---

### Post by praseodym on 2011-10-28
Ok, now both devices wanto connect to "SuperAwesome". Add an UDEV-rule, which unloads the driver of the internal device, if the stick is plugged in:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```
Insert:
```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for int. WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-Stick accepted, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf b43"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick plug-out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe b43"

LABEL="rules_end"
```
save, close and reload udev:
```
sudo service udev reload
```
You also may want to remove the iptable-rules:
```
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by Atticus8631 on 2011-10-28
blake@Ruiner:~$ gksu gedit /etc/udev/rules.d/10-wlan-stick.rulesblake@Ruiner:~$ sudo service udev reload
blake@Ruiner:~$ sudo iptables -t filter -n -L -v
Chain INPUT (policy ACCEPT 1700K packets, 2474M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1038K packets, 62M bytes)
 pkts bytes target     prot opt in     out     source               destination         
blake@Ruiner:~$ sudo iptables -F
blake@Ruiner:~$ sudo iptables -X
blake@Ruiner:~$

---

