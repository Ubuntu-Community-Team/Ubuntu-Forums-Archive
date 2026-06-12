---
title: "flash - no audio :("
date: 2013-08-28
forum: Mythbuntu
---

### Post by slaterson on 2013-08-28
i have a htpc packed with sound cards, i can get all of them to work just as i want with the exception of playing audio from flash content/youtube/any web browser.  i need help, i've googled a ton and tried a lot of stuff with alsa and pulse, all to no avail.

here's my setup:
htpc, intel i5 processor
motherboard has onboard hda intel chip, i have it disabled in the bios (do not want audio from this device).
sound card 0 (PAD, device 0 - analog): rme pad/96 - an instance of mpd is playing through this card perfectly via pulseaudio.
sound card 1 (PAD_1, device 0 - analog): rme pad/96 - a second instance of mpd is playing through this card perfectly via pulseaudio.
sound card 2 (hw:NVidia, device 9 - HDMI): nvidia gt 430 - mythtv outputs to audio to this card, which in turn is connect to an external processor which is connected to my tv.  output in mythtv is configured to use hw:CARD=NVidia,DEV=9.

i've pasted my aplay -l and aplay -L output below.

the nvidia card has several devices, device 9 is the only one i get audio from.  playing videos in mythtv works great, i get excellent video and audio quality.  when i open a web browser to play a youtube video, flash stream, basically _any_ sound played from the computer that isn't from mythtv or mpd, there is no audio.

here is my use case: i run mythtv as my media center (not as a PVR) to watch movies (i buy a dvd or blu-ray, copy it to my media server, mythtv picks it up).  sometimes, i want to watch some youtube content or a streaming live video, so i close mythfrontend, open a web browser and watch.  pretty simple.  i need the browser audio to go to the same device that mythfrontend is using (no, mythfrontend won't be running at the same time).

is this possible?  i've tried making NVidia,Device 9 the default audio device and still get no sound.  i also tried making pulse the default device, still no sound.

i just installed mythbuntu 12.04.3 last night, its a fresh install.  appreciate any help!

my aplay -l output:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PAD [RME Digi96/8 PAD], device 0: Digi96 IEC958 [Digi96 IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PAD [RME Digi96/8 PAD], device 1: Digi96 ADAT [Digi96 ADAT]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PAD_1 [RME Digi96/8 PAD], device 0: Digi96 IEC958 [Digi96 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PAD_1 [RME Digi96/8 PAD], device 1: Digi96 ADAT [Digi96 ADAT]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L:
```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
sysdefault:CARD=PAD
    RME Digi96/8 PAD, Digi96 IEC958
    Default Audio Device
dmix:CARD=PAD,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct sample mixing device
dmix:CARD=PAD,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct sample mixing device
dsnoop:CARD=PAD,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct sample snooping device
dsnoop:CARD=PAD,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct sample snooping device
hw:CARD=PAD,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct hardware device without any conversions
hw:CARD=PAD,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct hardware device without any conversions
plughw:CARD=PAD,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Hardware device with all software conversions
plughw:CARD=PAD,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Hardware device with all software conversions
sysdefault:CARD=PAD_1
    RME Digi96/8 PAD, Digi96 IEC958
    Default Audio Device
dmix:CARD=PAD_1,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct sample mixing device
dmix:CARD=PAD_1,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct sample mixing device
dsnoop:CARD=PAD_1,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct sample snooping device
dsnoop:CARD=PAD_1,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct sample snooping device
hw:CARD=PAD_1,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Direct hardware device without any conversions
hw:CARD=PAD_1,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Direct hardware device without any conversions
plughw:CARD=PAD_1,DEV=0
    RME Digi96/8 PAD, Digi96 IEC958
    Hardware device with all software conversions
plughw:CARD=PAD_1,DEV=1
    RME Digi96/8 PAD, Digi96 ADAT
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```

---

### Post by larsolav on 2013-08-29
Have you tried setting up an asound.conf file? If not, check out [http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto) and scroll to about the middle of the page under the headline "Set up ALSA for these settings". Maybe one of the sample asound.conf files will work. I think for my HDMI setup I had to use a slightly different file. I'll check mine tonight if the ones listed there don't work for you. Cheers!

---

### Post by slaterson on 2013-08-29
i finally got it working last night (several days of trying this and that)...

here is the final setup:
1) create asound.conf in /etc to create an alsa pulse audio pcm and ctl device, then set those as default.
```
more /etc/asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```
2) update /etc/pulse/default.pa with the following:
```
load-module module-alsa-sink device=hw:CARD=NVidia,DEV=9
set-default-sink output 0

```
the values above, of course, are for my system and will vary depending hardware setup.

i am not sure if the /etc/asound.conf file is needed.  i think mythbuntu creates an alsa pulse device on it's own, if that is the case then that conf file should be able to be removed.  i'm not about to touch it right now, its working!

now to figure out why
1) my screen goes blank and won't return if the system sits for extended periods (few hours)..
2) why do folder for backed-up blu-ray discs appear in the media library - it should be showing only the movie title (i get the movie title _and_ the folder, so two entries for one movie).

---

