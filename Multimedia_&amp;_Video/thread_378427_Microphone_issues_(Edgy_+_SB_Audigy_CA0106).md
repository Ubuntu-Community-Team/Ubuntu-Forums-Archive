---
title: "Microphone issues (Edgy + SB Audigy CA0106)"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by zeroblitzt on 2007-03-07
Hello.

I haven't had a very good history of using Ubuntu to make music, and this time is no exception. I recorded a song the other day on my 4 track recorder, and connected it to the microphone input on the back of my computer (the input on the soundcard). Through every combination I could think of in Gnome Mixer, I cannot get it to accept sound coming in through there.

I tried Alsamixer as well, but its the same deal. The microphone level is unmuted, at 100%, yet when I try to open Audacity and record (Well actually, it wont even open without giving me a host error!), or sound recorder (actually I've had problems here too... when I hit record, it instantly closes), no sound will come in.

Any tips?

---

### Post by tenjin1 on 2007-03-08
double-click the speaker icon in taskbar top right. Then navigate to the 'Capture' Tab. You should have a 'Microphone' setting with volume sliders (channels). Here, make sure it's unmuted (little speaker icon on bottom left of volume sliders).

If the 'Microphone' setting is not here....add it. 
Go to -> Edit -> Preferences  and check the box next to microphone.

Hope that helps.

---

### Post by zeroblitzt on 2007-03-09
Yep, that was already all done, but still no dice.

---

### Post by sebrock on 2007-03-11
Yep, same problems here. I can't record sound. Funny enough I do hear myself through the speakers when talking into the mic. But no recording is done. I really need this. Microphone supposedly was added end 2005. Somebody must gotten this to work?

---

### Post by tenjin1 on 2007-03-11
What channel do you have your sound coming out of 'Analog Front' or 'IEC958 Center'?

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its an ALSA bug mainly in feisty but they might be using the same version in edgy so its definitely related. I myself have no mic/sound capture/recording capabilities as of the moment. Please Read, Review, Confirm the bug and related info here [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there.

Cheers!!!


GaryBrlow :biggrin:

---

