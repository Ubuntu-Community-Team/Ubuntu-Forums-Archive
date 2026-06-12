---
title: "turning on sound turns off the usb mouse"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by stronzo420 on 2008-02-12
Howdy folks,

Just installed ubuntu, everything's working fine except sound, which there is none. Have an old diamond sound card. Following [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) I did cat /proc/asound/cards which gave me this:

```
home@home-desktop:~$ cat /proc/asound/cards
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC200,200P at 0xd000, irq 21
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
 2 [au8830         ]: au8830 - Aureal Vortex au8830
                      Aureal Vortex au8830 at 0xee000000 irq 22
```

which seems like my sound card is getting bumped to card2, so i went into /etc/modprobe.d/alsa-base, commented out this:

```
options snd-usb-audio index=-2
```

and added this:

```
options snd-usb-audio index=2
```

Upon rebooting I think sound was working because I heard the speakers kind of pop on, but unfortunately the USB mouse stopped working so I couldn't test it out. Had to revert the change. I'm a total newbie, can someone point me to what I'm doing wrong?

BTW - here's some other output that other threads on debugging sound problems seem to like to have, not that I understand it...

```
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```

```
 lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
video                  16388  0 
battery                10756  0 
button                  8720  0 
container               5248  0 
ipv6                  269088  8 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
snd_mpu401              9256  0 
nvidia               4713780  32 
snd_au8830             52788  0 
snd_mpu401_uart         9472  2 snd_mpu401,snd_au8830
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
analog                 12832  0 
gameport               16520  3 snd_au8830,analog
snd_intel8x0           34332  1 
snd_ac97_codec         98464  2 snd_au8830,snd_intel8x0
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usbhid                 26592  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
hid                    27392  1 usbhid
sis_agp                 9604  1 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                79876  4 snd_au8830,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
agpgart                35400  2 nvidia,sis_agp
snd                    54020  15 snd_mpu401,snd_au8830,snd_mpu401_uart,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
i2c_sis96x              6532  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_sis96x
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
8139too                27648  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
pata_sis               14732  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  1 libata
sis5513                14856  0 [permanent]
floppy                 59524  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  5 usbhid,ehci_hcd,uhci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

---

### Post by stronzo420 on 2008-02-13
So it turns out that changing the options snd-usb-audio index=2 didn't really change anything in my setup. The popping I heard when I turned on the computer is still happening even now that i reverted the change.

So this is just a plain old sound problem, I don't have sound, forget the mouse :-) Any ideas?

---

