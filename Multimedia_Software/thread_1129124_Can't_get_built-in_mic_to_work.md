---
title: "Can't get built-in mic to work"
date: 2009-04-18
forum: Multimedia Software
---

### Post by buffalobillion on 2009-04-18
I am running Intrepid on a Dell Studio 17" laptop, which has a built-in microphone. I am trying to use it in conjunction with the Sound Recorder application in Gnome, and I can't get any sound to record. Otherwise sound works fine: I can play sound files, etc. I've Googled everywhere, and the more I read about sound in Ubuntu, the more confused I get. Is there anyone that knows the answer?

First, some details: 
- When I go to System > Preferences > Sound, everything under **Sound Events**, **Music and Movies**, and **Audio Conferencing** is set to "**PulseAudio Sound Server**". Other options are: "Autodetect", "HDA Intel STAC92xx Analog (ALSA)", "HDA Intel STAC92xx Analog (OSS)", "HDA Intel STAC92xx Analog (OSS)", "ALSA - Advanced Linux Sound Architecture", "OSS - Open Sound System". Does anyone else think those seem redundant? **Default Mixer Tracks** is set to "**HDA Intel (Alsa Mixer)**". Other options are: "Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)", "Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)", "Generic 8086 ID 2802 (OSS Mixer)", and "Playback: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)" Again, several seem redundant. 

- When I click the Volume Control, It opens with two tabs, Playback, and Recording. **Device** has "**HDA Intel (Alsa mixer)**" selected. Other options are: "Generic 8086 ID 2802 (OSS Mixer)", "Playback: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)", "Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)", and "Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)". the **Recording** tab has one slider, "Capture". The microphone icon at the bottom of the slider has the red x indicating mute. I click it to un-mute, but every time I close it, and open it up again, it shows it's muted.

- I have a PulseAudio applet that shows in my toolbar, and selecting Volume Meter (Recording)... from it opens a volume meter, but I can't get any sound to show on the meter. Likewise, when I select Volume Control, and select the Recording tab, the Sound Recorder will show up when I click the record button as gnome-sound-recorder: Record Stream. The Input Devices tab shows "ALSA PCM on front:0 (STAC92XX Analog) via DMA." The "Show" selection has "All Except Monitors". If I select "All Input Devices", a second selection called "Monitor Source of ALSA PCM on front:0 (STAC92XX Analog) via DMA" is added.

- Sound Recorder has Master selected on Record from input. No other option is available.

Phew! That's as much as I can think of. I am confused about the various volume controls, seemingly duplicate sound source entries, etc. Any help would be greatly appreciated.

---

### Post by xc3RnbFO8P on 2009-04-18
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=1007990]("http://ubuntuforums.org/showthread.php?t=1007990")

---

### Post by buffalobillion on 2009-04-18
Tried it, and still no worky...

---

### Post by xc3RnbFO8P on 2009-04-18
Could be a bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998")

---

