---
title: "ALSA .asoundrc config question for 24bit 96khz support"
date: 2008-12-18
forum: Multimedia Software
---

### Post by bullethead on 2008-12-18
I'm really looking for help with ALSA and .asoundrc,

I'm using a netbook that has onboard sound, so using the asoundconf utility I set the default card to the USB soundcard which I am using (Bel Canto USB Link 24/96).

I noticed that when observing the sound stream files at 96khz they were defaulting to 48khz, (I then set that default rate to 44.1khz in "/etc/asound.conf") just to serve up playing baseline 44.1khz files in their pure format (most of my music is 16bit 44.1khz).

However in order to have the stream identify the little bit of sound files which are 96khz I had to create an .asoundrc file in my home directory. Here's the contents (pretty simple):

---start---

pcm.!default {
type hw
card USB
}
ctl.!default {
type hw
card USB
}

pcm.rate_convert {
type plug
slave {
pcm "hw:USB"
rate 96000
}
}

---end---

Is what I am doing correct?  The ALSA stream info identifies the 96khz files as playing back in 96khz after creating the .asoundrc. I am concerned about the pcm.rate.convert section only upsampling a 44.1khz stream, instead of playing it as a pure 96khz stream.  Pulseaudio is disabled.

Any feedback would be appreciated, this is my first dip into hi-res...

---

