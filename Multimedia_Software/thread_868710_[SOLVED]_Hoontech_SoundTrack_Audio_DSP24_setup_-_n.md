---
title: "[SOLVED] Hoontech SoundTrack Audio DSP24 setup - no audio output"
date: 2008-07-24
forum: Multimedia Software
---

### Post by kah-el on 2008-07-24
Just installed the latest version of Ubuntu Studio (based on Hardy Heron) and can't get any sound out of the system.

I have checked that the system has found and identified my sound card (Hoontech ST Audio 24 Value). In fact aplay reports several devices:

```
> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 1: ICE1712 consumer [ICE1712 consumer]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 2: ICE1712 consumer (DS) [ICE1712 consumer (DS)]
  Subdevices: 6/6
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
```

I have tried to play an mp3 file with the default program (Movie Player) and that gives me an error: Failed to connect stream: Invalid argument. Did not mess around with the settings yet.

I also tried playing the file with Audacious. Initially the player just loaded the file but did not start the playback, even when I hit play. From Preferences I changed the Current output plugin from PulseAudio output plugin to ALSA Output Plugin. After that Audacious starts the playback and seems to be playing the song, but I get no sound from my system. Tried both the analogue and the digital output.

I started alsamixer from the terminal and got a bit confused. There are 49 columns in playback section alone, including Mic, Video, and Phone, for which I haven't yet found any connectors on my card... I would greatly appreciate it if someone would help me go trough the settings (I knew how to set up the card on Windows side).

I also checked the audio group thing. The file /etc/group has the line

```

audio:x:29:pulse,mikael

```

(don't know what the pulse is, probably the plugin that Audacious was initially configured to use, mikael is my user name). Edited the line to ```
audio:x:29:mikael
``` but that did not seem to help. What should I restart after editing the file, by the way?

I also tried to use some of the software synthesizers with the ALSA output, but did not try to learn the JACK system just yet.

Which would be the best programs and procedures to test the audio output?

Any other ideas?


Kind regards,

Mikael

---

### Post by kah-el on 2008-07-25
Found some help in [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt). Added the following lines to /etc/modprobe.d/alsa-base

```
install snd-ice1712 /sbin/modprobe --ignore-install snd-ice1712 && { /sbin/modprobe -Qb snd-ice1712 ; }
options snd-ice1712 model=dsp24_value
```

Just copied the --ignore-install stuff from other lines, without really understanding what all of that means.

Anyway, now everything seems to work, Audacious plays mp3's, youtube videos have sound (even simultaneously with the Audacious playing the mp3), also software synths seem to work.

---

