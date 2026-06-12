---
title: "Volume Control problem (possibly after update)"
date: 2009-04-08
forum: Multimedia Software
---

### Post by ekidd91 on 2009-04-08
So yesterday I let my system install all the updates it wanted (there weren't too many but I, stupidly, didn't check what hey all were). Now, today, when I load up my system, I get no sound.

 - When I click on Volume Control I get an error message [screenshot attached]
 - When I try to 'Open Volume Control' after right clicking I get an error message.
 - When I try typing 'alsamixer' into terminal it tells me that there are "No mixer elems found".
 - When I open Rhythmbox and try to play any file it freezes and I have to Force Quit.

From left to right in screenshot: Terminal; Volume Control error 1; Volume control error 2.

Hope someone can help,
thanks.

---

### Post by MaindotC on 2009-04-08
Paste output of lsmod and lspci.

---

### Post by ekidd91 on 2009-04-08
Output of lsmod:
```
Module                  Size  Used by
snd_hwdep              15236  0 
snd_util_mem           12416  0 
snd_pcm_oss            46848  0 
snd_pcm                83204  1 snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
ipv6                  263972  8 
af_packet              25728  2 
binfmt_misc            16904  1 
bridge                 56980  0 
rfcomm                 44560  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
pci_slot               12680  0 
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
video                  25232  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
ac97_bus                9856  0 
evdev                  17696  6 
nvidia               4717332  22 
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
serio_raw              13444  0 
psmouse                45200  0 
i2c_sis96x             12420  0 
emu10k1_gp             10880  0 
sis_agp                15232  1 
button                 14224  0 
pcspkr                 10624  0 
gameport               19468  2 emu10k1_gp
agpgart                42184  2 nvidia,sis_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
i2c_core               31892  2 nvidia,i2c_sis96x
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ohci1394               37936  0 
pata_sis               18436  2 
ieee1394               96324  2 sbp2,ohci1394
sis900                 27904  0 
mii                    13440  1 sis900
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  3 pata_acpi,ata_generic,pata_sis
usbcore               149488  3 ohci_hcd,ehci_hcd
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

Output of lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

```

---

### Post by Zeedok on 2009-04-08
Same problems here.  Here is my lsmod and lspci


lsmod
```
Module                  Size  Used by
snd_pcm_oss            52256  0 
snd_pcm                98696  1 snd_pcm_oss
snd_page_alloc         18576  1 snd_pcm
snd_mixer_oss          25088  1 snd_pcm_oss
snd_seq_dummy          11652  0 
snd_seq_oss            40704  0 
snd_seq_midi           15808  0 
snd_rawmidi            34336  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67616  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33424  2 snd_pcm,snd_seq
snd_seq_device         16660  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    83400  9 snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
af_packet              29568  2 
binfmt_misc            18700  1 
sco                    20612  2 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 sco,rfcomm,bnep,l2cap
vboxdrv              1653120  0 
ppdev                  17032  0 
ipv6                  314312  39 
acpi_cpufreq           16400  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
cpufreq_userspace      12420  0 
cpufreq_ondemand       16400  2 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
video                  29204  0 
output                 11776  1 video
wmi                    15808  0 
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
isofs                  43944  0 
udf                    93480  0 
crc_itu_t              10496  1 udf
xfs                   575376  1 
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                49968  3 ppdev,parport_pc,lp
dvb_usb_dib0700        48136  19 
dib7000p               27528  3 dvb_usb_dib0700
dib7000m               26116  1 dvb_usb_dib0700
dvb_usb                27276  1 dvb_usb_dib0700
dvb_core               99628  1 dvb_usb
lirc_imon              26888  2 
dib3000mc              22408  1 dvb_usb_dib0700
lirc_dev               22216  1 lirc_imon
joydev                 20736  0 
dibx000_common         12292  3 dib7000p,dib7000m,dib3000mc
nvidia               7964296  26 
evdev                  20512  7 
dib0070                16900  3 dvb_usb_dib0700
i2c_core               36000  8 dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,nvidia,dib0070
shpchp                 42140  0 
iTCO_wdt               21072  0 
pcspkr                 11136  0 
iTCO_vendor_support    12420  1 iTCO_wdt
pci_hotplug            39216  1 shpchp
button                 15904  0 
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47656  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_acpi              13568  0 
usbhid                 39648  0 
hid                    58944  1 usbhid
ata_piix               29444  3 
ata_generic            14212  0 
uhci_hcd               34336  0 
ehci_hcd               49420  0 
libata                201184  3 pata_acpi,ata_piix,ata_generic
scsi_mod              183288  4 sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
r8169                  40452  0 
mii                    14592  1 r8169
usbcore               175760  8 dvb_usb_dib0700,dvb_usb,lirc_imon,usbhid,uhci_hcd,ehci_hcd
thermal                27552  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  1 

```

