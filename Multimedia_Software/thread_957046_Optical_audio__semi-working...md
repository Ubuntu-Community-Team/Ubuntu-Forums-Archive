---
title: "Optical audio : semi-working.."
date: 2008-10-23
forum: Multimedia Software
---

### Post by k3kiaze on 2008-10-23
I followed these guides to get optical audio working:

[URL="http://ubuntuforums.org/showthread.php?t=843012"]
_http://ubuntuforums.org/showthread.php?t=843012_[/URL]
and
[_http://ubuntuforums.org/showthread.php?t=776958_]("http://ubuntuforums.org/showthread.php?t=776958")

I have audio from all applications tested so far, except Miro and Ubuntu startup sound. I've discovered through my journey that Pulse audio is different to ALSA. It seems ALSA (which is what I setup using the 1st link on top) is working 100% and i'm not sure of pulse. Also [_this_]("http://alsa.opensrc.org/index.php/DigitalOut") article shows I have to set "PCM Out" to truly benefit from optical out. So I have 2 questions:

1. Can someone please help me get Miro and ubuntu startup sound working?

2. How do I set"PCM Out" That article comically states "*TODO: Tell people how to set "PCM out" mode.*"

Thanks in advance.

---

### Post by fjf on 2008-10-24
Yes, we lost optical since pulseaudio :confused:  I have an intel HDA with an ALC888 digital out and there is no way to get it working now.  It worked fine before, with the old ALSA.  Sometimes we make changes for the worst :mad:

---

### Post by k3kiaze on 2008-10-24
Thanks for the reply, so youre saying that although I get audio through a single optical cable it's not truly optical aka PCM?

Also I cannot control the volume i.e master volume, only mute unmute, is this an optical connection issue? because this happens in both windows and ubuntu.

---

### Post by vaderj on 2008-12-21
I have been running coax spdif for a long time now and i have never been able to control the volume through the mixer either, but since i have always just had it going to a receiver it wasnt really a problem, i am assuming that this is because it is a digital signal, therefore you are not actually increasing the voltage of waveform like you would be with an analog output. with a digital signal, to increase the volume, you would have to, via the driver/decoder, apply some sort of multiplier to the actual audio signal.  think of it similar to a turntable vs a cd player; if you press down on a turntable while a record is playing, it slows the playback ..... try this with a cd, and the cd player will most likely give you a read error

---

### Post by ifmusic on 2009-12-27
> **k3kiaze said:**
> Thanks for the reply, so youre saying that although I get audio through a single optical cable it's not truly optical aka PCM?

Also I cannot control the volume i.e master volume, only mute unmute, is this an optical connection issue? because this happens in both windows and ubuntu.

I'm exactly at the same point, I get stereo only and Not raw PCM output to the reciever. I know your post is a year old so may be you've found out some solution... or gave up on it...

Thanks

---

