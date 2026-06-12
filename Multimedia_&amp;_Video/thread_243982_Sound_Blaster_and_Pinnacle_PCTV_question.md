---
title: "Sound Blaster and Pinnacle PCTV question"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by chrroessner on 2006-08-25
Hi,

I have a Sound Blaster Audigy SE and a Pinnacle PCTV 300i card. The TV card is connected to the aux port on the sound card.

Regular sounds are working. But how can I get the TV card playing sound? There is no aux in alsamixer. I do not know how to set capturing to aux.

The sound card uses the snd_ca0106. I would like to use tvtime as tv application. So what should the line <option name="MixerDevice" value="/dev/mixer:line"/> look like?

Any help would be really great.

Thanks in advance

Christian

---

### Post by chrroessner on 2006-08-26
bump

Maybe I could split my question:

a) What is the name of the alsamixer control for aux? Do I need a special asoundrc or something else?

b) What is the device name for appications like tvtime

Is there noone who has a Creative Soundblaster Audigy SE with any device connected to the aux port?

Is there some more inoormation needed to help me answering my question?

---

### Post by chrroessner on 2006-09-01
bump :-(

---

### Post by cylon359 on 2006-09-04
I've heard these cards can't do capture (although I presume you just want pass through?) with the dapper drivers.  It'll be supported in Edgy.

---

### Post by chrroessner on 2006-09-04
Well, I have taken the alsa 1.0.11 drivers from Debian unstable and have backported them for dapper drake.

I also have viewed the source code from alsa 1.0.12, but the ca0106 driver got only minor changes.

I can not understand that the is no one who has connected anything to the aux port and does not want to listen to this device. I mean this is one of the most basic features and damn alsa stuff is much to difficult for normal users. I mean:

Why is there no aux control in the alsamixer that I can push up and then listen to the connected device? I think that the ca0106 is very young (0.0.17 or so) and maybe these features are simply missing. Also the Master, PCM, CD controls are all missing.

I think I have to ask the person who implemented the ca0106. But thanks anyway.

Regards

Christian

---

### Post by TheBigJimbrowski on 2007-01-10
Hi, I don't know if this will answer your question or not, but I had been pulling my hair out over a similar problem for a little while.

Firstly, I made sure that my Pinnacle's audio out cable was connected to my soundcard's 'aux' input on the card (this is the same as the type of cable which connects the CD to the sound card) This is important, as the Pinnacle card does not send its audio signal through the card, it is an external cable, without this cable, its IMPOSSIBLE to have sound from a pinnacle card. If your setup worked before in Windows then this isn't your issue of course.

Then, in the volume control panel (double click the speaker top right), go to->edit?->Change device->select your soundblaster.

Then click 'preferences' and enable the 'aux' input on the card, un-mute it and turn up the volume. Ahhh, if only all my problems were that simple (even though it took me days to find the solution :)

Hope that helps.

---

