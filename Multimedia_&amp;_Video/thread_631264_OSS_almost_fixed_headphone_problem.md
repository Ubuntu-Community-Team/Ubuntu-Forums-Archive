---
title: "OSS almost fixed headphone problem"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Jadd on 2007-12-04
**This post could be related to an Ubuntu bug filed at**:    [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: sound, headphones, OSS 4, ALSA, SB450 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello, community!

I have a Packard Bell laptop. Ubuntu Gutsy's sound worked great on it, except for the fact that the headphones didn't work. Pluggin in the headphones stopped the speakers though.

So I tried installing OSS 4, following [these instructions](http://ubuntu-unleashed.blogspot.com/2007/10/get-better-sound-in-ubuntu-with-brand.html). System sounds don't seem to work but amarok does great! Plugging in the headphones still doesn't work.

BUT, when I tried running osstest, I got sound through the headphones!
Here's the output:
```
Sound subsystem and version: OSS 4.0 (b1009/200711300206) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007

*** Scanning sound adapter #-1 ***
/dev/oss/hdaudio0/pcm0 (audio engine 0): ATI HD Audio pcm
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47958.00 Hz (-0.09%)> 
/dev/oss/hdaudio0/pcm1 (audio engine 1): ATI HD Audio front
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47007.00 Hz (-2.07%)> 
/dev/oss/hdaudio0/pcm2 (audio engine 2): ATI HD Audio side
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47960.00 Hz (-0.08%)> 
/dev/oss/hdaudio0/pcmin0 (audio engine 3): ATI HD Audio rec
- Skipping input only device

*** All tests completed OK ***
```
The first section (/dev/oss/hdaudio0/pcm0) played sound from the speakers, and nothing else. The second section (/dev/oss/hdaudio/pcm1) played sound only from the headphones. The third section didn't play anything.

So great! Theoritically, the headphones can work under Ubuntu.

What I would like is to get alsa back with the headphones working. Could I use the information I got (/dev/oss/hdaudio0/pcm2) to make alsa work with the headphones? OSS doesn't work perfectly (no sound systems, headphone doesn't work except in osstest, skype doesn't work), so I'd prefer ALSA.

My audio card is SB450.

---

### Post by Jadd on 2007-12-20
bump

---

