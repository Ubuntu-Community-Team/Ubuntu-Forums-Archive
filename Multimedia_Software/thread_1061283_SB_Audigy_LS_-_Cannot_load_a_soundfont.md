---
title: "SB Audigy LS - Cannot load a soundfont"
date: 2009-02-05
forum: Multimedia Software
---

### Post by ticket on 2009-02-05
****SOLVED**sfxload always errors with "No AWE synth device is found"**

[COLOR="Blue"]Duh! As was suspected, it is a driver issue. The Alsa driver for this particular card (the Sound Blaster Audigy SE / CA0106) does not support soundfonts (nor much else, it seems).  While the CA0106 driver can make it produce sounds, that is about the limit of its functionality for the current driver release. This page gives a complete list of Alsa driver capabilities for different Creative soundcards:
 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

So I went and bought a Soundblaster live card, replacing the audigy one. After powering on, I used  "System->Preferences->Default Sound Card" to select the new hardware and everything now works. After loading a soundfont even the file selector plays midi when hovering over a midi file!.
Moral : check first that your soundcard is fully supported by Alsa!  I guess my main concern now is the scant support for sound fonts in the Alsa drivers - it appears that the awesfx package only supports those creative soundcards using the emu10k1 chipset.  Is that really the case?
[/COLOR]



Ubuntu Destop 8.10 with RT kernel

I am being driven nuts by this.
I want to use the hardware synthesiser in my PCI Creative Audigy soundcard.
This sound card most definitely supports soundfonts.

I have have sound working with this card after switching off the Ac97 onboard sound in the BIOS.
Music and videos play fine.
But the soundfont downloader utility refuses me everytime, e.g.

sfxload -i
No AWE synth device is found

asfxload -i
No Emux synth hwdep device is found

How can I get this to work?

I have applied the advice in [https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)
but to no avail.

I have playd with fluidsynth & timidity before, but software sound synthesis was too much of a drain on my Ubuntu system.
My old Windows computer was a PII 400MHz with onboard Yamaha synth and worked really well.
This Unbuntu system is running the RT kernel on a 1.5GHz P4 and is, so far, quite dismal.
Not a good advert for Ubuntu!

Browse loads of forums (even non-English ones) to find a solution. This just confirmed I am not alone with this problem.

A russian site suggested removing pulse audio - is that a good idea?  
I also saw a suggestion to try adding this to a start-up script
  sudo /usr/bin/aweset -v init
Should I do this? Which file should I edit? 

Help!!  Help!!

**System configuration:**
================================
**aplaymidi -l**

 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    CA0106                           CA0106 MPU-401 (UART)
=================================
**lspci -v**

02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at ece0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

=============================================
**cat /etc/modules**

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
# added 
snd-seq
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd_emux_synth
snd_emu10k1_synth
snd-emu10k1
snd-sbawe
snd-emu8000-synth
=========================================================
**cat /dev/sndstat**

Sound Driver:3.8.1a-980706 (ALSA v1.0.17 emulation code)
Kernel: Linux gkh-desktop 2.6.27-3-rt #1 PREEMPT RT Mon Oct 27 03:05:19 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Audigy SE [SB0570] at 0xece0 irq 11

Audio devices:
0: CA0106 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CA0106 MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: mixer00
===============================
**cat /etc/modprobe.d/alsa-base**

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

============================
**lsmod**

