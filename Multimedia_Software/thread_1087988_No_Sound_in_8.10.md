---
title: "No Sound in 8.10"
date: 2009-03-05
forum: Multimedia Software
---

### Post by natpagle on 2009-03-05
As the title above suggests, I have no sound in 8.10.  I didn't have it when I used the live CD and again when I finally installed it for good.

I followed every step on the Comprehensive Sound Problem Solution Guide above.

My laptop is an e-machines W4605.  Pretty old yes, but functional in Windows.

I am a new Linux user.  Any help would be appreciated.

Here are the outputs of the various commands:

> ryan@ryan-laptop:~$ sudo modprobe snd
[sudo] password for ryan: 
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with '‘blacklist'
WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with '-e'

> ryan@ryan-laptop:~$ sudo modprobe snd-atiixp
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with '‘blacklist'
WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with '-e'
ryan@ryan-laptop:~$ 

> ryan@ryan-laptop:~$ lspci -v
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 0301
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at d0503400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

> 
ryan@ryan-laptop:~$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with unknown codec at 0xd0503400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xd0503800, irq 17

> ryan@ryan-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.17.

> ryan@ryan-laptop:~$ lsmod | grep snd
snd_atiixp             24204  3 
snd_seq_dummy          10884  0 
snd_atiixp_modem       20360  0 
snd_ac97_codec        111652  2 snd_atiixp,snd_atiixp_modem
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_seq_oss            38528  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_pcm                83204  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  3 snd_atiixp,snd_atiixp_modem,snd_pcm


---

### Post by avrilrox on 2009-03-05
Do you think you could post the output of:

```
aplay -l
```

```
cat .asoundrc
```

---

### Post by tombom3000 on 2009-03-05
Hi,

am having a similar problem (so you hope you don't mind me hijacking this post ;) ), although I'm certain it's not hardware as I've had the sound working in a previous install of 8.10.

Am also new to Linux and have tried the sound guide but to no avail.

aplay -l gives:

**** List of PLAYBACK Hardware Devices ****
card 0: rev40 [VIA 82C686A/B rev40], device 0: VIA 82C686A/B rev40 [VIA 82C686A/B rev40]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And cat .asoundrc gives:

cat: .asoundrc: No such file or directory

Again, any help much appreciated!

Thanks,
Matt

---

### Post by avrilrox on 2009-03-05
> **tombom3000 said:**
> Hi,

am having a similar problem (so you hope you don't mind me hijacking this post ;) ), although I'm certain it's not hardware as I've had the sound working in a previous install of 8.10.

Am also new to Linux and have tried the sound guide but to no avail.

aplay -l gives:

**** List of PLAYBACK Hardware Devices ****
card 0: rev40 [VIA 82C686A/B rev40], device 0: VIA 82C686A/B rev40 [VIA 82C686A/B rev40]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And cat .asoundrc gives:

cat: .asoundrc: No such file or directory

Again, any help much appreciated!

Thanks,
Matt


Run these commands:

> cat /proc/asound/cards
> cat /proc/asound/version 
>  cat  /etc/modprobe.d/alsa-base


---

### Post by tombom3000 on 2009-03-05
Thanks for the quick reply.  As requested...

cat /proc/asound/cards gives:
 0 [rev40          ]: VIA686A - VIA 82C686A/B rev40
                      VIA 82C686A/B rev40 with VIA1612A at 0xe400, irq 10
 1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                      VIA 82XX modem at 0xe800, irq 10

cat /proc/asound/version gives:
Advanced Linux Sound Architecture Driver Version 1.0.17.

cat /etc/modprobe.d/alsa-base 
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

---

### Post by natpagle on 2009-03-05
Before I run the above commands:

> ryan@ryan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And now I'm running the commands:

> 
ryan@ryan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> ryan@ryan-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.17.

> ryan@ryan-laptop:~$ cat /etc/modprobe.d/alsa-base 
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

---

### Post by avrilrox on 2009-03-05
tombom3000:
Might not work BUT try editing this line:

options snd-via82xx-modem index=-2

to

options snd-via82xx-modem index=0

Go into System -> Preferences -> Sound and change everything to alsa.

Also, please post a screenshot (if possible).

Restart your computer.


Also, try this command:

> sudo modprobe snd_via82cxxx_audio
Tell me whether it returns any error.

---

### Post by avrilrox on 2009-03-05
> **natpagle said:**
> Before I run the above commands:



And now I'm running the commands:

Your sound card should work fine. Do you think you could send me a screnshot of the Sound settings? (System -> Preferences -> Sound)

---

### Post by natpagle on 2009-03-05
I have tried flipping through all of the Playback modules, turning up and down, muting and unmuting.  No sound comes out.


[IMG]http://i30.photobucket.com/albums/c348/celant/soundprefs.jpg[/IMG]

---

### Post by avrilrox on 2009-03-05
> **natpagle said:**
> I have tried flipping through all of the Playback modules, turning up and down, muting and unmuting.  No sound comes out.


[IMG]http://i30.photobucket.com/albums/c348/celant/soundprefs.jpg[/IMG]

Change all of them to ALSA.

---

### Post by avrilrox on 2009-03-05
> **avrilrox said:**
> Change all of them to ALSA.

Also, do you think you could scroll down and tell me what is shown in the rest of the list at the bottom?

---

### Post by natpagle on 2009-03-05
They are all set to:
> ALSA - Advanced Linux Sound Architecture

except Default Mixer Tracks, because there isn't that option.  It is set to:
> ATI IXP (Alsa Mixer)

the rest of the mixer's are:
> ATI IXP Modem (Alsa mixer)
Capture: ALSA PCM on front:0 (ATI IXP AC97) via DMA (PulseAudio...
Capture: Monitor Source of ALSA PCM on front:0 (ATI IXP AC97)...
Conexant id 30 (OSS Mixer)
Playback: ALSA PCM on front:0 (ATI IXP AC97) via DMA (PulseAudio...


Under ATI IXP (Alsa mixer), the list continues with:
> Master
Headphone
PCM
Line-in
CD
Microphone
IEC958 Playback AC97-SPSA
PC Speaker
Capture

---

### Post by orethrius on 2009-03-05
I had this same issue some time ago, here's a thread that solved it for me.

[http://ubuntuforums.org/showthread.php?t=826941](http://ubuntuforums.org/showthread.php?t=826941)

---

### Post by avrilrox on 2009-03-05
If the link orethrius posted does not seem to help, try selecting **IEC958 Playback AC97-SPSA**.

---

### Post by Kartagis on 2009-03-17
Hello,

I also have the same problem (from what I read it's the same) and only a reboot fixes it. Here are some outputs:

```

cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc440000 irq 22

```

```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.17.

```

```

cat /etc/modprobe.d/alsa-base
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
options snd-hda-intel model=lenovo

```

I can post any other information you want.

Regards,
/kartagis

---

