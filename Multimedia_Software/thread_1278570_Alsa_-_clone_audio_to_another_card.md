---
title: "Alsa - clone audio to another card?"
date: 2009-09-29
forum: Multimedia Software
---

### Post by Swift_gti on 2009-09-29
Hi All,
 
I'm currently trying to setup Alsa so that it clones all the audio sent to my default soundcard (just bog standard onboard connected via headphone jack) and duplicates the output to a USB soundcard.
 
I've been led to beleive this is possible via some configuration of /etc/asound.conf or .asoundrc
 
Currently I've got this, but i'm only getting audio output from the default onboard card..
```

pcm.!default {
        type plug
        slave.pcm "dup"
}
pcm.dup {
        type copy
        slave.pcm "hw:0,0"
        slave.pcm "hw:1,0"
}
```
 
Here is the output of aplay -l (the first device is my default, the last is the one I want to clone to)
 
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
 
Can anyone spot where I've gone wrong ?
I checked out the documentation for the asoundrc config but it's not making too much sense.
 
Many Thanks!

---

### Post by markbuntu on 2009-09-29
You could use pulseaudio, it will correct for the clock drift of the sound devices which alsa cannot do. There is a box you can check in pulse audio preferences for simultaneous output.

---

### Post by Swift_gti on 2009-09-30
Thanks Mark,
 
Is it easy to setup pulse audio to duplicate audio via the CLI ?
I currently have no 'desktop' installed as this PC solely runs XBMC.
 
I'm not sure of what you mean by 'clock drift' presumably it's as it sounds and the cards would slowly get out of sync, so one would end up playing audio slightly later than the other ?
If so thats not a huge issue for me, since the cards feed speakers in two seperate rooms, so any one person won't be listening to both cards at the same time..

---

### Post by markbuntu on 2009-09-30
I had a really difficult time trying to get two sound cards working with just alsa and eventually gave up and used pulse.

I don't know about using pulseaudio strictly from the cli but I suppose it can be done using the pacmd and pactl commands. I seem to remember some people having some issues with getting pulse and XBMC set up properly so if you do try it be aware of that.

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

