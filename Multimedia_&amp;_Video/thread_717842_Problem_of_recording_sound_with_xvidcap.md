---
title: "Problem of recording sound with xvidcap"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by worc on 2008-03-07
Hi all,
I'm on Gutsy.
To record sound using gnome-sound-recorder, everything is fine. The recorded sound is smooth.
If I try to capture my desktop with xvidcap, the video is OK but the sound is very noisy. I can hear the sound I want to record as expected, but I can also hear high frequency noises, which is much louder than the sound I try to record.
I tried OSS 4.0, sound recording with xvidcap is OK and there is no noise any more.

I want to stick with ALSA. Any idea to help me get through? 

Right now, gnome-sound-recorder works fine but xvidcap doesn't.

---

### Post by worc on 2008-03-08
Bump.

Xvidcap has an option to define the device used to capture sound, which is default to /dev/dsp. I wonder if gnome-sound-recorder uses the same device to capture sound? If it doesn't, is it possible to fix the problem by changing the capture device in xvidcap to the one gnome-sound-recorder uses?  I'm just guessing.
Anyway, if anyone can teach me  how to figure out which device gnome-sound-recorder uses to capture sound, I'd like to give it a try.

---

### Post by worc on 2008-03-09
bumpppppppppp

---

### Post by Roti on 2008-03-10
Hi!

 I tried gtk-recordMyDesktop, but the sound and the video was not in sync.
So I tried xvidcap. I had the same problem, which is the noisy sound.

Finally I had a total solution:
- Installed pulseaudio, and started with "pulseaudio" (not installed PulseAudio sound server  yet) (I read that Hardy Heron will have pulseaudio by deault)
- I started xvidcap with: "padsp xvidcap"

My recording is so cool with sound!


Roti

---

