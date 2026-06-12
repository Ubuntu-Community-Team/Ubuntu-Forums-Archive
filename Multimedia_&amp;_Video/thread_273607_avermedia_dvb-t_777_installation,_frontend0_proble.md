---
title: "avermedia dvb-t 777 installation, frontend0 problem"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by mcuerdo on 2006-10-08
I followed this how to [http://linuxtv.org/wiki/index.php/AverTV_DVB-T_777_PCI](http://linuxtv.org/wiki/index.php/AverTV_DVB-T_777_PCI)
 but when I try to scan I get:

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

which I created with the provided script. any idea? i'm using kernel 2.6.17

**dmesg:**
```
[17179592.676000] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 11, latency: 32, mmio: 0xe7002000
[17179592.676000] saa7133[0]: subsystem: 1461:2c05, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179592.676000] saa7133[0]: board init: gpio is 2f000
[17179592.860000] saa7133[0]: i2c eeprom 00: 61 14 05 2c 00 00 00 00 00 00 00 00 00 00 00 00
[17179592.860000] saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a8 ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.860000] saa7133[0]: registered device video0 [v4l2]
[17179592.860000] saa7133[0]: registered device vbi0
[17179592.880000] saa7134 ALSA driver for DMA sound loaded
[17179592.880000] saa7133[0]/alsa: saa7133[0] at 0xe7002000 irq 11 registered as card -1
```

**lsmod**
```
binfmt_misc 11848 1
rfcomm 38360 6
l2cap 24964 5 rfcomm
ip_conntrack_irc 6616 0
ip_conntrack_ftp 7644 0
ip_conntrack 50072 2 ip_conntrack_irc,ip_conntrack_ftp
nfnetlink 6872 1 ip_conntrack
ppdev 9540 0
cpufreq_userspace 4052 0
cpufreq_stats 5700 0
freq_table 4548 1 cpufreq_stats
cpufreq_powersave 1792 0
cpufreq_ondemand 6624 0
cpufreq_conservative 6688 0
video 15108 0
button 6480 0
battery 9348 0
container 4352 0
ac 4740 0
af_packet 22344 0
nls_iso8859_1 4096 1
nls_cp437 5760 1
vfat 13440 1
fat 55452 1 vfat
nls_utf8 2112 1
ntfs 111476 1
dm_mod 57844 1
ipv6 263808 16
md_mod 80468 0
sr_mod 16996 0
sbp2 23432 0
lp 11968 0
saa7134_alsa 13408 0
hci_usb 15700 6
bluetooth 50148 15 rfcomm,l2cap,hci_usb
saa7134 116256 1 saa7134_alsa
snd_intel8x0 33116 1
snd_ac97_codec 96672 1 snd_intel8x0
snd_ac97_bus 2240 1 snd_ac97_codec
snd_pcm_oss 42784 0
snd_mixer_oss 18624 1 snd_pcm_oss
snd_pcm 89096 4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 24324 1 snd_pcm
video_buf 26244 2 saa7134_alsa,saa7134
tsdev 7936 0
ir_kbd_i2c 8656 1 saa7134
ir_common 27332 2 saa7134,ir_kbd_i2c
ov511 75604 0
snd 54208 9 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9888 1 snd
snd_page_alloc 10248 2 snd_intel8x0,snd_pcm
usblp 13888 0
serio_raw 7044 0
pcspkr 2944 0
parport_pc 36464 1
parport 38344 3 ppdev,lp,parport_pc
shpchp 40728 0
pci_hotplug 31796 1 shpchp
i2c_nforce2 7040 0
floppy 62060 0
psmouse 40392 0
forcedeth 29580 0
nvidia_agp 8092 1
agpgart 33072 1 nvidia_agp
evdev 10176 1
ext3 142024 1
jbd 59860 1 ext3
mbcache 9028 1 ext3
ide_generic 1216 0 [permanent]
uhci_hcd 23180 0
ohci1394 35504 0
ieee1394 301944 2 sbp2,ohci1394
ehci_hcd 33096 0
ohci_hcd 21060 0
usbcore 131740 7 hci_usb,ov511,usblp,uhci_hcd,ehci_hcd,ohci_hcd
ide_cd 41568 0
cdrom 38512 2 sr_mod,ide_cd
ide_disk 17152 6
generic 4356 0 [permanent]
amd74xx 14428 0 [permanent]
sata_nv 9668 0
libata 72972 1 sata_nv
scsi_mod 138412 3 sr_mod,sbp2,libata
thermal 13128 0
processor 22016 1 thermal
fan 4612 0
vga16fb 12616 0
cfbcopyarea 3712 1 vga16fb
vgastate 9344 1 vga16fb
cfbimgblt 2880 1 vga16fb
```
cfbfillrect 4096 1 vga16fb

---

### Post by JPDyno on 2007-02-16
sorry not a solution,
but im having exactly the same problem

i have a clean install of 6.10

i tried to step through this :
[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

when i get to scan, i have the same problem.

after reading through whatever i could find, ive added
saa7134
saa7134-dvb
saa7134-alsa
to etc/modules

and all of them are listed under lsmod
and there is still no /dev/dvb

---

### Post by david_2001 on 2007-02-16
> **JPDyno said:**
> 
after reading through whatever i could find, ive added
saa7134
saa7134-dvb
saa7134-alsa
to etc/modules

and all of them are listed under lsmod
and there is still no /dev/dvb

The dmesg output posted by mcuerdo indicates that the saa7134 driver is not recognising the card:
> [17179592.676000] saa7133[0]: subsystem: 1461:2c05, board: UNKNOWN/GENERIC [**card=0**,autodetected]
What I read tells me that the card is supported from kernel 2.6.17 but the card number needs to be passed to the saa7134 driver.  Using information from the [COLOR="SandyBrown"][AVerMedia AVerTV DVB-T 777 PCI]("http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_PCI")[/COLOR] page, the following ought to work when combined with all of the /etc/modules entries listed above, though they shouldn't really be necessary:
```
sudo sh -c 'echo "options saa7134 card=85" > /etc/modprobe.d/saa7134'
```
All it does is create a file in /etc/modprobe.d containing the card identity number to be passed as a load parameter to the saa7134 driver.  If it's correct then a restart should find the card being detected.

---

### Post by JPDyno on 2007-02-17
it worked!!
thankyou very much for the quick reply

---

### Post by david_2001 on 2007-02-17
You're welcome :)

---

### Post by mcuerdo on 2007-02-20
> **JPDyno said:**
> it worked!!
thankyou very much for the quick reply
JPDyno, have you got you Remote Control working? 

I just installed last version of v4l-dvb and it worked ;-)

Well, you need some files (lircrc, etc...) they are explained in the howto you followed. Tell me if you need some help

---

