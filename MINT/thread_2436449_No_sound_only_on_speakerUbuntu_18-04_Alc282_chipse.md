---
title: "No sound only on speaker/Ubuntu 18-04/ Alc282 chipset"
date: 2020-02-06
forum: MINT
---

### Post by guicar on 2020-02-06
Hello all,
Help is most welcome on my issue as i  need some direction in order to solve.

[B]Summary:
[/B]No sound on speaker despite headset and Hdmi outpout sound is okMy laptop is a Teclast F5
In pavucontrol the speakers and the headphones are listed, and the volume bar showed sound being played. The speaker test did not produce sound at the speakers. The headphones, when plugged in, worked perfectly.
Alsa mixer don't show any mute and speaker volume,master and Pcm are at max.
Sound is ok when using Hdmi on television.
Speaker are working under Windows10.

**Details**
```

cat /proc/version
Linux version 5.3.0-28-generic (buildd@lcy01-amd64-009) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020
Over Linux Mint
lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 19.3 Tricia
Release:    19.3
Codename:    tricia

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k5.3.0-28-generic

lspci | egrep -i audio 
00:0e.0 Audio device: Intel Corporation Device 3198 (rev 03)

cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa1210000 irq 128

cat /proc/asound/pcm
00-00: ALC282 Analog : ALC282 Analog : playback 1 : capture 1
00-03: HDMI 0 : HDMI 0 : playback 1
00-07: HDMI 1 : HDMI 1 : playback 1
00-08: HDMI 2 : HDMI 2 : playback 1
00-09: HDMI 3 : HDMI 3 : playback 1
00-10: HDMI 4 : HDMI 4 : playback 1

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC282 Analog [ALC282 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card0/id
PCH

ls /proc/asound/card0/
codec#0  eld#2.0  eld#2.2  eld#2.4  eld#2.6  eld#2.8  pcm0c  pcm10p  pcm7p  pcm9p
codec#2  eld#2.1  eld#2.3  eld#2.5  eld#2.7  id       pcm0p  pcm3p   pcm8p

cat /proc/asound/card0/pcm0c/info 
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC282 Analog
name: ALC282 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0

cat /etc/modprobe.d/alsa-base.conf
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2




aplay -vv linuxmint-login.wav 
Playing WAVE 'linuxmint-login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 22050
  period_size  : 5512
  period_time  : 125000
  tstamp_mode  : NONE
  tstamp_type  : GETTIMEOFDAY
  period_step  : 1
  avail_min    : 5512
  period_event : 0
  start_threshold  : 22050
  stop_threshold   : 22050
  silence_threshold: 0
  silence_size : 0
  boundary     : 6206523236469964800
#+                                                 | 01

```
Nothing on speaker but ok on headphone

Hope somebody have some knowledge around this topic .... thank you for your time.

  Kind regards,

---

### Post by coffeecat on 2020-02-11
*Thread moved to **Mint** sub-forum.*

---

