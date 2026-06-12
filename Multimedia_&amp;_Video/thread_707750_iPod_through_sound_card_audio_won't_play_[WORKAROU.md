---
title: "iPod through sound card: audio won't play [WORKAROUND]"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by thoughts on 2008-02-25
Hello,

I'm having trouble getting a portable audio player to play through my sound card's line input jack in Gutsy.  When I hook up my iPod or iPhone (which is already playing music), no sound comes through the PC's speakers.

However, when I open Audacity and hit the record button, it does record the sound from the line input; I see the waveform and can then play it back in Audacity.

And when I go to Main Menu > System > Preferences > Sounds, on the Devices tab I have a section called Audio Conferencing, and in that section there is a Sound Capture setting with a drop-down list and a Test button.  When I hit the Test button, the sound from the iPod suddenly starts coming through the speakers, but after a few seconds, an error message pops up:

```

Failed to construct test pipeline for 'gconfaudiosrc !
audioconvert ! audioresample ! gconfaudiosink profile=chat'
[Close]

```

The sound keeps playing until I hit the Close button on that error message, then the sound stops.

All of the sound settings are set to ALSA or Autodetect, and other than this issue, the sound on my system works fine: from the browser, from Amarok, VLC/gxine/Totem, etc.

I've gone through all the sliders and toggles in Volume Control and alsamixer, setting them all to 100% and all to on/unmuted.  There's one called "Line in as output" which I've disabled.  The "input source" is set to "line."  And as stated above, Audacity picks it up fine.

Audacity's recording device is set to "ALSA: HDA Intel: STAC92xx Analog (hw:0,0)", and my Volume Control is also set to use "HDA Intel (Alsa mixer)" as opposed to the other option which is "SigmaTel STAC9271D (OSS Mixer)".  I've tried with and without the "Enable software sound mixing (ESD)" setting.  Here's my hardware info:

```

# lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

After searching here and launchpad.net, I tried a few things: I installed pulseaudio-esound-compat, but that didn't help.  Then I tried running the following command:

```

gst-launch gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat

```

...and that worked; the sound instantly started coming through my speakers.  I found that I could boil that command down further to the following and it still worked:

```

gst-launch gconfaudiosrc ! gconfaudiosink

```

I only reboot once every month or two, so it's not a big deal for me to hit Alt-F2 and run that command once when I log in to Gnome.  (Or of course I could set it to autorun using various methods.)  So this is a decent workaround for the problem, but the question is, why isn't my line input routed into the playback system by default?

UPDATE: actually, after running for a few hours, the gst-launch process consumes several GIGABYTES of RAM, so either I'm doing something horribly wrong in the way that I'm calling it, or else this is NOT an acceptable workaround to my sound issue.

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

