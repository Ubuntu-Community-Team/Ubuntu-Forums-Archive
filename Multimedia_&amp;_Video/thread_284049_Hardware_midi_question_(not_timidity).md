---
title: "Hardware midi question (not timidity)"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by firenewt on 2006-10-25
Hi, well,

I got hardware midi to play by loading the modules and loading soundfonts through asfxload and all that. The sound card is 'SB Live 5.1 (SB0220)'.

My question is, are we supposed to hear stereo through this? Because I think I can hear both midi channels, but only on the right speaker while the left is mute. Is this how it's supposed to be. If not, any idea what I've done wrong?

---

### Post by sp4rd on 2006-10-25
I have a SB Live! Value [CT4831], Do you use pmidi or playmidi?
You can try
```
export ALSA_OUTPUT_PORTS=17:0,17:1,17:2,17:3
```
Those are the midi ports on the Value, I don't know if they are the same on your card. What does
```
cat /proc/asound/Live/wavetableD1
```
tell you.

---

