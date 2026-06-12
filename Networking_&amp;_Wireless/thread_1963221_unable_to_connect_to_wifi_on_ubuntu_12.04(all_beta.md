---
title: "unable to connect to wifi on ubuntu 12.04(all betas)"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by ashjas on 2012-04-22
ive been willing to test ubuntu 12 since long.. but one insane bug doesnt allow me to..

whenever i try to connect to wifi ,firstly not all wifi access points listed are clickable,, secondly if they are available.. the following dialog appears that has the connect button disabled..
[IMG]http://i.stack.imgur.com/cLnLs.png[/IMG]


this is has been happening since every beta for ubuntu 12..

Please suggest a solution..

Thanks.

Update: I tried installing it over a more recent laptop and everything is working on it fine.. So most probably ubuntu has made some changes in the defaultly shipped drivers that is causing such an issue... may be they decided not to support my hardware.. [http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=108831](http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=108831)

Can anyone guide me to make this thing working? Thanks..

---

### Post by wildmanne39 on 2012-04-22
Hi, I will give it a try, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ashjas on 2012-04-22
output on Precise beta2:
```
ubuntu@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ubuntu 3.2.0-20-generic-pae #33-Ubuntu SMP Tue Mar 27 17:05:18 UTC 2012 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: 8139too
--
06:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Device [8086:2741]
	Kernel driver in use: ipw2200
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1e3d:2092 Chipsbank Microelectronics Co., Ltd 
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
dm_crypt               22528  0 
parport                40930  3 parport_pc,ppdev,lp
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  0 
dm_multipath           22710  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146207  0 
libipw                 46701  1 ipw2200
tifm_7xx1              12937  0 
joydev                 17393  0 
yenta_socket           27465  0 
cfg80211              178679  2 ipw2200,libipw
tifm_core              15040  1 tifm_7xx1
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14040  2 ipw2200,libipw
toshiba_acpi           17930  0 
mac_hid                13077  0 
psmouse                72846  0 
soundcore              14635  1 snd
sparse_keymap          13658  1 toshiba_acpi
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
squashfs               36095  1 
overlayfs              27511  1 
nls_utf8               12493  1 
isofs                  39553  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41906  0 
hid                    77367  1 usbhid
usb_storage            39646  1 
radeon                733636  3 
ttm                    65344  1 radeon
drm_kms_helper         32857  1 radeon
drm                   197551  5 radeon,ttm,drm_kms_helper
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
8139too                23283  0 
8139cp                 26759  0 
i2c_algo_bit           13199  1 radeon
video                  18907  0 
ubuntu@ubuntu:~$ 
```

Output on ubuntu 10.04 (where things are working fine..)
```
ashish@ashish-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ashish-laptop 2.6.32-40-generic #87-Ubuntu SMP Mon Mar 5 20:26:31 UTC 2012 i686 GNU/Linux
ashish@ashish-laptop:~$ lspci -nnk | grep -iA2 net
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
06:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200
ashish@ashish-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ashish@ashish-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"AirtelBB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:40:F1:9B:07   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=-37 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:40

ashish@ashish-laptop:~$ rfkill list all
ashish@ashish-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
usb_storage            40033  0 
arc4                    1153  2 
lib80211_crypt_wep      2667  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_oss            26722  0 
vga16fb                11385  0 
snd_seq_midi            4557  0 
vgastate                8961  1 vga16fb
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                678831  3 
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  1 
ttm                    49847  1 radeon
soundcore               6620  1 snd
drm_kms_helper         29329  1 radeon
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
drm                   163779  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
intel_agp              24375  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63677  0 
video                  17375  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  1 sdhci
tifm_core               6045  1 tifm_7xx1
ipw2200               135216  0 
agpgart                31724  3 ttm,drm,intel_agp
libipw                 39896  1 ipw2200
lib80211                5046  3 lib80211_crypt_wep,ipw2200,libipw
output                  1871  1 video
joydev                  8740  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ohci1394               26950  0 
8139too                18545  0 
8139cp                 16186  0 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
ashish@ashish-laptop:~$ 

```

Thanks so much for helping...

---

### Post by wildmanne39 on 2012-04-23
Hi, it looks like you have a hidden network if that is the case please unhide it and see if you can connect to it, just so you know it really is not any safer to have a hidden network.

After you do that please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep ipw
```
```
sudo cat /var/log/syslog | grep -e ipw -e firmware -e eth1 -e wpa -e etork | tail -n55
```
Thanks

---

