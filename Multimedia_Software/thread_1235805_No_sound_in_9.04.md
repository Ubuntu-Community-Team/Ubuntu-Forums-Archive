---
title: "No sound in 9.04"
date: 2009-08-09
forum: Multimedia Software
---

### Post by methodtwo on 2009-08-09
Hi there
I've just installed the latest release of ubuntu on my HPvd2000 laptop.
There were no login sounds when i logged in.There is no sound when i try to play CDs.I've tried entering alsamixer and turning up the level for pcm-2
but that didn't work either.
Here is the relevant output from lspci about my sound card:
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
And here's the relevant output from lsmod regarding the sound drivers:
```
snd_hda_intel         435636  5 
arc4                    9856  2 
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
iwl3945                97912  0 

```
So the drivers are there and the alsamixer levels are up.I don't know what to do.Any help would be great.Thank you in advance

---

### Post by methodtwo on 2009-08-09
I solved this issue by right clicking on the speaker icon at the top right hand corner of the screen. Then when the volume control GUI comes up i went to preferences. I then had to add(under set tracks to be visible)PCM-2
As i said i'm using a laptop so if you're using a laptop this may be the fix for you!
regards methodtwo

---

