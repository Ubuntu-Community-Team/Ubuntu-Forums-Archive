---
title: "Gutsy/Audigy sound problem"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by darkmage77 on 2007-09-30
I'm at my wits' end here. So this is the comprehensive disclosure in the hopes that SOMEONE might have a clue what's going on.

I'm running Gutsy (beta) off of a clean install, fully updated as of last night. I had WinXP previously on my comp (it's gone now) and no hardware changes have been made as of the conversion.

My system is custom. Here are the specs:

CPU:          AMD AthlonXP 3000+
MOBO:       Abit NF7-S2G, nForce2 Ultra400 chipset
SOUND:     Creative SB Audigy PCI (the very first one)

I have no sound output--no system, no video, no anything. There are no error messages when I try to test Sounds from the applet, and my card appears properly within the applet for ALSA (Audigy 1 [SB0090] ). For OSS it gives me (TriTech TR28602) as the mixer.

All volume channels (Master, PCM, Line-In) are unmuted and turned up. In **alsamixer** all channels have been unmuted, and the ones which were have been turned up.

I have replaced the linux-sound-base, alsa-base, and alsa-utils. No change. I have installed alsa-oss, also with no change. When I ran **asoundconf list**, the only card to show up was my audigy, which I then set with **asoundconf set-default-card Audigy**. It accepted with no problems. I've also run **modprobe snd-emu10k1**, which is my card's driver in Ubuntu. It ran and returned, which leads me to believe the driver wasn't loaded. But I still have no sound.

Now to the documentation.

**/etc/modprobe.d/alsa-base**
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
options snd-cx88_alsa index=-2
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

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**lspci -v** (where it pertains to the soundcard)
```
02:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at b000 [size=32]
        Capabilities: <access denied>

02:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at b400 [size=8]
        Capabilities: <access denied>

02:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at e0025000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

and finally, **lsmod|grep snd**
```
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

I've been trying for almost 12 hours now (with some sleeptime snuck in there somewhere) and looked through a lot of forum posts, and while a lot of people are having sound issues with Gutsy - and previous flavors, evidently - I haven't seen my issue anywhere as of yet.

EDIT: I should also add that I had Edgy and Feisty both as a dual-boot when I had WinXP, and the sound was picked up and worked right off the bat.

---

### Post by darkmage77 on 2007-09-30
bump

I reseated the card, on the off-chance that it had been nudged somehow. No change.

---

### Post by darkmage77 on 2007-09-30
bump

I installed VLC and tried to play some mp3 files. VLC acts like it's playing, but I'm hearing no sound. Also, I saw in a post that although the speakers weren't putting out, the headphone jack was. My speakers have a headphone jack, so I plugged in some speakers. No sound.

The only thing I've noticed that points to a non-hardware issue is that the PC speaker will beep at the login screen. I need to reiterate that no hardware has been changed since I swept my dual-boot setup off of my hard drive; sound worked under WinXP, Feisty and Edgy.

---

### Post by sinagreine on 2007-10-01
I have exactly the same problem. I reinstalled a machine I had been running Feisty on, where the sound worked out of the box. Othe Gutsy beta, the sound configuration all looks fine, but all I get is silence.

Relevant lspci -v output
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at 3000 [size=64]
        Capabilities: [dc] Power Management version 2

02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at 3040 [size=8]
        Capabilities: [dc] Power Management version 2

 lsmod | grep -i snd
snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           152864  2 snd_emu10k1_synth
snd_ac97_codec        122200  1 snd_emu10k1
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11920  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                62496  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd

---

### Post by sinagreine on 2007-10-01
OK, I got sound working after some poking around.

I rebuilt the ALSA drivers as described in the post by  joshuachad on this thread
[http://ubuntuforums.org/showthread.php?t=545784&highlight=sound+suse](http://ubuntuforums.org/showthread.php?t=545784&highlight=sound+suse)

I rebooted and the sound worked.

I don't know why this worked because the driver is still emu10k1 on my sound card when I recompile.

---

