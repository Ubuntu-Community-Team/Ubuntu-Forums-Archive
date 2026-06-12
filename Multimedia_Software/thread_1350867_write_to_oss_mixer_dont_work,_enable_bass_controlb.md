---
title: "write to oss_mixer dont work, enable bass control/bass boosting..."
date: 2009-12-09
forum: Multimedia Software
---

### Post by teique on 2009-12-09
Hi!

I've been researching for some days now w/o success..

As I read, if I type this command I should enable the Bass control at alsamixer:
echo 'BASS "Bass" 0' >/proc/asound/card0/oss_mixer

It doesnt give error (I typed "sudo bash" before...), but when I type:
cat /proc/asound/card0/oss_mixer

I see no changes, also if I check at alsamixer, no news either.

Also, nobody else seems to be having this problem, so I must be missing some step :/

Any tips?

---------- Here is my oss_mixer if it helps: ----------
VOLUME "Master" 0
BASS "" 0
TREBLE "" 0
SYNTH "" 0
PCM "PCM" 0
SPEAKER "PC Speaker" 0
LINE "Line" 0
MIC "Mic" 0
CD "CD" 0
IMIX "" 0
ALTPCM "" 0
RECLEV "" 0
IGAIN "Capture" 0
OGAIN "" 0
LINE1 "Aux" 0
LINE2 "" 0
LINE3 "" 0
DIGITAL1 "IEC958" 0
DIGITAL2 "" 0
DIGITAL3 "" 0
PHONEIN "Phone" 0
PHONEOUT "Master Mono" 0
VIDEO "Video" 0
RADIO "" 0
MONITOR "" 0

And this is the /proc/asound/cards:
    0 [CK804]: NFORCE - NVidia CK804
    NVidia CK804 with ALC850 at irq 22

Why all this? My new headphones 20hz-22khz arent cool, I had a 8hz-22khz (almost sure) that was great, but it broke :((((((((((((((((

PS.: couldnt find other so specific thread for this subject.

Thx!

---

