---
title: "Headphone Jack Doesn't Work"
date: 2019-09-26
forum: Multimedia Software
---

### Post by wasi0013 on 2019-09-26
I'm using ubuntu 16.04 LTS on my [B][hp pavilion 15-cb012tx]("https://support.hp.com/us-en/document/c05573875"). 

[/B]The laptop needs to be restarted with volume 100% to get built in speakers working. If restarted with volume 0% no sounds on built in speaker. I tried installing pulseaudio, alsamixer but in vain. No output in headphone jack no matter what.
here is the detailed information regarding alsa: [http://alsa-project.org/db/?f=0fde8721d636a192acddc8826d4614e7578a47d1](http://alsa-project.org/db/?f=0fde8721d636a192acddc8826d4614e7578a47d1)

---

### Post by Autodave on 2019-09-27
Since no one else has jumped in, let me give you a trick that has worked for me in the past.  Put your volume somewhere around 50%.  Power off the machine.  Plug headphones in.  Power back up.  Do the headphones work now?  How about when you unplug them: do the speakers function?

I had a machine that I avtually had to do that 3 or 4 times on before everything worked properly.  Once it decided to work, I never did have a problem with it after that.

---

### Post by wasi0013 on 2019-09-28
Thanks Autodave, I will try this and let you know.

---

### Post by wasi0013 on 2019-09-30
> **Autodave said:**
> Since no one else has jumped in, let me give you a trick that has worked for me in the past.  Put your volume somewhere around 50%.  Power off the machine.  Plug headphones in.  Power back up.  Do the headphones work now?  How about when you unplug them: do the speakers function?

I had a machine that I avtually had to do that 3 or 4 times on before everything worked properly.  Once it decided to work, I never did have a problem with it after that.

I tried this today, steps that I tried:

1. Put my volume to around 50% (speakers were working) shut down the laptop. It did shutdown properly.
2. Plugged headphone in and turned on the laptop using power button. The headphone worked!
3. Unplugged the headphone. Tested the speaker by increasing / decreasing volumes the speakers didn't work. Plugged back headphone in it was still working. Unplugged it again, tested speakers it didn't work. Plugged headphone in headphone no longer works! 
4. Brought volume back to 50% and shut down laptop. It didn't shut down properly it was stuck with a blinking caps lock key (it was in panic mode) Powered off by press and hold the power button. 
5. Plugged headphone back in. And turned on laptop again this time both headphone and speakers were not working. Unplugged headphone again, brought volume back to 50% and shut down laptop again this time it didn't panic. 
6. Plugged headphone in turned on laptop headphone worked again, but no speakers yet. Unplugged and plugged headphone multiple times it didn't stop working this time. Turned off laptop it stuck in panic mode again.
7. Forcefully turned off laptop plugged headphone in turned it on again, headphone still works but no sound in speakers...

I wonder why does it go to panic mode! The panic mode is random some time it does go to panic sometime it doesn't.

---

### Post by wasi0013 on 2019-09-30
Update: Only left headphone is working. Not both, The right one has some kind of radio like beeping sound.

---

### Post by wasi0013 on 2019-09-30
I tried another stackexchange solution:

> #!/bin/bash
hda-verb /dev/snd/hwC0D0 0x20 SET_COEF_INDEX 0x67
hda-verb /dev/snd/hwC0D0 0x20 SET_PROC_COEF 0x3000


But it didn't work.

---

