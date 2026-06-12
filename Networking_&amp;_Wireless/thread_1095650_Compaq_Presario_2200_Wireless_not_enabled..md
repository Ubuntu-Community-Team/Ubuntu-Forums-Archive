---
title: "Compaq Presario 2200 Wireless not enabled."
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mountzionryan on 2009-03-13
The Compaq Presario 2200 has a button that allows you to turn off the wireless network adapter.  It was working fine in XP, but when I installed Ubuntu, it does not work.

Here the pertinant info.  Please help.

ON a Presario 2200 here's all the info from terminal:


ryan@ryan:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ryan@ryan:~$ lspci -nn | grep 'Broadcom'
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

ryan@ryan:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ryan@ryan:~$ iwconfig wlan0
wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ryan@ryan:~$ lsmod
Module Size Used by
nls_iso8859_1 12032 1
nls_cp437 13696 1
vfat 18816 1
fat 57376 1 vfat
usb_storage 81728 1
libusual 27156 1 usb_storage
ipv6 263972 8
af_packet 25728 2
rfkill_input 12672 0
i915 38144 2
drm 86056 3 i915
binfmt_misc 16904 1
rfcomm 44432 0
bridge 56980 0
stp 10628 1 bridge
bnep 20480 2
sco 18308 2
l2cap 30464 6 rfcomm,bnep
bluetooth 61924 6 rfcomm,bnep,sco,l2cap
ppdev 15620 0
cpufreq_powersave 9856 0
cpufreq_conservative 14600 0
cpufreq_userspace 11396 0
cpufreq_ondemand 14988 0
cpufreq_stats 13188 0
freq_table 12672 2 cpufreq_ondemand,cpufreq_stats
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
pcmcia 43052 0
arc4 9984 2
ecb 10880 2
crypto_blkcipher 25476 1 ecb
b43 131356 0
rfkill 17176 2 rfkill_input,b43
mac80211 216820 1 b43
cfg80211 32392 1 mac80211
evdev 17696 9
led_class 12164 1 b43
snd_intel8x0 37532 3
input_polldev 11912 1 b43
snd_ac97_codec 111652 1 snd_intel8x0
psmouse 45200 0
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46848 0
snd_mixer_oss 22784 1 snd_pcm_oss
serio_raw 13444 0
yenta_socket 31756 1
snd_pcm 83204 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
rsrc_nonstatic 19072 1 yenta_socket
pcmcia_core 43412 3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy 10884 0
container 11520 0
video 25104 0
output 11008 1 video
pcspkr 10624 0
snd_seq_oss 38528 0
snd_seq_midi 14336 0
wmi 14504 0
battery 18436 0
snd_rawmidi 29824 1 snd_seq_midi
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi
ac 12292 0
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
button 14224 0
snd_timer 29960 2 snd_pcm,snd_seq
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 63268 16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
soundcore 15328 1 snd
snd_page_alloc 16136 2 snd_intel8x0,snd_pcm
shpchp 37908 0
pci_hotplug 35236 1 shpchp
iTCO_wdt 18596 0
iTCO_vendor_support 11652 1 iTCO_wdt
intel_agp 33724 1
agpgart 42184 3 drm,intel_agp
ext3 133256 1
jbd 55444 1 ext3
mbcache 16004 1 ext3
sr_mod 22212 0
cdrom 43168 1 sr_mod
sd_mod 42264 5
crc_t10dif 9984 1 sd_mod
sg 39732 0
ata_piix 24580 2
pata_acpi 12160 0
8139cp 27520 0
ata_generic 12932 0
libata 177312 3 ata_piix,pata_acpi,ata_generic
ssb 40580 1 b43
8139too 31616 0
mii 13440 2 8139cp,8139too
uhci_hcd 30736 0
ehci_hcd 43276 0
scsi_mod 155212 5 usb_storage,sr_mod,sd_mod,sg,libata
dock 16656 1 libata
usbcore 148848 5 usb_storage,libusual,uhci_hcd,ehci_hcd
thermal 23708 0
processor 42156 2 thermal
fan 12548 0
fbcon 47648 0
tileblit 10880 1 fbcon
font 16512 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit
fuse 60828 3

ryan@ryan:~$ sudo lshw -C network
[sudo] password for ryan:
*-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 10
serial: 00:c0:9f:6d:2b:ea
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
*-network:1
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 6
bus info: pci@0000:02:06.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:90:4b:b5:f8:0b
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 7e:73:0c:ad:6b:14
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


ryan@ryan:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 No scan results

pan0 Interface doesn't support scanning.


ryan@ryan:~$ uname -mr
2.6.27-7-generic i686

ryan@ryan:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... [ OK ]

---

### Post by mountzionryan on 2009-03-14
bump

---

