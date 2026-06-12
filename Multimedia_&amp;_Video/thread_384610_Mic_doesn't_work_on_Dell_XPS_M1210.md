---
title: "Mic doesn't work on Dell XPS M1210"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by 1002285 on 2007-03-14
I have always been able to listen to music and see movies with my

Dell XPS M1210 laptop with integrated audio card

on Ubuntu - Dapper and Edgy and now Feisty,

but the microphone has never worked I guess. I have only tried a couple of monhhs ago when I needed to use Skype (I had Edgy then), and I couldn't get it to work. I have now tried Skype and Audacity and sound recorder, and have checked my sound settings acoording to some instructions I found in threads here, but I guess that the system does not see the mic input at all. It does not work in any of the 3 plugs that Dell has (1 for mic and 2 for ouput).

I can use the same mic fine in Windows and the same computer, but I don't want to log into Windows every time I need to use Skype. Any ideas?

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a long standing ALSA bug in feisty. I myself have no mic/sound capture/recording capabilities as of the moment. Please Read, Review, Confirm the bug and related info here [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there.

Cheers!!!


GaryBrlow  :biggrin:

---

### Post by flerchjj on 2007-06-21
I'm having a similar problem.  I just bought a Dell Dimension E520 and the line-in doesn't work.  I've tried installing kmix & several other things... nothing seems to work.

---

### Post by flerchjj on 2007-06-22
Don't like posting immediately after myself, but I wanted to make sure notification was sent out.

I'm still playing with it, but it looks like the audio lines are all mis-routed for ALSA on my new Dell Dimension E520 that came with Ubuntu 7.04.  The ALSA Line was routed to the Rear Mic (Pink), the ALSA Front Mic was routed to the Front Mic, and the ALSA Rear Mic was routed to the Stereo Output Rear Channel (Black)... go figure.

The easiest way I've found to test inputs with ALSA (assuming your speakers work) is to open the terminal & type 
```
arecord | aplay
```
This will route your currently selected ALSA input (from the Volume Control aka ALSA Mixer) to the speakers.  You can then move from audio jack to audio jack with your input to find where ALSA is reading from.

Maybe it has similar issues and is reading a different/wrong jack as the mic input.  Sound quality isn't that great yet (hear ~16kHz tones occasionally).

---

### Post by mccurry on 2007-10-05
Skype works fine after a litte config.  However thats with onboard mic.  I can't get external to work, and when I record with onboard in audacity I get a click which is REALLY annoying since I podcast.

---

