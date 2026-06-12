---
title: "Fornt mic problem"
date: 2008-09-04
forum: Multimedia Software
---

### Post by oguzy on 2008-09-04
I have been trying to run my front mic at my laptop. Unfortunatelly i couldn't managed it run although i installed the alsa-driver 1.0.17. When i plug the headphone and use its mic, i am able to record. I changed the alsa.base module file according to the Alsa Project sites explanation and added "options snd-hda-intel model=basic" I opened front, front mic and capture options also at the volume manager and muted the other mics and choose internat mic at the source part. Still no way. 

Se below is the berief into:

At the volume-manager i have Front, Front Mic, Front Mic Boost is unmuted. At the Recording pane i have Capture unmouted. I have headphones is checked at the Switches pane. And at the Options part i have Internal Mic is choosed. 
My Codec is Realtek ALC269, i have added the related module option to the alsa-base file which mentioned above. But it seems something is missing. Anybody have an idea?

O&#287;uz Yar&#305;mtepe
[http://www.loopbacking.info](http://www.loopbacking.info)

---

### Post by clekstro on 2008-09-04
I would recommend trying the tutorial on this site:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

That said, I have not gotten the microphone to work using this method, even after compiling all three alsa packages from source (alsa-driver, alsa-lib, alsa-utils).  The rest of the sound is working, but the internal mic just seems to hiss really loudly, and no sounds can be heard when trying to record.

Anyone else have any ideas?  I'll be checking through the forums, and if I find my solution I'll post it here, as both of us have the hda-intel card.
Hope the tutorial works...

---

