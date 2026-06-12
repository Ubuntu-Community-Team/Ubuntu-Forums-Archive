---
title: "No sound in breezy"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by Captn on 2005-10-20
I have a sound blaster live 5.1 and I have no sound, I'm NEW to linux and was wondering if someone could help me get some sound. Thank you in advance. :smile:

---

### Post by Captn on 2005-10-20
[QUOTE=Captn]I have a sound blaster live 5.1 and I have no sound, I'm NEW to linux and was wondering if someone could help me get some sound. Thank you in advance. :smile:[/QUOTE]

Ok I fixed it and have sound, but its not 5.1. Any ideas? Thank you in advance. :confused:

---

### Post by allupinya on 2005-10-20
In my soundblaster live..I had the same problem.
I enabled sound in the setting  "sound system" area set the hardware or 2nd tab to full duplex and the speaker tabs to 6 spkrs.
Then went to the mixer "settings" and enabled all the settings. Make sure you to set the recreate front speakers in the "switchs" area and then adjust the sound thru, master and  PCM for the rear speakers..
Hope that helps

---

### Post by Captn on 2005-10-21
[QUOTE=allupinya]In my soundblaster live..I had the same problem.
I enabled sound in the setting  "sound system" area set the hardware or 2nd tab to full duplex and the speaker tabs to 6 spkrs.
Then went to the mixer "settings" and enabled all the settings. Make sure you to set the recreate front speakers in the "switchs" area and then adjust the sound thru, master and  PCM for the rear speakers..
Hope that helps[/QUOTE]

I'm NEW to linux, where might i find this  "I enabled sound in the setting  "sound system" area set the hardware or 2nd tab to full duplex and the speaker tabs to 6 spkrs"  I'm not seeing this anywhere. Thank you in advance ;)

---

### Post by markdrago on 2005-10-21
I had this problem where my machine seemed to think that sound was working fine, but there was no sound.  I had to change the multimedia system that was being used.

Click on System >> Preferences >> Multimedia Systems Selector.
Change the Default Sink to 'ALSA'

Clicking on 'Test' should produce some sound that you can actually hear.

This worked for me, I hope it works for everyone else as well.

---

### Post by Captn on 2005-10-22
[QUOTE=markdrago]I had this problem where my machine seemed to think that sound was working fine, but there was no sound.  I had to change the multimedia system that was being used.

Click on System >> Preferences >> Multimedia Systems Selector.
Change the Default Sink to 'ALSA'

Clicking on 'Test' should produce some sound that you can actually hear.

This worked for me, I hope it works for everyone else as well.[/QUOTE]

When i click on "test" I get an error box that pops up & it says "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture' "

Any ideas?  :confused:

---

### Post by brutaldrummer on 2005-10-25
I'm having the same problem. I am running a sound blaster live 5.1, I did some researching on google and found a driver replacement but I think you have to buy it. Any alternatives?

---

### Post by avliet on 2005-11-19
My sound /was/ working, then it just stopped.  I suspect that this is an update issue.  Am looking into it, but wouldn't mind some colaboration.

---

