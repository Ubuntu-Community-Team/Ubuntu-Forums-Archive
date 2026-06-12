---
title: "Stumped on audio."
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by TheEmb3rEgg on 2006-08-09
I followed the comprehensive audo guide. In the first step, get my soundcard listed by entering the following text in the terminal.

```
aplay -l
```

I get the following text.

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I unmuted everything in alsamixer, but I still have no sound. =/

---

### Post by computergroove on 2006-08-09
Does or has your sound ever worked in this install of linux? If so, when was the last time it worked? What are the specs of your computer? Is it a laptop?

---

### Post by TheEmb3rEgg on 2006-08-10
Does or has your sound ever worked in this install of linux? If so, when was the last time it worked? What are the specs of your computer? Is it a laptop?

It hasn't worked yet. My computer is a desktop pc: 

Dell Dimension 4700

Pentium 4 w/ HT @ 3ghz
768mb 400mhz ddr2 RAM
Intel 915g express chipset (ICH6 integrated 5.1 audio I believe) 

I think that might be enough info.

When I installed Ubuntu, it recognized sound

---

### Post by computergroove on 2006-08-10
You can buy an excellent sound card that works natively with Ubuntu 6.06 for areoun $15 from newegg.com (aopen cobra 6 channel surround). It's what I would do. I tried manually compiling and installing a sound card awhile ago and you can forget that brother. Talk about impossible.
When you say that it recognised sound, do you mean that audio worked with the live cd? That's too bizarre. Dell has pretty good support for linux stuff for thier hardware. check support.dell.com and search for yourself if you dont want to spend any money. Good Luck installing those puppies.

---

### Post by TheEmb3rEgg on 2006-08-10
What I meant by recognized was that I never got an error saying that it wasn't recognized. I could change the volume in alsamixer. I never tried to play audio files in the Live CD. I'll go have a look at Dell. 

Thanks for your help!

---

