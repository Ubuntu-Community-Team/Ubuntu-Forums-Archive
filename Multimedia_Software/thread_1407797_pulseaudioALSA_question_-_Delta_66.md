---
title: "pulseaudio/ALSA question - Delta 66"
date: 2010-02-15
forum: Multimedia Software
---

### Post by savory19 on 2010-02-15
Hi all,

I have an M-Audio Delta 66 sound card which looks like it's been picked up and recognized by my new install of Ubuntu Studio 9.10 - card and drivers are ok according to the guide in the stickied thread here.

I can pick the device from pulse and according to pulse it's getting the audio stream from Audacious using the pulse output plugin, but I see no signal in alsamixer or envy24control (and obviously nothing out of my speakers).  

I have disabled both the HDMI audio from my video card and the USB audio input from a webcam.  

Any suggestions on what could be wrong here?  Thanks!

---

### Post by savory19 on 2010-02-15
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30)

this + switching to analog in the sound preferences got me stereo output at least, we'll see how the rest goes

---