and lspci

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

Also attached are some screenshots with the error messages in case that's useful.

Thanks

---

### Post by MaindotC on 2009-04-08
ekkid, from googling this seems to be an issue with "Audigy Analog/Digital Output Jack".  I don't have a creative labs card so bear with me as I'm not certain what your audio properties look like.  You can make this visible by right-clicking on the Volume Control and selecting "Open Volume Control".  Then you need to select "Edit -> Preferences" and see which one of those switches shows the Audigy Analog/Digital Output Jack and enable/disable it to see if that helps.

---

### Post by MaindotC on 2009-04-08
Zeedok I think you need to try a different audio driver.  Can you go to System -> Preferences -> Sound and try selecting different audio drivers like Pulse or Alsa for your audio devices and clicking "Test"?

---

### Post by ekidd91 on 2009-04-08
> **strAlan said:**
> ekkid, from googling this seems to be an issue with "Audigy Analog/Digital Output Jack".  I don't have a creative labs card so bear with me as I'm not certain what your audio properties look like.  You can make this visible by right-clicking on the Volume Control and selecting "Open Volume Control".  Then you need to select "Edit -> Preferences" and see which one of those switches shows the Audigy Analog/Digital Output Jack and enable/disable it to see if that helps.

I'm unable to 'Open Volume Control' (see error message 2 in original post). I've had my soundblaster working for months, so I doubt if it's a hardware problem.

---

### Post by Zeedok on 2009-04-08
I agree with ekidd91 - on both counts.  I can't open preferences and my hardware is < 1 month old.  When I open "System -> Preferences -> Sound" I can't see the checkbox you're talking about.

Also, I have tried other drivers but they all give me the same error message (see my attached screenshots)

Thanks - keep the suggestions coming . . .

---

### Post by MaindotC on 2009-04-08
I'm certain it's not a hardware problem either - it really seems to just be a setting or a configuration.  If you can't access the configuration changes from the gui, then you should try replicating the same configuration changes in the command line.  Everything has a command line equivalent.  [This link](http://www.mepis.org/docs/en/index.php/Sound_Driver_Database#Creative_Labs) says you should be using the snd-ca0106 driver and I don't see it listed in your output.  This is a different distribution but it appears to be a supported driver independent of the distribution.  Can you try modprobe'ing it?

---

### Post by Zeedok on 2009-04-08
Sorry, rusty on my CLI, you mean:

```
sudo modprobe snd-ca0106
```

right?

---

### Post by MaindotC on 2009-04-08
That's correct.  You can make sure you have this module, or any others you want to try, by typing:
```

sudo modprobe -l

```
and you can attach "grep" to look for a specific module.  In this case snd-ca0106.  Try inserting that.

Zeedok this is not for you!  You are using an Intel card which should use a different driver.  The snd-ca0106 driver is for Creative Labs.  You need to try Intel drivers because you have an Intel chipset for your audio card.  Try modprobing the drivers listed from:
```

sudo modprobe -l | grep intel

```
I think you're supposed to be using the snd_hda driver (or other varian) which I don't see listed in your lsmod output.

---

### Post by Zeedok on 2009-04-08
I was poking around posts where people had problems with my Sound device and people edited /etc/modprobe.d/alsa-base - I thought I would show you my current /etc/modprobe.d/alsa-base in case it gives you some ideas:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by MaindotC on 2009-04-08
modprobe.d is just the configuration that instructs which drivers to be loaded on startup.  I suggest you try loading the drivers manually with modprobe and then once you find one that works you can add it to alsa-base or modprobe.conf.

---

### Post by Zeedok on 2009-04-08
Here's the output from my:

```
sudo modprobe -l | grep intel
```

It looks like there is an "snd-hda-intel" driver there (line 3)??

```
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/misc/intel_menlow.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/mtd/maps/intel_vr_nor.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/char/agp/intel-agp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/char/hw_random/intel-rng.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/video/intelfb/intelfb.ko
/lib/modules/2.6.27-11-generic/kernel/arch/x86/kvm/kvm-intel.ko
```

---

### Post by ekidd91 on 2009-04-08
output of sudo modprobe snd-ca0106:

