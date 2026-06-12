---
title: "USB WEB camera Vimicro ZC0301PL can not work with EKIGA"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by Evgeni45 on 2007-07-31
USB WEB camera Vimicro ZC0301PL can not work with EKIGA , OS Ubuntu 6.10 or 7.04.

   USB WEB camera Vimicro ZC0301PL can not work with EKIGA
Listing after execute command LSMOD is

root@rezv:/home/rezv# lsmod
Module Size Used by
zc0301 48516 0
gspca 659920 0
sg 36252 0
sd_mod 23428 2
usb_storage 72256 1
libusual 17936 1 usb_storage
videodev 28160 2 zc0301,gspca
v4l2_common 25216 2 zc0301,videodev
v4l1_compat 15236 1 videodev
ipv6 268960 8
rfcomm 40856 0
l2cap 25856 5 rfcomm
bluetooth 55908 4 rfcomm,l2cap
binfmt_misc 12680 1
ppdev 10116 0
powernow_k8 16064 0
cpufreq_userspace 5408 0
cpufreq_stats 7360 0
cpufreq_powersave 2688 0
cpufreq_ondemand 9228 1
freq_table 5792 3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative 8200 0
tc1100_wmi 8068 0
pcc_acpi 13184 0
dev_acpi 12292 0
sony_acpi 6284 0
video 16388 0
sbs 15652 0
i2c_ec 6016 1 sbs
dock 10268 0
button 8720 0
battery 10756 0
container 5248 0
ac 6020 0
asus_acpi 17308 0
backlight 7040 1 asus_acpi
rt61 245128 0
nls_iso8859_1 5120 2
nls_cp437 6784 2
vfat 14208 2
fat 53916 1 vfat
lp 12452 0
snd_via82xx 29208 1
gameport 16520 1 snd_via82xx
snd_ac97_codec 98464 1 snd_via82xx
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 10888 2 snd_via82xx,snd_pcm
snd_mpu401_uart 9472 1 snd_via82xx
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
parport_pc 36388 1
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport 36936 3 ppdev,lp,parport_pc
pcspkr 4224 0
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse 38920 0
serio_raw 7940 0
usblp 14848 0
i2c_viapro 10132 0
k8temp 6656 0
i2c_core 22656 2 i2c_ec,i2c_viapro
snd 54020 13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_agp 13700 1
agpgart 35400 1 amd64_agp
soundcore 8672 1 snd
shpchp 34324 0
pci_hotplug 32576 1 shpchp
af_packet 23816 2
tsdev 8768 0
evdev 11008 3
ext3 133128 1
jbd 59816 1 ext3
mbcache 9604 1 ext3
ide_cd 32672 0
cdrom 37664 1 ide_cd
ide_disk 17024 4
floppy 59524 0
ehci_hcd 34188 0
via_rhine 25608 0
mii 6528 1 via_rhine
uhci_hcd 25360 0
usbcore 134280 8 zc0301,gspca,usb_storage,libusual,usblp,ehci_hcd,uhci_hcd
via82cxxx 10372 0 [permanent]
sata_via 12548 0
ata_generic 9092 0
libata 125720 2 sata_via,ata_generic
scsi_mod 142348 4 sg,sd_mod,usb_storage,libata
generic 5124 0 [permanent]
thermal 14856 0
processor 31048 2 powernow_k8,thermal
fan 5636 0
fbcon 42656 0
tileblit 3584 1 fbcon
font 9216 1 fbcon
bitblit 6912 1 fbcon
softcursor 3200 1 bitblit
vesafb 9220 0
capability 5896 0
commoncap 8192 1 capability
root@rezv:/home/rezv#
  

The output of the lsusb command is:

root@rezv:/home/rezv# lsusb
Bus 005 Device 003: ID 058f:6387 Alcor Micro Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 004: ID 04e8:300c Samsung Electronics Co., Ltd ML-1210 Printer
Bus 001 Device 001: ID 0000:0000

Additional information.
I have System - Ubuntu 6.10
gspca modul from gspca-source_01.00.16-1-1_all.deb becouse mounted in distribution program Ubuntu 6.10 dont work.
  With gspca from gspca-source_01.00.16-1-1_all.deb WEB camera begin start and light diode.
  However EKIGA or Camorama show black screen.

I see the chip in WEB camera it is zc0301PL.





I execute command gstreamer-properties. Its result:

 root@rezv:/usr/gstreamer/gstreamer-0.10.13# gstreamer-properties

(gstreamer-properties:15668): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
root@rezv:/usr/gstreamer/gstreamer-0.10.13#

The black screen is as result.


I instal all gstreamer packages but EKIGA or Camorama or Mplayer show black screen.
  30.07.07
Evgeni

---

