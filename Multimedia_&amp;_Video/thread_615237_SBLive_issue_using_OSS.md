---
title: "SBLive issue using OSS"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by gad241 on 2007-11-16
Have been trying to get the SBLive card to produce sound using OSS. Was trying to configure the card under Alsa but Alsa couldn't detect the card. Posted is some information that may provide someone some insight to my problem```
07)
        Subsystem: Creative Labs CT4760 SBLive!
        Flags: medium devsel
        I/O ports at 1000 [size=32]
        Capabilities: [dc] Power Management version 1

00:14.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at fff0 [size=8]
        Capabilities: [dc] Power Management version 1

```

```
glen@glen-desktop:~$ ossinfo
Version info: OSS 4.0 (b1009/200711130545) (0x00040003) 
Platform: Linux/i686 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 (glen-desktop)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects
 0: osscore0 OSS core services
 1: sblive0 
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support

MIDI devices (/dev/midi*)

Mixer devices (/dev/mixer*)

Audio devices

```

Ubuntu 7.04

---

### Post by Yellow Pasque on 2007-11-17
It looks like you did not install OSS correctly. Try booting into the recovery kernel and running [CIOE]sudo soundon[/CODE]

---

### Post by gad241 on 2007-11-17
Thanks Temujin for the reply. Jumped out to failsafe terminal, entered "sudo soundon" and machine reported OSS is already loaded. I had entered this command via terminal under Xserver. I followed your instruction on loading OSS. It was pretty straight forward. Doing a "ossinfo" returns the same results from my previous post. Would you like to see more system info?

---

### Post by gad241 on 2007-11-17
For more infomation I have posted "lsmod" results.```
glen@glen-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vmix                   14132  0 
ossusb                 56072  0 
sblive                 92016  0 
osscore               569396  3 vmix,ossusb,sblive
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
apm                    22752  2 
ppdev                  10116  0 
ipv6                  268960  8 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sg                     36252  0 
sd_mod                 23428  2 
af_packet              23816  2 
lp                     12452  0 
fuse                   46612  0 
usb_storage            72256  1 
libusual               17936  1 usb_storage
at76_usb               95076  0 
nvidia               3930348  8 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
serio_raw               7940  0 
amd_k7_agp              9868  1 
psmouse                38920  0 
i2c_amd756              7684  0 
agpgart                35400  2 nvidia,amd_k7_agp
i2c_core               22656  1 i2c_amd756
emu10k1_gp              4736  0 
ac97_bus                3200  0 
gameport               16520  2 emu10k1_gp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  1 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
floppy                 59524  0 
ohci_hcd               22532  0 
usbcore               134280  6 ossusb,usb_storage,libusual,at76_usb,ohci_hcd
amd74xx                15260  0 [permanent]
generic                 5124  0 [permanent]
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

