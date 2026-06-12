---
title: "Unable to record in nvidia MCP61 (Realtek ALC888)"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by octaedro7 on 2007-07-24
I've been trying to record audio or use skype with my nvidia onboard sound card, about two month from now to no avail. I've tryied loads of different solutions but still I cannot record.
I'm running ALSA drivers 1.0.1.4rc1 with hda-intel module as adviced on nvidia's site (they say hda-intel.c though???).  I can monitor mic input but not record it.
More info below:


cabron@bicefalo-studio:~$ aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
cabron@bicefalo-studio:~$ lspci -v
```

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0888
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ddef8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```
cabron@bicefalo-studio:~$ lspci |grep Audio
```

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

```
cabron@bicefalo-studio:~$ cat /proc/asound/card0/codec#0 | grep -i codec
```

Codec: Realtek ALC888

```
cabron@bicefalo-studio:~$ lsmod
```

Module                  Size  Used by
ipv6                  274080  10 
binfmt_misc            13064  1 
rfcomm                 41752  0 
l2cap                  26112  5 rfcomm
bluetooth              57444  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7488  0 
cpufreq_ondemand        9356  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12164  0 
container               5248  0 
dock                   10424  0 
ac                      6020  0 
video                  16260  0 
asus_acpi              17308  0 
sbs                    15528  0 
battery                10756  0 
backlight               6784  1 asus_acpi
button                  8720  0 
i2c_ec                  6016  1 sbs
nls_utf8                3072  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    54044  1 vfat
ndiswrapper           199408  0 
fuse                   46996  15 
lp                     12548  0 
snd_hda_intel         262680  7 
snd_pcm_oss            45184  0 
snd_mixer_oss          18176  1 snd_pcm_oss
snd_pcm                81284  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35584  0 
snd_seq_midi            9728  0 
snd_rawmidi            26240  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54640  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24708  4 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               4714420  32 
af_packet              24072  8 
agpgart                35788  1 nvidia
snd                    57092  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9440  1 snd
psmouse                38792  0 
pcspkr                  4224  0 
serio_raw               7940  0 
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
i2c_core               23424  2 i2c_ec,nvidia
parport_pc             36644  1 
parport                37576  3 ppdev,lp,parport_pc
k8temp                  6656  0 
shpchp                 34324  0 
pci_hotplug            33608  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  134152  4 
jbd                    63528  1 ext3
mbcache                 9604  1 ext3
sg                     35996  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sd_mod                 23556  15 
usbhid                 26720  0 
hid                    27392  1 usbhid
generic                 5124  0 [permanent]
amd74xx                15260  0 [permanent]
ohci_hcd               22660  0 
ehci_hcd               34316  0 
forcedeth              46600  0 
sata_nv                21124  13 
ata_generic             9092  0 
libata                125848  2 sata_nv,ata_generic
scsi_mod              143116  3 sg,sd_mod,libata
usbcore               135048  5 ndiswrapper,usbhid,ohci_hcd,ehci_hcd
thermal                14856  0 
processor              31560  1 thermal
fan                     5636  0 
fbcon                  43296  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```
cabron@bicefalo-studio:~$ modinfo snd_hda_intel
```

filename:       /lib/modules/2.6.20-16-lowlatency/updates/alsa/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     69D244CEAA470298E0754E0
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd,snd
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           index:Index value for Intel HD audio interface. (int)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           model:Use the given board model. (charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           enable:bool

```
cabron@bicefalo-studio:~$ hwinfo --sound
```

16: PCI 05.0: 0403 Audio device                                 
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_10de_3f0
  Unique ID: CvwD.NrGvVZjpct4
  SysFS ID: /devices/pci0000:00/0000:00:05.0
  SysFS BusID: 0000:00:05.0
  Hardware Class: sound
  Model: "ASRock In Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f0 
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x0888 
  Revision: 0xa2
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xddef8000-0xddefbfff (rw,non-prefetchable)
  IRQ: 17 (471640 events)
  Module Alias: "pci:v000010DEd000003F0sv00001849sd00000888bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

By the way, Have no problems with playback, haven't tried 7.1 though.
Any clues of what's wrong?
is there anyone who have succeded in record audio with this chipset?

Tnx in advance

---

### Post by Yellow Pasque on 2007-07-24
Is it possible that it's muted?

I'd also recommend upgrading to the latest ALSA version (1.0.14). There have been A LOT of fixes.

---

### Post by octaedro7 on 2007-07-24
Everything unmuted of course.  I'm in fact using alsa driver 1.0.14, alsa lib 1.0.14.a, alsa utils 1.0.14

---

### Post by ANTDx1 on 2007-11-18
I am also using this sound system and having the same recording problem,  Anyone have any ideas?

---

### Post by Scott Carlson on 2007-12-10
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

I finally got my audio FULLY working, fixed for playback and record.  I had just got a new computer with Gigabyte  motherboard part# GA-M61SME-S2L.  with an AMD Athlon 64x2 4200+  It has an on board audio that uses the kernel sound driver snd-hda-intel.ko.  I had installed the latest  Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007.   Out of the box I had audio out but was not able to record audio.   I needed to be able to record to be able to use my skype.  With some research I see that many people where having this same problem or even worse but no easy solution.    I now have a fully working record and playback after downloading and installing the new version of alsa drive alsa-driver-1.0.15rc3.  I downloaded the driver from [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2).  I didn't update any of the other alsa stuff (maybe I should?) .  It still has  alsa-1.0.14 installed for the rest.  After that was installed it was just a mater of setting the mixer settings to the audio levels needed.  I also had to reboot my computer after the driver was installed.  I see in the Ubuntu 7.10 release they seem to have some costume driver for the snd-hda-intel.ko in the kernel.  It must have the record disabled for some reason.  Any way I just got it working today so I will just have to see how stable it is in the future.  There may be a reason they disabled it.  I never looked at the code.  Here is a lspci of whats inside my computer:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

I hope this will at least give you hope that you can make that MCP61 audio card/motherboard work.
 
  Good Luck to you all and thanks to all of you that have helped me.
     Scott Carlson
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFHXNwXWiRZJDu3utwRAi7EAJ0TExHLzyCttzg1Xo4qbK0s+IQr1ACePQqU
CR7thFK5XPzFouLCzP2naBQ=
=f0fS
-----END PGP SIGNATURE-----

---

