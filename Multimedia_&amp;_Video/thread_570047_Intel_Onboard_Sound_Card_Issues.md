---
title: "Intel Onboard Sound Card Issues"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by PeterDB on 2007-10-07
Sorry, but I'm a still very noobish at troubleshooting Linux/Ubuntu issues, so I need some help people...

I have a Compaq Evo D500 series desktop PC running a P4 1.7 Ghz with 768 MB on 20 GB HDD running 7.04, its main purpose is to be a server for SlimServer (for my 3 SqueezeBox's), but also as a minimal usage PC.

But, I have a problem getting the onboard Intel soundcard to work correctly.
[LIST]
[*]No matter if I mute the PC speaker in the Preferences > Sound, I still get sound out of it. Only if I mute PCM, does it stop, but then I get nothing elsewhere also.
[*]The speaker jack on the back doesn't work (haven't tested the microphone, since I don't need it)
[*]The head phone jack on the front works, but has a lot of static. Does mute though when I mute Microphone in the Preferences > Sound.
[*]Master volume control in Preferences > Sound, both the level and mute, doesn't do anything.
[/LIST]

I tried to follow the suggestion from [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)  to add the line "options snd-hda-intel model=3stack" to the file "/etc/modprobe.d/alsa-base" and restarted, but it didn't make a difference.

I tried reading [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) to see what other modules I could pick, but I have no bloody clue which one to even being with.

Can you help?


I included some information, which might be useful:
> **cat /etc/modprobe.d/alsa-base**

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack


> **lsmod**

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
button                  8720  0 
dock                   10268  0 
video                  16388  0 
container               5248  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  3 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
parport_pc             36388  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                36936  3 ppdev,lp,parport_pc
xpad                    9988  0 
pcspkr                  4224  0 
psmouse                38920  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
i2c_core               22656  1 i2c_ec
intel_agp              26140  1 
agpgart                35400  1 intel_agp
serio_raw               7940  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
floppy                 59524  0 
uhci_hcd               25360  0 
usbcore               134280  4 xpad,usbhid,uhci_hcd
e100                   36232  0 
mii                     6528  1 e100
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
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


>  **cat /proc/asound/cards**

 0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1885 at 0x2000, irq 19


>  **aplay --list-devices**

**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


>  lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: fd000000-fe1fffff
        Prefetchable memory behind bridge: f5e00000-f7ffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: fc200000-fc4fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12) (prog-if 80 [Master])
        Subsystem: Compaq Computer Corporation Unknown device 2411
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 2480 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 2411
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 2440 [size=32]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 2411
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2460 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
        Subsystem: Compaq Computer Corporation Evo D500
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2000 [size=256]
        I/O ports at 2400 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0072
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f6000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at f5e00000 [disabled] [size=64K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
        Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM
        Flags: bus master, medium devsel, latency 66, IRQ 16
        Memory at fc400000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1000 [size=64]
        Capabilities: <access denied>


---

### Post by PeterDB on 2007-10-08
Unfortunately, no one was able to provide me with a direct answer. So I posed this very same question on a Danish IT help board called Eksperten.dk.

In less than an hour, I had already gotten the first leads where to go look.

As it turns out the default Mixer in Ubuntu, does not seem to allow to control as much as AlsaMixer does in a Terminal window. The AlsaMixer has the Master muted, yet the Ubuntu default mixer's master was not. AlsaMixer also offered an option to control the channel Master Mono, after I muted it the music from the internal PC speaker was gone and the static in the front headphone jack had greatly dimished.

Thread from the forum is here: [http://www.eksperten.dk/spm/800098](http://www.eksperten.dk/spm/800098) . Thanks to psycosoft-funware for provided the last peice of information.

---

