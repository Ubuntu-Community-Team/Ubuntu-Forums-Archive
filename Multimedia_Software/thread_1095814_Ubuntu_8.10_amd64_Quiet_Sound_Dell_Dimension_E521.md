---
title: "Ubuntu 8.10 amd64 Quiet Sound Dell Dimension E521"
date: 2009-03-14
forum: Multimedia Software
---

### Post by johnnymaelstrom on 2009-03-14
I've just installed Ubuntu 8.10 amd64 on my Dell Dimension E521 and everything is great except the audio. The symptoms are at first no sound and then following some changes I got sound, but it was very quiet.

How can we overcome this or am I going to have to move distribution?

Here are the pieces of information I've seen asked for on this and other forums about similar sound related issues.

First the one change from the default installation was to add 

```
options snd-hda-intel model=STAC9227
```

to /etc/modprobe.d/alsa-base based on the output of 

```
cat /proc/asound/card0/codec#* | grep Codec
```
and seeing the output

```
Codec: SigmaTel STAC9227
```

I can't say if this actually improved things to the point of having very low sound or if it was already low and I just couldn't hear it.

Output of various diagnostics

/etc/modprobe.d/alsa-base

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
options snd-hda-intel model=STAC9227
```

/sbin/lsmod | grep snd

```
snd_bt87x              23844  0 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_hda_intel         492336  1 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                99208  3 snd_bt87x,snd_hda_intel,snd_pcm_oss
snd_timer              34320  2 snd_seq,snd_pcm
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  12 snd_bt87x,snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  3 snd_bt87x,snd_hda_intel,snd_pcm
```

---

### Post by johnnymaelstrom on 2009-03-14
I forgot to add a few other bits of information from the comprehensive audio guide:

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v

```
snip...

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Dell Device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

snip...

04:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. Device 13eb
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fdafe000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Bt87x
	Kernel modules: snd-bt87x
```

sudo modprobe snd-

```
snip...
snd-hda-intel
snd-bt87x
```

It all loads fine as a module

---

