---
title: "microphone, mic., not, working, alsa, oss, capture"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by ComputerGuy56 on 2007-03-11
I think I might've found a solution for the "My microphone isn't working" problem.
Double click the sound icon on your desktop.
Click File, Change Device, Make sure Alsa Mixer is selected.
Click Edit, Preferences, make sure Microphone, Microphone Capture, Microphone Boost, and Capture are selected.
Mute your microphone.
Then select the Capture tab and enable Capture. Make sure Microphone is enabled and microphone boost(for now) is turned off. Now Click Applications -> Sound & Video, Sound Recorder.
Make sure Capture is selected and test if your mic. works.

Good Luck!:popcorn:

---

### Post by ComputerGuy56 on 2007-03-11
Oops, I mixed up the tags and Title...

---

### Post by willskills on 2007-03-12
I will deinfitely give this a blast tonight. I have an SBLive! running EMU10K - playback works great, I have sound in World of Warcraft & can hear multiple people in Ventrilo (running both through aoss & wine)

I cannot get capture to work though, not in sound recorder, or even from the terminal.

I am ready to pay someone to fix this for me.... VNC/SSH however you want to do it ;)

I have been reading and tinkering for about 3 months trying to figure this out (when I have the time) and still no joy.

---

### Post by ComputerGuy56 on 2007-03-12
First thing is(and most basic)make sure your mic. works. I really don't know how to test it but atleast try. On my mic./headset, if I blow into my mic., it sorta echoes it. And if the mic. isn't plugged in, I don't hear anything.

---

### Post by redsoftretro on 2007-03-12
Great! This worked for me. I knew there'd be a dB boost somewhere but didn't know where it was.

Thanks very much.

I'm using Edgy by the way and a £4 Trust mic from Asda (UK).

Sound quality is fine for chatting on Skype etc.

---

### Post by ComputerGuy56 on 2007-03-16
1 So far...Maybe 2

---

### Post by keerikkadan on 2007-03-20
Make sure u have audio device in volume control as alsamixer.
go to terminal . type alsamixer and go to microphone volume bar. Check whether the mic is in mute (off) or in working mode(MM). Select correctly and exit with ESC button. 

Make sure capture is in your volume control using preferences. Mic worked for me. 
good luck.

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a long standing ALSA bug mainly in feisty but the same version might have been applied via updates in edgy/dapper so its related. I myself have no mic/sound capture/recording capabilities as of the moment. Sound capture(mic input etc.) and sound recording features should be working right out of the box like before with no tweaking applied.

Please Read, Review, Confirm the bug and related info here 
 [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there and help Ubuntu become better.

Cheers!!!


GaryBrlow :biggrin:

---

### Post by euchrid on 2007-06-07
I got the microphone working by updating the recently-released Alsa driver.

I posted a load of information here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Seems there a LOT of people with similar problems in Feisty. Hope the next release fixes them!

---

