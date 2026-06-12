---
title: "debian wireless help"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by chrisn2323 on 2009-07-18
k so I installed debian with gnome and the wireless internet wont work.  I used the gnome network tool to add my wireless connection but it wouldn't save the connection and connect with it.  Then I installed wireless-tools, the ralink driver, and wpa-supplicant but that still didnt make the network tool work.

So my question is: On a new install of debian, how do you get wireless internet to work?


various information

lsmod
```
chris@chriscomputer:~$ lsmod
Module                  Size  Used by
isofs                  28164  1 
zlib_inflate           14144  1 isofs
nls_utf8                1760  2 
nls_cp437               5568  1 
vfat                    9184  1 
fat                    40896  1 vfat
udf                    67684  0 
nls_base                6820  6 isofs,nls_utf8,nls_cp437,vfat,fat,udf
ipv6                  235364  16 
ppdev                   6500  0 
lp                      8164  0 
loop                   12748  0 
arc4                    1824  2 
ecb                     2624  2 
crypto_blkcipher       15236  1 ecb
rt61pci                20960  0 
crc_itu_t               2080  2 udf,rt61pci
rt2x00pci               7648  1 rt61pci
rt2x00lib              22432  2 rt61pci,rt2x00pci
parport_pc             22500  1 
parport                30988  3 ppdev,lp,parport_pc
firmware_class          6816  1 rt2x00lib
rfkill                  5652  1 rt2x00lib
led_class               3908  1 rt2x00lib
input_polldev           3752  1 rt2x00lib
mac80211              139712  2 rt2x00pci,rt2x00lib
psmouse                32336  0 
serio_raw               4740  0 
cfg80211               21576  2 rt2x00lib,mac80211
pcspkr                  2432  0 
k8temp                  4064  0 
eeprom_93cx6            2144  1 rt61pci
snd_hda_intel         325688  0 
i2c_piix4               7216  0 
i2c_core               19828  1 i2c_piix4
snd_usb_audio          70304  1 
snd_pcm                62596  2 snd_hda_intel,snd_usb_audio
snd_page_alloc          7816  2 snd_hda_intel,snd_pcm
snd_usb_lib            13440  1 snd_usb_audio
snd_seq_midi            5728  0 
snd_seq_midi_event      6432  1 snd_seq_midi
snd_rawmidi            18528  2 snd_usb_lib,snd_seq_midi
snd_hwdep               6212  1 snd_usb_audio
snd_seq                41456  2 snd_seq_midi,snd_seq_midi_event
snd_timer              17800  2 snd_pcm,snd_seq
snd_seq_device          6380  3 snd_seq_midi,snd_rawmidi,snd_seq
button                  6096  0 
snd                    45604  10 snd_hda_intel,snd_usb_audio,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               6368  1 snd
ati_agp                 6220  0 
agpgart                28776  1 ati_agp
evdev                   8000  4 
ext3                  105512  2 
jbd                    39444  1 ext3
mbcache                 7108  1 ext3
usbhid                 35904  0 
hid                    33184  1 usbhid
ff_memless              4392  1 usbhid
usb_storage            77024  1 
sg                     26964  0 
sr_mod                 13316  1 
cdrom                  30176  1 sr_mod
sd_mod                 22200  6 
atiixp                  3396  0 [permanent]
ide_pci_generic         3908  0 [permanent]
ide_core               96136  2 atiixp,ide_pci_generic
floppy                 47748  0 
ata_generic             4676  0 
ehci_hcd               28396  0 
ohci_hcd               18500  0 
usbcore               118224  7 snd_usb_audio,snd_usb_lib,usbhid,usb_storage,ehci_hcd,ohci_hcd
ahci                   23596  4 
libata                140416  2 ata_generic,ahci
scsi_mod              129324  5 usb_storage,sg,sr_mod,sd_mod,libata
dock                    8304  1 libata
r8169                  23684  0 
thermal                15228  0 
processor              32544  1 thermal
fan                     4164  0 
thermal_sys            10856  3 thermal,processor,fan

```lspci
```
chris@chriscomputer:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```ifconfig
```
chriscomputer:/home/chris# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1a:70:a4:f9:d2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```iwconfig
```
chriscomputer:/home/chris# iwconfig wlan0
wlan0     IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Entering info to connect
[IMG]http://img35.imageshack.us/img35/7986/screenshotjsr.png[/IMG]

What happens when I open the same program again
[IMG]http://img245.imageshack.us/img245/5880/screenshot1n.png[/IMG]

---

### Post by chrisn2323 on 2009-07-19
bump

---

### Post by LukonLinux on 2010-01-05
I've got the same issue.  Has no one come up with a solution yet?

---

