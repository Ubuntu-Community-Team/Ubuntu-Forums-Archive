---
title: "Ethernet quit working after update."
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by dipswitch on 2006-06-06
My onboard and NIC quit working yesterday when I got to work and performed updates. I've gone to my Network settings and activated and deactived each to no avail. Its a dual boot so I'm posting from XP on the same computer so I know it works and it was working just fine until Monday morning. Its got to be something simple but I'm about to lose my mind. ](*,)    At the moment I've disabled eth0 and I'm using eth1. Anyways here some info.

lspci
```

dipswitch@THEEGGMAN:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
dipswitch@THEEGGMAN:~$

```

ifconfig
```

dipswitch@THEEGGMAN:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:40:CA:47:3E:E5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```

lsmod
```

dipswitch@THEEGGMAN:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
savage                 35584  1
drm                    73236  2 savage
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
sg                     37920  0
sd_mod                 19984  2
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
fuse                   38412  0
af_packet              22920  2
lp                     11844  0
snd_seq_dummy           3844  0
usb_storage            74176  1
scsi_mod              139496  3 sg,sd_mod,usb_storage
tsdev                   8000  0
snd_seq_oss            33536  0
usbhid                 38368  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
i2c_prosavage           4224  0
i2c_algo_bit            9608  1 i2c_prosavage
pcspkr                  2180  0
snd_via82xx            28824  1
gameport               15496  1 snd_via82xx
snd_ac97_codec         92704  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
i2c_viapro              8980  0
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
i2c_core               21904  3 i2c_acpi_ec,i2c_algo_bit,i2c_viapro
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_ircc               26900  0
rtc                    13492  0
irda                  186940  1 via_ircc
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
psmouse                36228  0
crc_ccitt               2304  1 irda
serio_raw               7300  0
via_agp                 9856  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
agpgart                34888  2 drm,via_agp
tulip                  51872  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by dipswitch on 2006-06-06
Although I have no idea what I'm doing I managed to get back online. I opened up the terminal and used ifup for each connection and this is what I got.

```

root@THEEGGMAN:/home/dipswitch# ifup eth1
ifup: interface eth1 already configured
root@THEEGGMAN:/home/dipswitch# ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:04:5a:76:57:ce
Sending on   LPF/eth0/00:04:5a:76:57:ce
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.10.17.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.10.17.1
bound to 10.10.19.25 -- renewal in 322518 seconds.

```
Then opened up a browser and it still wouldn 't connect. I switched the cable to eth0 opened up my Network settings and reactivated eth0 and I'm connected. I moved the cable back to eth1 since the connection was slow with eth0 and now its working.

---

