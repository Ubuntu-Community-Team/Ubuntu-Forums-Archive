---
title: "Crackling Sound on SB Audigy"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by tuedel on 2006-11-11
Hi,
when I play back music with Amarok or XMMS on my Sound Blaster Audigy, I get a crackling sound. (I managed to record the effect with Audacity, see attachments)
Also, I noticed a kind of overmodulation on my system sounds. The only way to avoid these was turning down the volume on some controllers in the mixer and turning up my external amplifier (to an insane level, compared to the level I used in Windows)

I'm using Kubuntu 6.10 (edgy) and ALSA as my sound server. (At least I think so, I'm a desktop-linux and thus linux-audio newbie ;-)

Any suggestions?

---

### Post by lordgibbness on 2006-11-11
Have you tried turning off everything in 'alsamixer' and then turning them on one-by-one as required? Also, the main volume shouldn't be set above 80% if you max all the other controls.

alsamixer controls:
esc - exit
up/down - vol
left/right - device
tab - playback/recording
numbers - set percentage levels

---

### Post by tuedel on 2006-11-12
In Alsamixer everything that I don't need is already turned off (At least I think so.. See attachment)

---

### Post by tuedel on 2006-11-12
Oh, and btw: My main problem are these crackles/glitches/whatever, they get really annoying in the more 'quiet' parts of my music..
But I can live with having to turn up my external amplifier.

---

### Post by OwenA on 2006-11-12
SOrry for my ignorance...but how do you get into the Alsamixer controls?

---

### Post by tuedel on 2006-11-12
Well.. Just type ```
alsamixer
``` into the console ;-)
There is also a gui version, 'alsamixergui'.

---

### Post by xiangpeng on 2006-11-12
I have this problem too, but it crackles when the cpu load it high. didn't have this problem last time though

---

### Post by tuedel on 2006-11-13
I have just found out that the sound in XMMS doesn't crackle (or at least does crackle much less) when I use the jack output plugin instead of the alsa output plugin. This 'workaround' doesn't solve my problem though, since I would like to play my music via amarok's music library.

Oh, and if anyone suspects that jack is using to much resources and thus is causing the crackling on my ALSA output: The sound in amarok also crackles when jackd isn't running.

---

### Post by ubman on 2006-11-13
> **tuedel said:**
> I have just found out that the sound in XMMS doesn't crackle (or at least does crackle much less) when I use the jack output plugin instead of the alsa output plugin. This 'workaround' doesn't solve my problem though, since I would like to play my music via amarok's music library.

Oh, and if anyone suspects that jack is using to much resources and thus is causing the crackling on my ALSA output: The sound in amarok also crackles when jackd isn't running.



I fouund having the tone box ticked (int he switch's tab)
i have the same issue.

---

### Post by OwenA on 2006-11-13
> **tuedel said:**
> Well.. Just type ```
alsamixer
``` into the console ;-)
There is also a gui version, 'alsamixergui'.


OK...I see it but how do you modify it?

---

### Post by tuedel on 2006-11-13
Left and right arrow to select the controllers, up and down to turn them up or down, F1 for help (F3 to return to the controllers), TAB to select between  'Playback', 'Capture' and 'All'.

---

### Post by OwenA on 2006-11-13
> **tuedel said:**
> Left and right arrow to select the controllers, up and down to turn them up or down, F1 for help (F3 to return to the controllers), TAB to select between  'Playback', 'Capture' and 'All'.

LMAO!!! Thanks! Funny I tried my ALtec speakers and nothing. Tried some cheap speakers and nothing. I hook up my Altec headset for gaming and I hear my CD playing on it???? What gives?

---

### Post by tuedel on 2006-11-14
Umm.. Back to topic. Suggestions, anyone?

---

### Post by pcjunkie on 2007-02-20
It worked fine b4 update. not sure what changed///

---

### Post by Daveth on 2007-02-26
so, is the crackling with all music sources or just certain file formats, or tracks you ripped yourself? i.e. are you sure it is not a function of the media rather than the hardware?

---

### Post by jolger on 2007-03-06
If (in your alsamixer) you see a tab called something like "AC97" try turning it off ;) (turn it fully down since there is no mute button as far as i know)... That worked for me on my SoundBlaser Live! 

/Jolger

---

