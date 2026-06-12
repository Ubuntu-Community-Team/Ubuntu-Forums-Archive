---
title: "Youtube audio not working in Chromium-Browser or Firefox (HDMI)"
date: 2014-09-19
forum: Multimedia Software
---

### Post by jerry4 on 2014-09-19
I am running Mythbuntu (14.04) with Lubuntu desktop.
The problem I have is that I have no audio from Chromium or Firefox.
MythTV and VLC Media player work fine with audio.

It acts as if the volume control in youtube is trying to control the on-board analog audio which I am not using.
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


The HDMI is card 1 and device 3

I have also inserted "options snd-ati-hdmi model=auto" into /etc/modprobe.d/alsa-base.conf

```
cat /proc/asound/card1/codec* | grep Codec
Codec: ATI RS690/780 HDMI

```

A second issue is that the system tray audio control is also using analog.
I can load a media file and open the Pulse Audio Control and change the volume.

Another symptom is that when I run a speaker-test with no options which should pick up the default audio device, I have no errors but also no audio.
When I run the speaker-test with an option "speaker-test -Dplughw:1,3" I have no errors and the audio works.

---

### Post by jerry4 on 2014-09-21
Resolved:

I finally found the resolution to no sound from Chromium-Browser or Firefox.
The problem was in the /etc/asound.conf file.
Since the aplay -l clearly shows **[COLOR=#ff0000]card 1[/COLOR] [COLOR=#ff0000]device 3[/COLOR]** the following code which I have used to several previous versions of Ubuntu in the past does not work

This code for asound.conf file does not work:
Replace leadpad with the editor or your choice
```
sudo leadpad /etc/asound.conf
pcm.!default {
type hw
[COLOR=#ff0000]card 1
device 3[/COLOR]
}

```

This code similar for asound.conf file does not work:
Replace leadpad with the editor or your choice
```
sudo leadpad /etc/asound.conf
pcm.!default {
      type plug slave.pcm {
            type hw [COLOR=#ff0000]card 1 device 3[/COLOR]
      }
}

```

What does work and resolved my problem is using the card name in the asound.conf.
To get the unique card names run the following code:
```
aplay -l | awk -F \: '/,/{print $2}' | awk '{print $1}' | uniq
SB
[COLOR=#ff0000]HDMI[/COLOR]

```The card I want to use is HDMI, therefore replace the asound.conf as follows:

```
sudo leafpad /etc/asound.conf


pcm.!default {
    type hw
    card [COLOR=#ff0000]HDMI[/COLOR]
}


ctl.!default {
    type hw
    card [COLOR=#ff0000]HDMI[/COLOR]

```

As a note I also loaded "PulseAudio Volume Control" which I used to set up firefox.

---

