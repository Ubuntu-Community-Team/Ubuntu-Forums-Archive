---
title: "Help: 5.1 sound card 2.1 speakers w/ sub"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Robs227 on 2008-12-07
Hi everyone,

This is my first post. I could find similar topics to this one with the search button but nothing that gave me a solution.

I have a 5.1 sound card: Encore ENM232-6VIA
My speakers are 2.1 w/ sub and work with one input jack plugged into the sound card.
OS: Ubuntu 8.10
Music software: Audacious

My sound for the most part works (which I am thankful for), the problem is that certain sounds are not being played. For example, instrumentals are missing in songs and the sub is weak. I have concluded that the reason for this is that under a 5.1 speaker system certain sounds are only played on back/rear speakers. There are separate output jacks for the front speakers, rear, and sub. I obviously have nothing plugged into the rear or sub output jack on the sound card because, like I describe above, there is only one input jack (male end) for the 2.1 speakers. Hence the problem!

In winxp you can configure the sound card to play as with 2.1 speaker system, that way all sound goes thru the main output jack on the sound card. **But how do I do this in Ubuntu?**

Thank you for your help.

---

### Post by Robs227 on 2008-12-07
For some reason the problem with the lack of some instrumentals seemed to have solved itself. At least I cannot figure out what solved the problem. Possibly an automatic update? 

The sub sound was still weak so I tried to edit ~/.pulse/default.pa by copying a daemon file which ruined the sound completely so I restored it to the original version I had when all the instruments were being played, but now I am back a square one! Meaning instruments aren't getting played even though I restored default.pa back to how it was when they were working.

Therefore I still need help! Thanks

---

### Post by Robs227 on 2008-12-09
Bump. Still need help please!

---

### Post by piratebill on 2008-12-09
Is there a setting in Audacious to specify the speaker setup you have?  I have never used Audacious, just amarok.  I know amarok has settings were you can tell it how many speakers to use.  Sorry I can not be much more help than that.

---

### Post by Robs227 on 2008-12-09
Thanks for your response! I tried what you suggested and I downloaded Amarok, tried the correct speaker configuration by setting it to ALSA and choosing 2.1 but this did not help. I think this is a pulse audio issue but I'm not sure anymore. I'm not sure if the problem can be solved using a media player, either. 


!!!OKAY I REALIZED SOMETHING CRITICAL!!! It is actually the left speaker that is not working at all and that is why certain instruments cannot be heard.
1. This is not a speaker hardware related issue, the speakers work fine in winxp
2. Yes I am sure the volume level of the left speaker is turned up through the volume control panel
3. When I test the speakers in PulseAudio Volume Meter it shows that the left speaker is working even though it clearly is not.

SO what is causing this problem?

Still another development: New theory: My sub is being mistaken for a left speaker and the left speaker is being ignored. This would explain the weakness of the sub.

---

### Post by Robs227 on 2008-12-11
bump

---

