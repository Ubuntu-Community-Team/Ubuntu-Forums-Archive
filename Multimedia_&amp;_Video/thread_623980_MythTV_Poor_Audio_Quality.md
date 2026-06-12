---
title: "MythTV Poor Audio Quality"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by ehiebert on 2007-11-26
**Hardware Environment:**
AMD x86_64
NVIDIA MC51 (snd_hda_intel module)
NVIDIA 6150SE onbard graphics 
Hauppauge WintTV HVR-950 USB/ATSC/NTSC tuner card.

**Software Environment:**
Ubunto Gutsy (7.10) x86_64
Intalled Mythbuntu **after** everything in Ubuntu was already working.

**Currently Working**
Everything!!! Audio and Video with Amarok, mplayer, Kaiffeine, etc. 
TvTime gives great pictures and audio played with sox sounds good but has buffer delay (2 seconds delay).

I am trying to use Myth to as the PVR it claims to be, but the audio sounds abolutely awful. The audio device is /dev/dsp1 and is a 16-bit OSS device at 48K sample rate. I have my audio setup pointed to /dev/dsp1, but ther are no options for setup other than sample rate. When I use 48K or Restricted = NONE, I get audo that seems like it is only sampling at 8-bit resolution. There is quealing, and lots of pops and clicks as the lower 8-bits of sampling do not reflext a valid ADPCM stream.

Does anyone have a fix to set MythTV to sample 16-bits?

TIA for any help.

---

### Post by Skerit on 2008-01-30
TV Tuner problems don't get a lot of response on these forums (which in some way is understandable ...)

I'm having the same problem....

/dev/dsp is the regular soundcard, when I use this (with my line in) the sound *locally* is perfect, but the sound doesn't "travel" with it over my network, so on any other computer in the house it remains quiet..

The gentoo wiki told me to use /dev/dsp1 -- because that would be the audio device on the tuner card. Indeed, it is. I'm getting sound but, as ehiebert said, it's horrifying!

Has anyone else ever had this problem?

---

