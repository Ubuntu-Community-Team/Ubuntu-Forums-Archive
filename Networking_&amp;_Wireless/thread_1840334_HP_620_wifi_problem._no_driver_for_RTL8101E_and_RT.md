---
title: "HP 620 wifi problem. no driver for RTL8101E and RT3090"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by andoras on 2011-09-07
Hi!

I'm searching for drivers for my brand new HP 620 Notebook. The devices are the followings

Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller&#65279;

I use Ubuntu Linux. I'm  lookin after any driver, but 2.6.38 kernel or newer would the best. The [official driver]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=4158863&swItem=ob-88041-1&prodNameId=4158501&swEnvOID=2020&swLang=13&taskId=135&mode=5") (for SuSE Linux kernel 2.6.32) doesn't seems to work. I would like to use Natty but Lucid LTS is also a better solution than Windows. Is  there a possibility that I can use my notebook?

I would really appreciate your answer.

Andorás

---

### Post by praseodym on 2011-09-07
Hi,

please show

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by andoras on 2011-09-07
Here they are:
```
andoras@andoras-laptop:~$ uname -a
Linux andoras-laptop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
andoras@andoras-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Kernel driver in use: rt3090
    Kernel modules: rt3090sta
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8101, r8169
andoras@andoras-laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 33421  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      52042  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
joydev                  8740  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
uvcvideo               57374  0 
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
rt3090sta             674216  0 
intel_agp              24375  2 i915
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  3 
r8169                  34140  0 
mii                     4381  1 r8169
andoras@andoras-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 64:31:50:6e:08:8e  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6631:50ff:fe6e:88e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1843526 (1.8 MB)  TX bytes:539831 (539.8 KB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr 82:3e:77:69:f6:8a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

andoras@andoras-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

andoras@andoras-laptop:~$ rfkill list
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
andoras@andoras-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

Since I've post my problem I tried to install [compat-wireless]("http://linuxwireless.org/download/compat-wireless-2.6/"), but it didn't works.

---

### Post by praseodym on 2011-09-07
Try this updated driver, installation procedure:

[http://forum.ubuntuusers.de/post/2666022/](http://forum.ubuntuusers.de/post/2666022/)

Driver direct link:

[http://media.cdn.ubuntu-de.org/forum/attachments/2666017/RT3390_LinuxSTA_V2.4.0.1_20100831-angepasst.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2666017/RT3390_LinuxSTA_V2.4.0.1_20100831-angepasst.tar.gz)

It worked there for Lucid.

Compat wireless doesnt work for this wireless device.

---

### Post by andoras on 2011-09-07
Wow! I am amazed! Danke sehr!
It solved my problem.
Do you think it works on 11.04? Because I want to use it (and 11.10 after release)
And again, thank you, I spent two days to find the answer and you solved it.
:guitar:

---

### Post by praseodym on 2011-09-07
In 11.04 there are even 2 drivers for this device, rt2860sta (alias rt3090sta) and rt2800pci. The latter one is more developed now, so the rt2860sta should be blacklisted in 11.04 via:

```
echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

See this post/thread:

[http://forum.ubuntuusers.de/post/3204452/](http://forum.ubuntuusers.de/post/3204452/)

Edit: 2 drivers loaded dont work! Blacklisting is valid.

---

### Post by andoras on 2011-11-21
Hi there!

Sorry for disturbing you again, but I didn't get the right solution. Now I had just tried the Oneiric Ocelot (11.10) and I like the new outfit.
But my wifi card doesn't seem to work with the LiveCD so I shouldn't risk to clear my recent OS and replace with Ubuntu.

The sign up on the right started to search networks and found them right but after it couldn't connect.
The card is:
```
ubuntu@ubuntu:~$ lspci | grep net
85:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

Can I fix it with Live CD or should I install first?

Thank you is someone could help me.
andoras

---

### Post by praseodym on 2011-11-22
Hi andoras,

this is your LAN card. Please show completely
```
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by andoras on 2011-11-22
Here are the details:
```
ubuntu@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: ahci
    Kernel modules: ahci
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Hewlett-Packard Company Device [103c:1453]
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1526]
    Kernel driver in use: r8169
    Kernel modules: r8169
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0461:4db6 Primax Electronics, Ltd 
Bus 004 Device 002: ID 148f:1000 Ralink Technology, Corp. 
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  8 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci
snd_rawmidi            25241  1 snd_seq_midi
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              28932  2 snd_pcm,snd_seq
btusb                  18160  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 rt2x00lib,mac80211
bluetooth             148839  23 bnep,rfcomm,btusb
joydev                 17393  0 
uvcvideo               67271  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               85626  1 uvcvideo
hp_wmi                 13652  0 
psmouse                73673  0 
soundcore              12600  1 snd
sparse_keymap          13658  1 hp_wmi
serio_raw              12990  0 
eeprom_93cx6           12653  1 rt2800pci
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_utf8               12493  1 
isofs                  39549  1 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ahci                   21634  1 
libahci                25727  1 ahci
r8169                  43104  0 
i915                  505108  3 
wmi                    18744  1 hp_wmi
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ubuntu@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Thank you for looking at this.

---

### Post by praseodym on 2011-11-22
Try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2666017/RT3390_LinuxSTA_V2.4.0.1_20100831-angepasst.tar.gz
tar xzf RT3390_LinuxSTA_V2.4.0.1_20100831-angepasst.tar.gz
cd DPO_RT3390_LinuxSTA_V2.4.0.1_20100831
sudo make
sudo make install
sudo modprobe -rf rt2800pci
sudo modprobe rt3390sta
sudo depmod -a
sudo service network-manager restart
dmesg | grep rt3
iwconfig
sudo iwlist scan
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```

---

### Post by andoras on 2011-11-22
Thank you! & köszönöm!
It works with the Live CD so now I can start the installation process, to be one of the [200 million Ubuntu]("http://www.omgubuntu.co.uk/2011/05/mark-shuttleworth-delivers-uds-keynote-address-sets-goal-for-200-million-ubuntu-users-in-4-years/") user...

---

