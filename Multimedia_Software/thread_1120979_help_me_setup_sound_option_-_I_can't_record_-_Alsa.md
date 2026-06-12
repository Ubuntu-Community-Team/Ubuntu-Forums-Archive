---
title: "help me setup sound option - I can't record - Alsa ALC880"
date: 2009-04-09
forum: Multimedia Software
---

### Post by Ascenti0n on 2009-04-09
I'm having a terrible time trying to get my recording setup on my HP Pavilion PC. I don't know what I'm doing and my little peanut brain has a hard time trying to understand all the configuration options. Let me tell you what I've done and what I need. Please help.

I couldn't record within Audacity using a headset mic through the pink front mic input jack.

I searched the forums. I became convinced from what I read Pulsaudio was not configured  within Intrepid properly, so I followed steps to remove Pulsaudio and Setup Alsa. I'm still having problems.

Other post refer to setting up the sound preferences and there are too many options. I'm just clicking, checking options and testing, nothing is working.

In **System > sound Preferences** 
I have everything set to autodetect EXCEPT sound capture which is set to ALSA. Device is set to HDA Intel (Alsa mixer)
Within the 'device' box, I have checked/highlighted:
Master, PCM, front, front mic, line-in, microphone.

Right clicking on the **volume icon** on the top panel, and selecting preferences, the same options are highlighted as above.

**Selecting 'open volume control**'
**Device** - HDA Intel (Alsa Mixer)
**Playback:** Master, PCM, Front, CD, PC speaker are all on with levels up.
**Recording:** one option - capture, with mic icon marked with 'X', clicking this to presumably switching the mic input on, does not stay off permanent. 
**Switches:** headphones - unchecked.


Oh and in **Audacity > preferences:** both decies for playback and record are set to Alsa: default.

Can somebody please walk me through properly configuring these sound options, so I can record.


Thanks.

---

### Post by Ascenti0n on 2009-04-09
I forgot to mention, in: volume-control-preferences, 'front mic' and Microphone are listed as 'playback' and not 'record' is this correct?

---

### Post by Ascenti0n on 2009-04-09
[SIZE="4"]Can anybody advise please?[/SIZE]

---

### Post by Pkadjipag on 2009-04-10
I hope someone can answer you, I got the same problem.

---

### Post by Ascenti0n on 2009-04-10
OK, I've made SOME progress, but still a little way to go.

I found out that nothing seems to work when plugging the mic into the front mic (pink) jack.

As soon as I plugged the same mic into the rear port, I could hear what was being spoken through the mic, and that is despite both of these options always being available in my sound configuration.

I'm still having problems configuring my sound setup to record through Audacity. I even tried sound recorder. But I can't get it to work yet.

Still, a step in the right direction.

---

### Post by markbuntu on 2009-04-10
You need to set the mic capture in the alsa-mixer. You might want to get

gnome-alsamixer

it is easier to use and has switches for record and mute below the volume controls. or you can open the panel volume control, (the little speaker in the panel) right click and choose open volume control. Click Edit/Preferences and turn on microphone capture and mic boost capture. Microphone capture should now be present in Recording.

---

