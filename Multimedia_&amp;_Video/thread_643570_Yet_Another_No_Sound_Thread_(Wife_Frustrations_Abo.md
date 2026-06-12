---
title: "Yet Another No Sound Thread (Wife Frustrations Abound)"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by michaelkoss on 2007-12-17
Yes, another thread (I've read almost all the others) about missing sound in Ubuntu. I am trying to upgrade a MythTV box from Fedora 5 to Mythbuntu and my wife is getting frustrated at the downtime :( Any help to get me out of the dog-house would be /greatly/ appreciated!

Fresh install of mythbuntu 7.10. When I try to play live tv or a recording in MythTV, I get no sound. I also get no sound if I try to play an MP3 through VLC. I have messed with alsamixer and put a pair of headphones into every jack possible, even the MIC ;)

```

sudo cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC202 at irq 20

```

```

$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [e4] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at ffa80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        I/O ports at ec00 [disabled] [size=8]
        Capabilities: [d0] Power Management version 1

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at cc00 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at ffa7f400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: d6b00000-e6afffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at e800 [size=8]
        I/O ports at e400 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d800 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: medium devsel, IRQ 9
        I/O ports at d400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 4043
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at ffa7fc00 (32-bit, non-prefetchable) [size=512]
        Memory at ffa7f800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

01:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. Unknown device b7f1
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

01:01.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Netgear Unknown device 311a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        I/O ports at b800 [size=256]
        Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at d6b00000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2

```

```

$ sudo lsmod|grep snd
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

```

```

$ sudo lshw   //just the multimedia part
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

```

$ sudo cat /etc/modprobe.d/alsa-base 
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
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

That's all I can think to post. If there is anything else, I will provide it. The fate of the Linux world (in my wife's eyes) rests in your hands!

Michael.

---

### Post by peitschie on 2007-12-17
Hi Michael,

I'm quite impressed with the amount of detailed information you've posted!  Well done.

Well, a quick search on the net led to this: [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0") which you may have already seen.

Failing that, there are a whole bunch of posts on the net regarding the 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller. One that looked promising was: [http://lists.debian.org/debian-user/2007/08/msg00152.html]("http://lists.debian.org/debian-user/2007/08/msg00152.html")

 I don't see anything obviously wrong with your set up however.  I don't think it wouldn't hurt to double check all the sliders and mute buttons, check which audio device Ubuntu is attempting to use for output, checking the version of your alsa etc.

---

### Post by michaelkoss on 2007-12-17
Thanks for the links. Unfortunately, I'm tired :) I'll check these out tomorrow after work and post back.

If anyone else is experiencing/has experienced this problem, let me know please. Perhaps we can work together.

Michael.

---

