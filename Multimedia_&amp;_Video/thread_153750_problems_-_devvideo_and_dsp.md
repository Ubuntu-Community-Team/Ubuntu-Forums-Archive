---
title: "problems - /dev/video* and dsp*"
date: 2006-04-01
forum: Multimedia &amp; Video
---

### Post by mystical on 2006-04-01
I have problems whit Dexul DLV-BO1 webcam; /dev/video and dsp

Debian Etch kernel 2.6.15-1-k7

mystical:~# cd /dev/
mystical:/dev# ./MAKEDEV -v sound
create dsp      c 14 3 root:audio 0660
create dsp1     c 14 19 root:audio 0660
...
[B]mystical:/dev# ls dsp*
ls: dsp*: No such file or directory[/B]

mystical:/dev# ./MAKEDEV -v video
create video0   c 81 0 root:video 0660
create radio0   c 81 64 root:video 0660
create video1   c 81 1 root:video 0660
create radio1   c 81 65 root:video 0660
create vtx0     c 81 192 root:video 0660
create vbi0     c 81 224 root:video 0660
create radio    -> radio0
create video    -> video0
create vbi      -> vbi0
...
[B]mystical:/dev# ls vide*
ls: vide*: No such file or directoy[/B]

mystical:/dev# mknod /dev/video0 c 81 0
mystical:/dev# chmod g+rw /dev/video0
mystical:/dev# grep -e video /etc/group
mystical:/dev# ls video*
video0

[B]mystical:~# xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-1-k7)
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no video grabber device available
[/B]

mystical:~# lsmod
Module                  Size  Used by
isofs                  33400  0
udf                    74628  0
spca5xx               646416  0
videodev                8832  1 spca5xx
video                  16068  0
radeon                 97120  1
drm                    64724  2 radeon
ipv6                  222976  10
button                  6544  0
ac                      4740  0
battery                 9476  0
nls_iso8859_1           4032  2
ntfs                  191824  2
sr_mod                 16420  0
sbp2                   21380  0
eth1394                18696  0
rt2500                153188  1
joydev                  8960  0
evdev                   8896  1
psmouse                32516  0
ns558                   5188  0
gameport               14024  2 ns558
serio_raw               6596  0
mousedev               10592  1
radeonfb               79488  1
i2c_algo_bit            8392  1 radeonfb
snd_mpu401              6344  0
snd_mpu401_uart         6656  1 snd_mpu401
snd_rawmidi            22688  1 snd_mpu401_uart
snd_seq_device          8012  1 snd_rawmidi
parport_pc             32324  0
parport                31880  1 parport_pc
shpchp                 39872  0
pci_hotplug            24884  1 shpchp
ohci1394               30452  0
ieee1394               89208  3 sbp2,eth1394,ohci1394
snd_intel8x0           29660  1
snd_ac97_codec         82528  1 snd_intel8x0
snd_ac97_bus            2112  1 snd_ac97_codec
snd_pcm                77704  2 snd_intel8x0,snd_ac97_codec
snd_timer              21444  1 snd_pcm
snd                    48740  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8992  1 snd
snd_page_alloc          9992  2 snd_intel8x0,snd_pcm
i2c_nforce2             6336  0
nvidia_agp              7260  1
agpgart                31496  2 drm,nvidia_agp
i2c_core               19408  3 radeonfb,i2c_algo_bit,i2c_nforce2
ext3                  118664  1
jbd                    48724  1 ext3
mbcache                 8516  1 ext3
ide_cd                 36804  0
cdrom                  33568  2 sr_mod,ide_cd
ide_disk               15936  5
ide_generic             1216  0 [permanent]
sata_nv                 8836  0
libata                 51724  1 sata_nv
scsi_mod              126120  3 sr_mod,sbp2,libata
generic                 4356  0 [permanent]
amd74xx                12892  0 [permanent]
ide_core              112928  5 ide_cd,ide_disk,ide_generic,generic,amd74xx
ehci_hcd               29064  0
ohci_hcd               17860  0
forcedeth              20228  0
usbcore               113924  4 spca5xx,ehci_hcd,ohci_hcd
thermal                13512  0
processor              22976  1 thermal
fan                     4676  0

](*,) ](*,) ](*,)

---

