---
title: "AC97 on Ubuntu and WindowsXP"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by SonicSteve on 2006-12-11
OK so here is a strange phenomenon that I've seen over and over again. I'm hoping that one of you out there has seen this also and has some kind of explanation.

I fix mainboards and a common issue I come across is on board sound that no longer works in windows. Sometimes the driver will install properly sometimes it won't. The end is always the same though, the sound doesn't work in windows XP. Even a fresh install and installing the proper driver from the mainboard manufacturers website. 

Here's the strange part. Often a board like this will install and work with Ubuntu perfectly. EVEN THE SOUND WILL WORK?!?!
Why is this? It proves that the sound chip isn't dead, but then why will it not work in windows?

What is so different about the way that Linux (Ubuntu) interacts with the hardware than Windows XP? 

I'm quite stumped on this one!

---

### Post by scrooge_74 on 2006-12-11
I can't tell you why the difference, but from my experience in XP there is probably some irq or dma conflict which makes the sound card not to work

---

### Post by x64Jimbo on 2006-12-11
I'm gonna take a guess here - I'll bet that something in the hardware went sour - not so bad that it stops working, but bad enough that the system fails to recognize it correctly in Windows and it gives up. In Linux, I am betting that the person who wrote the hardware detection scripts was very intelligent and forward thinking, and probably programmed the script to keep trying until it either runs out of options or finds something that works. Windows probably just gives up too easily, but unfortunately that's not something you can readily change.

---

### Post by beldugo on 2006-12-12
easy. the sound is in mute. it happens sometimes when i install a fresh copy of windows. you need to go into volume and unmute it. 

if your getting driver problems you will need to get the original drivers or an older sound driver.

---

### Post by SonicSteve on 2006-12-12
I think x64 Jimbo has possibly hit on somthing. Though it's very hard to prove. 
I do know this however;
1. The sound is not mute, actually I've never seen the sound muted after a fresh install of windows and I've installed windows literally hundreds of times.
2. If it is a DMA conflict or the like it must be brought on by "sour" hardware. Windows doesn't seem to think there is a resource conflict. Often windows says that the device is "working properly" when it isn't. 
3. Almost certainly the hardware is slightly damaged.
     - Why will it work in Ubuntu but not in Windows though, that is the question?

Trust me this phenom isn't just a simple oversight by a noob wanna be tech. There is really something strange going on and I think that X64jimbo may have something. I just wish I knew exactly what.

---

### Post by scrooge_74 on 2006-12-12
A couple of times I had strange things like that: once I had a modem that will get properly recognize, drivers installed but it would not work.  The reason was that I had to manually pick the COM port it wanted to use not what  windows said it had to do.

Other times I had sound cards that will not work unless I use a certain version of their drivers, if I used a new version it will not work it had to be the original one.

---

### Post by SonicSteve on 2006-12-15
Anyone else wanna give a shot at answering this one? Perhaps you actually know what's happening? I would love to know if these sound chips will work in windows. I would even like to know if anyone else has seen what I'm talking about.

---

