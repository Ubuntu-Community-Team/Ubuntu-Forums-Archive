---
title: "Ubuntu doesn't recognize wireless in toshiba satelllit l350"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by yarooon on 2009-01-24
e: Ubuntu doesn't see my wireless card
thx eeeiii, will add some more info:

Laptop: TOshiba Satellite L350

jeroen@ubuntujeroen:~$ lsusb
Bus 007 Device 003: ID 0df6:000d Sitecom Europe B.V. WL-168 Wireless Network Adapter 54g
Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jeroen@ubuntujeroen:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


jeroen@ubuntujeroen:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1e:33:54:3e:ce
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::21e:33ff:fe54:3ece/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1817 errors:0 dropped:3268835171 overruns:0 frame:0
TX packets:1709 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1687099 (1.6 MB) TX bytes:302221 (302.2 KB)
Interrupt:220 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:264 errors:0 dropped:0 overruns:0 frame:0
TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:16832 (16.8 KB) TX bytes:16832 (16.8 KB)

wlan0 Link encap:Ethernet HWaddr 00:0c:f6:36:a8:14
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-0C-F6-36-A8-14-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
jeroen@ubuntujeroen:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.427 GHz Access Point: Not-Associated
Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
jeroen@ubuntujeroen:~$ lsmod
Module Size Used by
arc4 9984 2
ecb 10880 2
crypto_blkcipher 25476 1 ecb
rtl8187 53120 0
mac80211 216820 1 rtl8187
eeprom_93cx6 10240 1 rtl8187
cfg80211 32392 2 rtl8187,mac80211
af_packet 25728 4
ipv6 263972 10
i915 38144 2
drm 86056 3 i915
binfmt_misc 16904 1
rfcomm 44432 0
sco 18308 2
bridge 56980 0
stp 10628 1 bridge
bnep 20480 2
l2cap 30464 6 rfcomm,bnep
bluetooth 61924 6 rfcomm,sco,bnep,l2cap
ppdev 15620 0
acpi_cpufreq 15500 1
cpufreq_userspace 11396 0
cpufreq_conservative 14600 0
cpufreq_powersave 9856 0
cpufreq_ondemand 14988 1
cpufreq_stats 13188 0
freq_table 12672 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container 11520 0
wmi 14504 0
pci_slot 12552 0
sbs 19464 0
sbshc 13440 1 sbs
iptable_filter 10752 0
ip_tables 19600 1 iptable_filter
x_tables 22916 1 ip_tables
parport_pc 39204 0
lp 17156 0
parport 42604 3 ppdev,parport_pc,lp
joydev 18368 0
evdev 17696 10
pcspkr 10624 0
psmouse 45200 0
serio_raw 13444 0
uvcvideo 62728 0
iTCO_wdt 18596 0
iTCO_vendor_support 11652 1 iTCO_wdt
compat_ioctl32 9344 1 uvcvideo
snd_hda_intel 381488 3
videodev 41344 1 uvcvideo
v4l1_compat 22404 2 uvcvideo,videodev
snd_pcm_oss 46848 0
snd_mixer_oss 22784 1 snd_pcm_oss
snd_pcm 83204 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 10884 0
video 25104 0
output 11008 1 video
snd_seq_oss 38528 0
snd_seq_midi 14336 0
snd_rawmidi 29824 1 snd_seq_midi
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 29960 2 snd_pcm,snd_seq
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 63268 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
battery 18436 0
soundcore 15328 1 snd
ac 12292 0
button 14224 0
intel_agp 33724 1
snd_page_alloc 16136 2 snd_hda_intel,snd_pcm
shpchp 37908 0
pci_hotplug 35236 1 shpchp
agpgart 42184 3 drm,intel_agp
ext3 133256 2
jbd 55444 1 ext3
mbcache 16004 1 ext3
sd_mod 42264 4
sr_mod 22212 0
cdrom 43168 1 sr_mod
crc_t10dif 9984 1 sd_mod
sg 39732 0
ata_generic 12932 0
pata_acpi 12160 0
ata_piix 24580 0
ahci 37132 3
libata 177312 4 ata_generic,pata_acpi,ata_piix,ahci
scsi_mod 155212 4 sd_mod,sr_mod,sg,libata
dock 16656 1 libata
r8169 35972 0
ehci_hcd 43276 0
uhci_hcd 30736 0
usbcore 148848 5 rtl8187,uvcvideo,ehci_hcd,uhci_hcd
thermal 23708 0
processor 42156 4 acpi_cpufreq,thermal
fan 12548 0
fbcon 47648 0
tileblit 10880 1 fbcon
font 16512 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit
fuse 60828 3

WIll put more info in the nest post if anyone can help me would be just great!

---

### Post by yarooon on 2009-01-24
here is the rest of the info:

jeroen@ubuntujeroen:~$ sudo lshw -C network
[sudo] password for jeroen:
Sorry, try again.
[sudo] password for jeroen:
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:1e:33:54:3e:ce
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: ee:f1:e8:e6:b1:59
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jeroen@ubuntujeroen:~$

jeroen@ubuntujeroen:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
jeroen@ubuntujeroen:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

pan0 Interface doesn't support scannin

jeroen@ubuntujeroen:~$ lsb_release -d
Description: Ubuntu 8.10
2.6.27-7-generic i686
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.

THis all that is asked in the how to post.... I hope someone can help met, its is my second day with ubuntu and really enjoying it

YES WE CAN!!!!

---

### Post by yarooon on 2009-01-25
help  still wanted on this issue

---

### Post by Cylon on 2009-02-06
Go to System/Administration/Hardware Drivers. Turn off the Atheros proprietary driver.

Plug in the laptop with an ethernet cable. Go to System/Administration/Synaptic Package Manager.

Search for linux-restricted-modules-generic and install them.

Unplug the ethernet cable, restart, and when you get logged back in check your network connection for available wireless networks (up by the clock).

Hope that works.

---

### Post by Cylon on 2009-02-10
> **Cylon said:**
> Search for linux-restricted-modules-generic and install them.

Sorry that was the wrong package to look for. You want linux-backports-modules-intrepid.

---

### Post by Sky1337 on 2009-05-04
hey i tryed searching for them but it found nothing any ideas?

---

