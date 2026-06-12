---
title: "microphone: It's always the simple stuff..."
date: 2008-06-04
forum: Multimedia Software
---

### Post by uncleclinto on 2008-06-04
Okay, 

I can't record sound using audacity or sound recorder.  I swear I could at some point in the past.  I can turn those programs on... apparently their finding my card because I get no errors.  The problem is, no sound records.  Sound Recorder even says it's recording, but the slider doesn't move.  When I playback, I get nothing.  My flavor is Ubuntu Studio 7.04.  Can anyone tell me the magical formula to getting my mic to work???  I would just enter Synaptic and put a check next to everything with the word alsa in it, but I imagine that may cause problems.

Thanks in advance,
Clint

---

### Post by z0mbie on 2008-06-04
Have selected Mono in the Channel recording option of Audacity?

---

### Post by uncleclinto on 2008-06-05
> **z0mbie said:**
> Have selected Mono in the Channel recording option of Audacity?

Yes... I think the issue is simply driver related or something... I don't think my system is recognizing the mic.  As I said, sound recorder doesn't work either...

---

### Post by uncleclinto on 2008-06-24
Does anyone answer these things anymore... it's been two weeks... tap tap tap... hello??  Could someone at least give me an "I'm not sure" shout out so I know folks are reading my posts and I'm not being shunned or something??

---

### Post by jualin on 2008-06-24
hey there, sorry for the delay. The past week I had a similar problem and I solved it by playing with the "Volume Preferences Interface" (double clicking on the speaker icon). I noticed that my computer had two mics. You should try different options there like raising the volume of "Digital" or others. My solution was to enable recording with "Mic" and not Front Mic, maybe that could point you in the right direction. Hope this helps!

---

### Post by Phosphoric on 2008-06-25
have you had a look at Alsamixer in the terminal?

That will show you if you have the mic input enabled.  I struggled with this for a long time but got it fixed in the end.

Sorry I don't have any details for you as I'm at work but try searching for Alsamixer and how to use it.

Good luck.

---

### Post by jualin on 2008-06-25
Did you get it to work?

---