Module                  Size  Used by
ipv6                  256916  8 
binfmt_misc             8584  1 
af_packet              17280  2 
bridge                 48020  0 
stp                     2436  1 bridge
bnep                   12288  2 
sco                     9988  2 
rfcomm                 36112  0 
l2cap                  22016  6 bnep,rfcomm
bluetooth              53892  6 bnep,sco,rfcomm,l2cap
ppdev                   7428  0 
speedstep_lib           4484  0 
cpufreq_powersave       1792  0 
cpufreq_userspace       3224  0 
cpufreq_conservative     6176  0 
cpufreq_ondemand        6692  0 
cpufreq_stats           4380  0 
freq_table              4484  2 cpufreq_ondemand,cpufreq_stats
video                  16656  0 
output                  2944  1 video
container               3328  0 
sbs                    11272  0 
sbshc                   5248  1 sbs
pci_slot                4488  0 
wmi                     6440  0 
battery                10244  0 
iptable_filter          2816  0 
ip_tables              11152  1 iptable_filter
x_tables               14852  1 ip_tables
ac                      4100  0 
snd_emu8000_synth      13060  0 
snd_sbawe              30464  1 snd_emu8000_synth
snd_opl3_lib           10496  1 snd_sbawe
snd_sb16_dsp            9856  1 snd_sbawe
snd_sb16_csp           10752  1 snd_sbawe
snd_sb_common          16000  3 snd_sbawe,snd_sb16_dsp,snd_sb16_csp
snd_mpu401_uart         7168  1 snd_sbawe
snd_emu10k1_synth       6144  0 
snd_emu10k1           136352  1 snd_emu10k1_synth
snd_emux_synth         32768  2 snd_emu8000_synth,snd_emu10k1_synth
snd_seq_virmidi         5632  1 snd_emux_synth
snd_seq_midi_emul       6400  1 snd_emux_synth
snd_hwdep               7172  4 snd_opl3_lib,snd_sb16_csp,snd_emu10k1,snd_emux_synth
snd_util_mem            4224  3 snd_emu8000_synth,snd_emu10k1,snd_emux_synth
lp                      9444  0 
dcdbas                  6560  0 
snd_ca0106             32032  2 
snd_ac97_codec        102180  2 snd_emu10k1,snd_ca0106
snd_pcm_oss            38272  0 
snd_mixer_oss          14592  1 snd_pcm_oss
snd_pcm                73476  7 snd_emu8000_synth,snd_sbawe,snd_sb16_dsp,snd_emu10k1,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2692  0 
snd_seq_oss            29184  0 
snd_seq_midi            6272  0 
snd_rawmidi            21248  5 snd_mpu401_uart,snd_emu10k1,snd_seq_virmidi,snd_ca0106,snd_seq_midi
evdev                   9632  6 
snd_seq_midi_event      7168  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47408  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21148  4 snd_opl3_lib,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6924  11 snd_emu8000_synth,snd_sbawe,snd_opl3_lib,snd_emu10k1_synth,snd_emu10k1,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54692  25 snd_emu8000_synth,snd_sbawe,snd_opl3_lib,snd_sb16_dsp,snd_sb16_csp,snd_sb_common,snd_mpu401_uart,snd_emu10k1,snd_emux_synth,snd_seq_virmidi,snd_hwdep,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             31044  1 
serio_raw               5380  0 
parport                34336  3 ppdev,lp,parport_pc
soundcore               7264  1 snd
ac97_bus                1792  1 snd_ac97_codec
psmouse                36496  0 
snd_page_alloc          8072  3 snd_emu10k1,snd_ca0106,snd_pcm
nvidia               6891888  26 
i2c_core               23464  1 nvidia
button                  6032  0 
pcspkr                  2560  0 
intel_rng               4608  0 
intel_agp              25404  1 
shpchp                 29460  0 
agpgart                33484  2 nvidia,intel_agp
pci_hotplug            27320  1 shpchp
iTCO_wdt               10444  0 
iTCO_vendor_support     3588  1 iTCO_wdt
ext3                  123528  1 
jbd                    44948  1 ext3
mbcache                 7704  1 ext3
sr_mod                 14020  0 
cdrom                  34848  1 sr_mod
sd_mod                 34092  3 
crc_t10dif              1920  1 sd_mod
sg                     31200  0 
ata_piix               16516  2 
pata_acpi               4096  0 
ata_generic             4740  0 
libata                167776  3 ata_piix,pata_acpi,ata_generic
uhci_hcd               22160  0 
3c59x                  40360  0 
mii                     5248  1 3c59x
scsi_mod              145676  4 sr_mod,sd_mod,sg,libata
usbcore               139408  2 uhci_hcd
dock                    8484  1 libata
thermal                15516  0 
processor              29104  1 thermal
fan                     4356  0 
fbcon                  39456  0 
tileblit                2688  1 fbcon
font                    8320  1 fbcon
bitblit                 5760  1 fbcon
softcursor              1920  1 bitblit
uvesafb                26596  0 
fuse                   51612  3

---

### Post by ticket on 2009-02-06
Is there a clue in the message:

     [B]Synth devices: NOT ENABLED IN CONFIG
[/B]

How does one enable it?

---

### Post by ticket on 2009-02-06
Same problem exists when using kernel 2.6.27-11-generic

---

### Post by ticket on 2009-02-07
Seems this might be a bug or config issue in the sound modules / drivers.
The sound card was bought very recently - but is nothing special:

Creative Sound Blaster  Audigy SE 7.1 OEM PCI Soundcard
Signal Processor	Creative Audigy SE
Interface Type	        PCI
Features	        EAX ADVANCED HD, 
                        **SoundFont Bank technology,** 
                        Creative Multi Speaker Surround (CMSS) - 3D

Should work out of the box - and it does, except for loading soundfonts.

Still talking to myself on this forum, it seems ...

---

### Post by ticket on 2009-02-14
Bumping to show solution (see edited first post)
.:P

---