```
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.27-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.27-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by Zeedok on 2009-04-08
Temporary fix - I chose the older kernel at the GRUB menu and the sound works properly.  Here is the "sudo modprobe -l | grep intel output".  It's the same isn't it? EDIT - NO it's not the same, on this one there is no

```
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
```


```
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/misc/intel_menlow.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/maps/intel_vr_nor.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/char/agp/intel-agp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/char/hw_random/intel-rng.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/video/intelfb/intelfb.ko
/lib/modules/2.6.27-7-generic/kernel/arch/x86/kvm/kvm-intel.ko
```

---

### Post by frodon on 2009-04-08
Have you filled a launchpad bug report ?

---

### Post by Zeedok on 2009-04-08
> **frodon said:**
> Have you filled a launchpad bug report ?

Not yet.  Will do when I get a chance.

---

### Post by Zeedok on 2009-04-08
> **frodon said:**
> Have you filled a launchpad bug report ?

Not yet.  Will do when I get a chance.

EDIT [Looks like it has already been filed]("https://bugs.launchpad.net/ubuntu/+bug/357373") - contrary to the title it has not been solved.

---

### Post by MaindotC on 2009-04-08
Just so you know, the modprobe -l command is just listing what modules (drivers) you have available on your system.  I mentioned that command because this way you can esure it's present on your system.  If it wasn't you'd have to install it but it looks like you have a bunch of drivers for the intel audio card present (as most distributions do).  Zeedok, since it seems to be relative to a kernel upgrade then a bug report is definitely the way to go - they can help much more than I'll EVER be able to help.

ekidd when you receive that error message can you post the output of dmesg or /var/log/messages?  It's a log of a bunch of messages, so just look for the time period that correlates to when you tried inserting that module.

---

### Post by ekidd91 on 2009-04-08
> **strAlan said:**
> ekidd when you receive that error message can you post the output of dmesg or /var/log/messages?  It's a log of a bunch of messages, so just look for the time period that correlates to when you tried inserting that module.

which error message?

How do i get the output of those folders/files? Sorry, despite having been running ubuntu for several months i'm still a bit of a linux newbie.

---

### Post by MaindotC on 2009-04-08
The error message related to your previous post - post #15.  In that error it says "see dmesg" which is a command that posts the output of /var/log/messages.  Can you post the output of what is in /var/log/messages at the time you tried to load that module?  If not, could you try loading the module again and then quick go to /var/log/messages and post the output?

---

### Post by ekidd91 on 2009-04-09
After running sudo modprobe snd-ca0106 i used 'dmesg' and got the following (I didn't know how much to copy in sorry):

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781d000 - 37fef5a4
[    0.000000] ACPI: RSDP 000FAA40, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 3FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 3FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 3FFF0120, 3300 (r1    SiS      746      100 INTL  2002024)
[    0.000000] ACPI: FACS 3FFF8000, 0040
[    0.000000] ACPI: APIC 3FFF00C0, 005A (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fef5a4]          RAMDISK ==> [003781d000 - 0037fef5a4]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00fbc70] 000fbc70
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32464 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259711
[    0.000000] Kernel command line: root=UUID=44c7b725-2602-4ae2-aa3f-1b0e11d7dc5f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1679.107 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024680k/1048512k available (2576k kernel code, 22992k reserved, 1164k data, 424k init, 131008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03843ea   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 3358.21 BogoMIPS (lpj=6716428)
[    0.004062] Security Framework initialized
[    0.004077] SELinux:  Disabled at boot.
[    0.004130] AppArmor: AppArmor initialized
[    0.004144] Mount-cache hash table entries: 512
[    0.004458] Initializing cgroup subsys ns
[    0.004465] Initializing cgroup subsys cpuacct
[    0.004469] Initializing cgroup subsys memory
[    0.004495] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004499] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004526] Checking 'hlt' instruction... OK.
[    0.020470] SMP alternatives: switching to UP code
[    0.027566] Freeing SMP alternatives: 11k freed
[    0.027574] ACPI: Core revision 20080609
[    0.029858] ACPI: Checking initramfs for custom DSDT
[    0.425161] ENABLING IO-APIC IRQs
[    0.425344] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.465034] CPU0: AMD Athlon(tm) XP 2000+ stepping 02
[    0.468029] Brought up 1 CPUs
[    0.468029] Total of 1 processors activated (3358.21 BogoMIPS).
[    0.468029] CPU0 attaching NULL sched-domain.
[    0.468029] net_namespace: 840 bytes
[    0.468029] Booting paravirtualized kernel on bare hardware
[    0.468029] Time: 16:20:37  Date: 04/09/09
[    0.468029] NET: Registered protocol family 16
[    0.468029] EISA bus registered
[    0.468029] ACPI: bus type pci registered
[    0.468029] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[    0.468029] PCI: Using configuration type 1 for base access
[    0.469207] ACPI: EC: Look up EC in DSDT
[    0.476735] ACPI: Interpreter enabled
[    0.476742] ACPI: (supports S0 S1 S4 S5)
[    0.476763] ACPI: Using IOAPIC for interrupt routing
[    0.484215] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.484347] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d3ffffff]
[    0.484495] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.484544] PCI: 0000:00:02.1 reg 20 io port: [c00, c1f]
[    0.484608] PCI: 0000:00:02.5 reg 20 io port: [ff00, ff0f]
[    0.484650] PCI: 0000:00:03.0 reg 10 32bit mmio: [cfffd000, cfffdfff]
[    0.484710] PCI: 0000:00:03.1 reg 10 32bit mmio: [cfffe000, cfffefff]
[    0.484784] PCI: 0000:00:03.2 reg 10 32bit mmio: [cffff000, cfffffff]
[    0.484835] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.484841] pci 0000:00:03.2: PME# disabled
[    0.484883] PCI: 0000:00:04.0 reg 10 io port: [d800, d8ff]
[    0.484892] PCI: 0000:00:04.0 reg 14 32bit mmio: [cfffc000, cfffcfff]
[    0.484923] PCI: 0000:00:04.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.484940] pci 0000:00:04.0: supports D1
[    0.484943] pci 0000:00:04.0: supports D2
[    0.484945] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484951] pci 0000:00:04.0: PME# disabled
[    0.484992] PCI: 0000:00:0a.0 reg 10 io port: [d400, d43f]
[    0.485041] pci 0000:00:0a.0: supports D1
[    0.485043] pci 0000:00:0a.0: supports D2
[    0.485075] PCI: 0000:00:0a.1 reg 10 io port: [dc00, dc07]
[    0.485125] pci 0000:00:0a.1: supports D1
[    0.485127] pci 0000:00:0a.1: supports D2
[    0.485162] PCI: 0000:00:0a.2 reg 10 32bit mmio: [cfffb800, cfffbfff]
[    0.485171] PCI: 0000:00:0a.2 reg 14 32bit mmio: [cfff4000, cfff7fff]
[    0.485216] pci 0000:00:0a.2: supports D1
[    0.485219] pci 0000:00:0a.2: supports D2
[    0.485221] pci 0000:00:0a.2: PME# supported from D0 D1 D2 D3hot
[    0.485227] pci 0000:00:0a.2: PME# disabled
[    0.485308] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.485316] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, c7ffffff]
[    0.485323] PCI: 0000:01:00.0 reg 18 32bit mmio: [cdb80000, cdbfffff]
[    0.485343] PCI: 0000:01:00.0 reg 30 32bit mmio: [cfee0000, cfefffff]
[    0.485400] PCI: bridge 0000:00:01.0 32bit mmio: [cdd00000, cfefffff]
[    0.485407] PCI: bridge 0000:00:01.0 32bit mmio pref: [bd900000, cdbfffff]
[    0.485417] bus 00 -> node 0
[    0.485427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.504914] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.505109] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.505290] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.505470] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.505651] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.505845] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.506028] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506208] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.506399] ACPI: Power Resource [URP1] (off)
[    0.506449] ACPI: Power Resource [URP2] (off)
[    0.506499] ACPI: Power Resource [FDDP] (off)
[    0.506548] ACPI: Power Resource [LPTP] (off)
[    0.506677] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.506738] pnp: PnP ACPI init
[    0.506752] ACPI: bus type pnp registered
[    0.511340] pnp: PnP ACPI: found 12 devices
[    0.511346] ACPI: ACPI bus type pnp unregistered
[    0.511352] PnPBIOS: Disabled by ACPI PNP
[    0.512068] PCI: Using ACPI for IRQ routing
[    0.512266] NET: Registered protocol family 8
[    0.512266] NET: Registered protocol family 20
[    0.512266] NetLabel: Initializing
[    0.512266] NetLabel:  domain hash size = 128
[    0.512266] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.512266] NetLabel:  unlabeled traffic allowed by default
[    0.512565] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.512568]    actual entries 65620
[    0.512921] AppArmor: AppArmor Filesystem Enabled
[    0.512949] ACPI: RTC can wake from S4
[    0.512968] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.512968] system 00:01: ioport range 0x295-0x296 has been reserved
[    0.512968] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.512968] system 00:01: ioport range 0x880-0x8ff has been reserved
[    0.512968] system 00:01: ioport range 0xc00-0xc1f has been reserved
[    0.512968] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.548901] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.548905] pci 0000:00:01.0:   IO window: disabled
[    0.548914] pci 0000:00:01.0:   MEM window: 0xcdd00000-0xcfefffff
[    0.548920] pci 0000:00:01.0:   PREFETCH window: 0x000000bd900000-0x000000cdbfffff
[    0.548942] bus: 00 index 0 io port: [0, ffff]
[    0.548945] bus: 00 index 1 mmio: [0, ffffffff]
[    0.548948] bus: 01 index 0 mmio: [0, 0]
[    0.548950] bus: 01 index 1 mmio: [cdd00000, cfefffff]
[    0.548953] bus: 01 index 2 mmio: [bd900000, cdbfffff]
[    0.548956] bus: 01 index 3 mmio: [0, 0]
[    0.548980] NET: Registered protocol family 2
[    0.549177] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.549745] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.552514] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.553878] TCP: Hash tables configured (established 131072 bind 65536)
[    0.553886] TCP reno registered
[    0.554106] NET: Registered protocol family 1
[    0.554323] checking if image is initramfs... it is
[    1.052092] Switched to high resolution mode on CPU 0
[    1.435632] Freeing initrd memory: 8009k freed
[    1.437005] audit: initializing netlink socket (disabled)
[    1.437038] type=2000 audit(1239294037.436:1): initialized
[    1.443837] highmem bounce pool size: 64 pages
[    1.443850] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.447485] VFS: Disk quotas dquot_6.5.1
[    1.447639] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.447848] msgmni has been set to 1761
[    1.448156] io scheduler noop registered
[    1.448159] io scheduler anticipatory registered
[    1.448162] io scheduler deadline registered
[    1.448179] io scheduler cfq registered (default)
[    1.448277] pci 0000:01:00.0: Boot video device
[    1.449289] isapnp: Scanning for PnP cards...
[    1.802773] isapnp: No Plug & Play device found
[    1.869214] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.869398] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.870679] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.873532] brd: module loaded
[    1.873658] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.873881] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.874275] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.874283] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.875285] mice: PS/2 mouse device common for all mice
[    1.875521] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.875551] rtc0: alarms up to one year
[    1.875762] EISA: Probing bus 0 at eisa.0
[    1.875804] EISA: Detected 0 cards.
[    1.875809] cpuidle: using governor ladder
[    1.875813] cpuidle: using governor menu
[    1.876602] TCP cubic registered
[    1.876652] Using IPI No-Shortcut mode
[    1.877094] registered taskstats version 1
[    1.877262]   Magic number: 5:630:337
[    1.877325] tty ttyzc: hash matches
[    1.877510] tty tty58: hash matches
[    1.877610] rtc_cmos 00:03: setting system clock to 2009-04-09 16:20:38 UTC (1239294038)
[    1.877616] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.877618] EDD information not available.
[    1.878461] Freeing unused kernel memory: 424k freed
[    1.878541] Write protecting the kernel text: 2580k
[    1.878592] Write protecting the kernel read-only data: 940k
[    1.897253] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.216068] fuse init (API version 7.9)
[    2.348130] processor ACPI0007:00: registered as cooling_device0
[    3.190624] No dock devices found.
[    3.321578] SCSI subsystem initialized
[    3.349891] usbcore: registered new interface driver usbfs
[    3.349952] usbcore: registered new interface driver hub
[    3.377965] usbcore: registered new device driver usb
[    3.388277] sis900.c: v1.08.10 Apr. 2 2006
[    3.388366] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.389441] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    3.400200] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.414571] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, 00:13:8f:fa:12:40
[    3.444306] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.444335] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    3.444434] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    3.444493] ehci_hcd 0000:00:03.2: cache line size of 64 is not supported
[    3.444518] ehci_hcd 0000:00:03.2: irq 23, io mem 0xcffff000
[    3.448757] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.473433] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.473787] usb usb1: configuration #1 chosen from 1 choice
[    3.473830] hub 1-0:1.0: USB hub found
[    3.473858] hub 1-0:1.0: 6 ports detected
[    3.491213] libata version 3.00 loaded.
[    3.576629] pata_sis 0000:00:02.5: version 0.5.2
[    3.577508] scsi0 : pata_sis
[    3.577756] scsi1 : pata_sis
[    3.578936] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.578942] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.748480] ata1.00: ATA-7: Maxtor 6Y060L0, YAR41VW0, max UDMA/133
[    3.748488] ata1.00: 120103200 sectors, multi 16: LBA 
[    3.750114] ata1.01: ATA-7: Maxtor 6L200P0, BAJ41G20, max UDMA/133
[    3.750121] ata1.01: 398297088 sectors, multi 16: LBA48 
[    3.764492] ata1.00: configured for UDMA/133
[    3.781895] ata1.01: configured for UDMA/133
[    3.952429] ata2.00: ATAPI: PIONEER DVD-RW  DVR-110D, 1.08, max UDMA/66
[    3.952462] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[    3.968437] ata2.00: configured for UDMA/66
[    3.984397] ata2.01: configured for UDMA/33
[    3.984652] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5
[    3.984865] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L200P0   BAJ4 PQ: 0 ANSI: 5
[    3.991504] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.08 PQ: 0 ANSI: 5
[    3.995392] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    3.995618] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.995646] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.995691] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.995734] ohci_hcd 0000:00:03.0: irq 20, io mem 0xcfffd000
[    4.050454] usb usb2: configuration #1 chosen from 1 choice
[    4.050514] hub 2-0:1.0: USB hub found
[    4.050538] hub 2-0:1.0: 3 ports detected
[    4.152596] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.152628] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    4.152670] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    4.152723] ohci_hcd 0000:00:03.1: irq 21, io mem 0xcfffe000
[    4.210431] usb usb3: configuration #1 chosen from 1 choice
[    4.210479] hub 3-0:1.0: USB hub found
[    4.210503] hub 3-0:1.0: 3 ports detected
[    4.312613] ohci1394 0000:00:0a.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.362494] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfffb800-cfffbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.702758] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.702824] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    4.702885] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    4.702945] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    4.752313] Driver 'sd' needs updating - please use bus_type methods
[    4.753113] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[    4.753144] sd 0:0:0:0: [sda] Write Protect is off
[    4.753148] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.753185] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.753313] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[    4.753334] sd 0:0:0:0: [sda] Write Protect is off
[    4.753338] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.753372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.753379]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    4.785889]  sda5 >
[    4.786181] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.786346] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    4.786374] sd 0:0:1:0: [sdb] Write Protect is off
[    4.786378] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.786415] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.786500] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    4.786522] sd 0:0:1:0: [sdb] Write Protect is off
[    4.786526] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.786560] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.786567]  sdb: sdb1
[    4.807995] sd 0:0:1:0: [sdb] Attached SCSI disk
[    4.839086] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.839097] Uniform CD-ROM driver Revision: 3.20
[    4.839321] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.846972] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    4.847141] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.016765] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    5.016774] ata1.00: BMDMA stat 0x64
[    5.016783] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[    5.016786]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[    5.016790] ata1.00: status: { DRDY ERR }
[    5.016794] ata1.00: error: { ICRC ABRT }
[    5.016829] ata1: soft resetting link
[    5.641585] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510ec592]
[    8.340394] ata1.00: configured for UDMA/133
[    8.357766] ata1.01: configured for UDMA/133
[    8.357787] ata1: EH complete
[    8.444298] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[    8.445747] sd 0:0:0:0: [sda] Write Protect is off
[    8.445753] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.446630] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.447029] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    8.447226] sd 0:0:1:0: [sdb] Write Protect is off
[    8.447230] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    8.468282] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.472047] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[    8.472601] sd 0:0:0:0: [sda] Write Protect is off
[    8.472607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.472659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.472711] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    8.472732] sd 0:0:1:0: [sdb] Write Protect is off
[    8.472736] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    8.472771] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.652574] PM: Starting manual resume from disk
[    8.652583] PM: Resume from partition 8:5
[    8.652586] PM: Checking hibernation image.
[    8.652983] PM: Resume from disk failed.
[    8.686922] EXT3-fs: INFO: recovery required on readonly filesystem.
[    8.686930] EXT3-fs: write access will be enabled during recovery.
[   13.827105] kjournald starting.  Commit interval 5 seconds
[   13.827148] EXT3-fs: sda1: orphan cleanup on readonly fs
[   13.827163] ext3_orphan_cleanup: deleting unreferenced inode 500915
[   13.827262] ext3_orphan_cleanup: deleting unreferenced inode 500913
[   13.862661] ext3_orphan_cleanup: deleting unreferenced inode 500907
[   13.872284] ext3_orphan_cleanup: deleting unreferenced inode 500770
[   13.877548] EXT3-fs: sda1: 4 orphan inodes deleted
[   13.877552] EXT3-fs: recovery complete.
[   13.910818] EXT3-fs: mounted filesystem with ordered data mode.
[   24.495200] udevd version 124 started
[   26.070018] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.232321] Linux agpgart interface v0.103
[   26.542348] agpgart-sis 0000:00:00.0: SiS chipset [1039/0741]
[   26.549276] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   26.715011] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.772158] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xdc00, speed 1217kHz
[   26.824334] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   26.824345] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[   26.824349] ACPI: Device needs an ACPI driver
[   26.913223] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.960451] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   26.972077] ACPI: Power Button (FF) [PWRF]
[   26.972295] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   26.992210] ACPI: Power Button (CM) [PWRB]
[   28.069022] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   28.100248] parport_pc 00:0a: reported by Plug and Play ACPI
[   28.100359] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   28.420053] nvidia: module license 'NVIDIA' taints kernel.
[   29.236894] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.241981] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
[   59.364052] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   59.364068] ata1.01: cmd 25/00:08:f0:87:bd/00:00:17:00:00/f0 tag 0 dma 4096 in
[   59.364070]          res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[   59.364075] ata1.01: status: { DRDY }
[   59.364113] ata1: soft resetting link
[   59.552402] ata1.00: configured for UDMA/133
[   59.569770] ata1.01: configured for UDMA/133
[   59.569788] ata1: EH complete
[   59.580050] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   59.618821] sd 0:0:0:0: [sda] Write Protect is off
[   59.618828] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.658939] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.691884] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[   59.713616] sd 0:0:1:0: [sdb] Write Protect is off
[   59.713625] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   59.713673] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.713726] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   59.713748] sd 0:0:0:0: [sda] Write Protect is off
[   59.713752] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.713787] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.713819] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[   59.713839] sd 0:0:1:0: [sdb] Write Protect is off
[   59.713843] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   59.713876] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.716051] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   89.716069] ata1.01: cmd c8/00:08:00:02:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   89.716071]          res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[   89.716076] ata1.01: status: { DRDY }
[   89.716113] ata1: soft resetting link
[   89.904391] ata1.00: configured for UDMA/133
[   89.921768] ata1.01: configured for UDMA/133
[   89.921782] ata1: EH complete
[   89.941487] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   89.959895] sd 0:0:0:0: [sda] Write Protect is off
[   89.959906] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.959981] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.960108] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[   89.960131] sd 0:0:1:0: [sdb] Write Protect is off
[   89.960135] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   89.960170] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.960205] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   89.960226] sd 0:0:0:0: [sda] Write Protect is off
[   89.960230] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.960264] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.960297] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[   89.960317] sd 0:0:1:0: [sdb] Write Protect is off
[   89.960321] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   89.960354] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  119.972049] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  119.972066] ata1.01: cmd c8/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 dma 16384 in
[  119.972069]          res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[  119.972073] ata1.01: status: { DRDY }
[  119.972111] ata1: soft resetting link
[  120.160393] ata1.00: configured for UDMA/133
[  120.177775] ata1.01: configured for UDMA/133
[  120.177789] ata1: EH complete
[  150.176024] ata1.01: limiting speed to UDMA/100:PIO4
[  150.176030] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  150.176038] ata1.01: cmd c8/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 dma 16384 in
[  150.176040]          res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[  150.176044] ata1.01: status: { DRDY }
[  150.176071] ata1: soft resetting link
[  150.364393] ata1.00: configured for UDMA/133
[  150.381793] ata1.01: configured for UDMA/100
[  150.381801] ata1: EH complete
[  150.381896] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  150.400927] sd 0:0:0:0: [sda] Write Protect is off
[  150.400932] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  150.436228] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  150.445100] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  150.448212] sd 0:0:1:0: [sdb] Write Protect is off
[  150.448217] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  150.448618] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  150.448670] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  150.448692] sd 0:0:0:0: [sda] Write Protect is off
[  150.448697] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  150.448733] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  150.448766] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  150.448787] sd 0:0:1:0: [sdb] Write Protect is off
[  150.448790] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  150.448824] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  150.887293] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  150.887306] snd_ac97_codec: Unknown symbol ac97_bus_type
[  150.935901] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  150.935914] snd_ac97_codec: Unknown symbol ac97_bus_type
[  150.959570] snd_emu10k1: Unknown symbol snd_ac97_write_cache
[  150.959929] snd_emu10k1: Unknown symbol snd_ac97_resume
[  150.961414] snd_emu10k1: Unknown symbol snd_ac97_mixer
[  150.961798] snd_emu10k1: Unknown symbol snd_ac97_bus
[  150.962855] snd_emu10k1: Unknown symbol snd_ac97_suspend
[  151.431880] lp0: using parport0 (interrupt-driven).
[  151.681856] Adding 2498068k swap on /dev/sda5.  Priority:-1 extents:1 across:2498068k
[  152.283692] EXT3 FS on sda1, internal journal
[  153.452102] type=1505 audit(1239294190.201:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3887
[  153.775060] type=1505 audit(1239294190.521:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3892
[  153.775616] type=1505 audit(1239294190.521:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3892
[  153.977326] ip_tables: (C) 2000-2006 Netfilter Core Team
[  154.944122] ACPI: WMI: Mapper loaded
[  156.406751] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  156.483393] apm: BIOS not found.
[  156.744346] ppdev: user-space parallel port driver
[  189.408056] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  189.408147] ata1.01: cmd c8/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 dma 16384 in
[  189.408149]          res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[  189.408280] ata1.01: status: { DRDY }
[  189.408365] ata1: soft resetting link
[  189.596394] ata1.00: configured for UDMA/133
[  189.613794] ata1.01: configured for UDMA/100
[  189.613813] ata1: EH complete
[  189.636049] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  189.671329] sd 0:0:0:0: [sda] Write Protect is off
[  189.671340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  189.671708] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  189.671991] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  189.672220] sd 0:0:1:0: [sdb] Write Protect is off
[  189.672225] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  189.672476] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  189.672721] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  189.672903] sd 0:0:0:0: [sda] Write Protect is off
[  189.672908] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  189.673166] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  189.673405] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  189.673582] sd 0:0:1:0: [sdb] Write Protect is off
[  189.673587] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  189.673835] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  190.139511] Bluetooth: Core ver 2.13
[  190.142996] NET: Registered protocol family 31
[  190.143005] Bluetooth: HCI device and connection manager initialized
[  190.143012] Bluetooth: HCI socket layer initialized
[  190.163419] Bluetooth: L2CAP ver 2.11
[  190.163430] Bluetooth: L2CAP socket layer initialized
[  190.180566] Bluetooth: SCO (Voice Link) ver 0.6
[  190.180576] Bluetooth: SCO socket layer initialized
[  190.271053] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  190.271063] Bluetooth: BNEP filters: protocol multicast
[  190.358785] Bluetooth: RFCOMM socket layer initialized
[  190.359269] Bluetooth: RFCOMM TTY layer initialized
[  190.359276] Bluetooth: RFCOMM ver 1.10
[  190.442660] Bridge firewalling registered
[  196.529046] eth0: Media Link On 100mbps full-duplex 
[  199.500043] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  199.500058] ata1.01: cmd ef/05:fe:00:00:00/00:00:00:00:00/50 tag 0
[  199.500060]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  199.500065] ata1.01: status: { DRDY }
[  199.500103] ata1: soft resetting link
[  199.688411] ata1.00: configured for UDMA/133
[  199.705826] ata1.01: configured for UDMA/100
[  199.705861] ata1: EH complete
[  199.709779] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  199.723022] sd 0:0:0:0: [sda] Write Protect is off
[  199.723032] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  199.723109] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  199.723165] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  199.723187] sd 0:0:1:0: [sdb] Write Protect is off
[  199.723191] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  199.723225] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  199.723261] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[  199.723282] sd 0:0:0:0: [sda] Write Protect is off
[  199.723285] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  199.723320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  199.723352] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[  199.723372] sd 0:0:1:0: [sdb] Write Protect is off
[  199.723376] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  199.723409] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  200.001941] NET: Registered protocol family 17
[  200.268660] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[  200.268704] agpgart-sis 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[  200.268713] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[  200.268768] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[  203.445461] NET: Registered protocol family 10
[  203.448890] lo: Disabled Privacy Extensions
[  207.207904] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[  207.207947] agpgart-sis 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[  207.207957] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[  207.208027] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[ 4339.078182] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 4339.078205] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 4339.123785] snd_ca0106: Unknown symbol snd_ac97_mixer
[ 4339.123965] snd_ca0106: Unknown symbol snd_ac97_bus

```

---

### Post by markbuntu on 2009-04-09
Try this


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

This should get alsa to detect your cards properly again.

---

### Post by Zeedok on 2009-04-09
I thought I would report back now that my problem is solved.

I emailed the chap who built my system and he suggested that the kernel update installed an older version of the alsa-driver than the one I had (and require).  [He has written a set of instructions here]("http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.10") that lead you through the process of installing the latest driver and everything works beautifully.

Hope this helps some people . . .

---

### Post by ekidd91 on 2009-04-10
> **Zeedok said:**
> I thought I would report back now that my problem is solved.

I emailed the chap who built my system and he suggested that the kernel update installed an older version of the alsa-driver than the one I had (and require).  [He has written a set of instructions here]("http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.10") that lead you through the process of installing the latest driver and everything works beautifully.

Hope this helps some people . . .

Cannot thank you enough, sounds working again :D

---

### Post by Zeedok on 2009-04-10
> **ekidd91 said:**
> Cannot thank you enough, sounds working again :D

No problems.

---

