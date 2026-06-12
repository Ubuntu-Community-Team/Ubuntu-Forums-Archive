---
title: "MythTV Audio-In through PCI Nova-S+"
date: 2012-02-03
forum: Multimedia Software
---

### Post by maff on 2012-02-03
This has been driving me nuts for a few days now.

I have the following setup.

Machine with onboard sound + 2 Hauppauge Nova-S+ DVB-S cards.

The DVB-S cards are setup and work fine though mythtv for SD satellite channels both video and sound working fine.

(PC is attached back to TV via HDMI).

However the Nova-S's have a Composite In too, which I want to use to record from my Sky+ Box.

I have wired it up, created a new channel in myth-setup using /dev/video0 and /dev/vbi0 and ALSA:default

The new channel shows video fine but gets no sound.

I know the sound works, because if I run gnome-sound-recorder and record from "Master" then it records the audio from the sky box.

I just cant get it to work in mythtv.

aplay -L gives:
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC889 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC889 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC889 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC889 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC889 Digital
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
```

more</proc/asound/cards 

```
 0 [CX8801_1       ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf8000000
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf4000000
 2 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 3 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19

```

more</proc/asound/devices
```
  1:        : sequencer
  2: [ 1- 0]: digital audio capture
  3: [ 1]   : control
  4: [ 0- 0]: digital audio capture
  5: [ 0]   : control
  6: [ 2- 2]: digital audio capture
  7: [ 2- 1]: digital audio playback
  8: [ 2- 0]: digital audio playback
  9: [ 2- 0]: digital audio capture
 10: [ 2- 0]: hardware dependent
 11: [ 2]   : control
 12: [ 3- 3]: digital audio playback
 13: [ 3- 0]: hardware dependent
 14: [ 3]   : control
 33:        : timer

```

Any help would be appreciated.

Cheers

Maff

---

### Post by maff on 2012-03-16
No body?

---

### Post by BicyclerBoy on 2012-03-16
alsa inputs are listed with
arecord [-l | -L]

alsa:default is defaulted to the pulseaudio server input unless you overwrite the definition with !default in asound.conf.

Use pavucontrol & change the default pulse input to your nova-s input or..
a better way would be to point mythtv directly at the correct alsa device.

arecord -l
see which one works by recording from each alsa device & playing back:
arecord -c 2 -t wav -r 48000 -f S16_LE -V stereo -D hw:0,0 ~/input.wav

It would pay to check the input mixer levels (mine were muted):
alsamixer 
then <F4>

---

### Post by maff on 2012-03-17
> **BicyclerBoy said:**
> 
a better way would be to point mythtv directly at the correct alsa device.



Cheers!

arecord -c 2 -t wav -r 48000 -f S16_LE -V stereo -D hw:2,0 ~/input.wav

Does indeed record sound perfectly, so now I know which card.

So in mythtv setup on the card, i've tried set the audio device to:
hw:2,0
and
ALSA:hw,2,0

neither of which workd, still silence, is that the right format to type the aduio device in?

Edit: Ive now got video and audio perfectly in VLC just the damn audio on mythtv to sort.

---

### Post by BicyclerBoy on 2012-03-17
It could be due to MythTV not being able to detect or set the sample format/bit rate etc..

try this auto rate converting device:
plughw:2,0

If this fails then you may have to make a custom virtual plug (in asound.conf) so that the sample rate/format/channels can be forced but still linked to device hw:2,0.

---

### Post by maff on 2012-03-18
> **BicyclerBoy said:**
> It could be due to MythTV not being able to detect or set the sample format/bit rate etc..

try this auto rate converting device:
plughw:2,0

If this fails then you may have to make a custom virtual plug (in asound.conf) so that the sample rate/format/channels can be forced but still linked to device hw:2,0.

Sorted it.

Needed to click the Force Sample Rate to 48000 in setup, the arecord command from your previous post gave me the clue.

Really appreciate the help. 

Cheers!

---

### Post by maff on 2012-06-15
New problem on the same theme.

The order of the cards keeps changing on reboot, now i have read about defining the order in /etc/modprobe.d/alsa-base but 2 of my cards have the same name, so the order of those two cards keeps swapping.

Is there anyway to specify the order of the pci slots so the cards are always detected in the same order?

```


maff@mythbox:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 cx88_alsa
 2 cx88_alsa
 3 snd_hda_intel

```

devices 1 & 2 are the problem children :)

Cheers all

Maff

---

