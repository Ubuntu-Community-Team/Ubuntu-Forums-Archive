---
title: "Broadcom issue..."
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by mastermesh on 2010-06-09
Ok, in Ubuntu 10.04 my wireless had a major problem and did not work. I've gone back and reinstalled Ubuntu 9 instead and now I think it might work. I just did this this morning, so have not tested it yet since I had to go to work... but the blue light came on so that's a good sign. The computer is a HP DV9700. I've done a lot of reading on this forum and a lot of other forums about it over the last few days. Apparently the issue has to do with the kernel and the wireless driver for this particular type of wifi connector thingy... posts I've read say that it did not work a couple of years ago, then in Ubuntu 9 worked, and then in 10 did not... so if this thing is really working, what do I need to "lock" to keep it from upgrading when I go to upgrade the rest of the Ubuntu system to 10.04 through the update manager? Is this even necessary - i.e. will the version 9 Ubuntu's making it work make things ok if/when I get around to upgrading as long as I do the upgrade via the downloads in synaptic and upgrade manager instead of using a 10.04 installer iso cd?!? If I do need to lock something, what is it, and how do you do that?

---

### Post by SlidingHorn on 2010-06-09
What card/chipset/driver are we talking about here?

---

### Post by mastermesh on 2010-06-09
It's not a wireless card. It's built in to the motherboard I think?!?... Quick little search on hp's site shows these drivers:
 
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=2100&lc=en&cc=us&dlc=en&sw_lang=&product=3636841#N2533](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=2100&lc=en&cc=us&dlc=en&sw_lang=&product=3636841#N2533)
 
Before I downgraded Ubuntu, I used some sort of gizmo that is a part of the main Ubuntu packages that detected the windows driver but I could not get it to work for some reason. Stuff like wifi radar and wikid was completely dead in finding any wireless stuff, and the switch was always red/orange instead of blue indicating no wireless... 
 
Also, in 10.04 there were two wireless hardware thingys detected in the hardware detection thing, but only one of those installed and the other gave me an error of some sort. I tried the ndi wrapper thing listed in some thread somewhere and could not seem to get it to work, of course, I think those instructions were for Ubuntu version 8, not 9 or 10?
 
Not sure on what the real card/chipset/driver names are, but hopefully that gives you some idea... I can't remember exactly but I think the system kept calling the driver bcmwl6

---

### Post by SlidingHorn on 2010-06-09
please post the following outputs in code tags:

```
lspci -nn
```

```
lsmod
```

```
ndiswrapper -l
```

```
lshw -C Network
```

---

### Post by mastermesh on 2010-06-09
FROM 9.04 (EDITED IP ADDRESS TO XXX)

 lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

===
 lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               63240  0 
psmouse                61972  0 
ieee80211_crypt_tkip    16896  0 
joydev                 18368  0 
soundcore              15200  1 snd
compat_ioctl32          9344  1 uvcvideo
k8temp                 12416  0 
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
serio_raw              13316  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
usbhid                 42336  0 
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
forcedeth              61712  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
===
ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
===
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:98:8e:4c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=XXX.XXX.X.X latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:36:91:55
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:bf:b6:37:8d:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by mastermesh on 2010-06-09
from version 10.04 (on the other hard drive)

lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
===

lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 38965  8 
sco                     9302  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11591  2 
l2cap                  35030  16 rfcomm,bnep
b44                    30163  0 
ssb                    52795  1 b44
pcmcia                 35548  1 ssb
compat                  1939  1 ssb
pcmcia_core            38144  2 pcmcia,compat
mii                     5237  1 b44
ndiswrapper           244768  0 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792343  2 vboxnetadp,vboxnetflt
nfsd                  304055  11 
lockd                  75015  1 nfsd
nfs_acl                 2709  1 nfsd
auth_rpcgss            44452  1 nfsd
sunrpc                227939  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4202  1 nfsd
sha256_generic         10327  2 
cryptd                  8116  0 
aes_x86_64              7912  1851 
aes_generic            27607  1 aes_x86_64
dm_crypt               13043  1 
snd_hda_codec_conexant    28745  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  4 
xt_limit                2180  6 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
xt_tcpudp               2667  7 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
ipt_addrtype            2151  4 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
xt_state                1490  9 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip6table_filter         2887  1 
ip6_tables             19618  1 ip6table_filter
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
nf_nat                 19501  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12980  11 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73934  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2791  1 
ip_tables              18390  1 iptable_filter
uvcvideo               62403  0 
x_tables               22429  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
btusb                  12969  2 
bluetooth              58623  9 rfcomm,sco,bnep,l2cap,btusb
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11072  0 
snd                    70978  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               8096262  36 
i2c_nforce2             6099  0 
k8temp                  3912  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
psmouse                64608  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ath_pci               214472  0 
wlan                  249782  1 ath_pci
ath_hal               435276  1 ath_pci
lp                      9336  0 
parport                37160  2 ppdev,lp
nbd                     9935  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ohci1394               30260  0 
video                  20623  0 
output                  2503  1 video
pata_amd               11962  1 
ieee1394               94675  1 ohci1394
vga16fb                12757  1 
forcedeth              55592  0 
vgastate                9857  1 vga16fb
ahci                   37646  2 

====
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl6 : driver installed
	device (14E4:432B) present (alternate driver: wl)
===
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:98:8e:4c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=XXX.XXX.X.X latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f6000000-f6003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by mastermesh on 2010-06-09
I guess with I installed 9.04, I must have picked the second hard drive instead of the original one, so both OSs are on the computer at the moment.

---

