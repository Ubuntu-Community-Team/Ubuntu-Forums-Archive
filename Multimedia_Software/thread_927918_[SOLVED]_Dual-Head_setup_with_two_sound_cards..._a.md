---
title: "[SOLVED] Dual-Head setup with two sound cards... asoundrc??"
date: 2008-09-23
forum: Multimedia Software
---

### Post by taiwanjohn on 2008-09-23
I'm building a box for a coffee shop, for two main purposes: 1. Play music over the main speakers; and 2. Run slingbox on a separate screen, with separate speakers. (Those in the main seating area will hear music, but those seated at the bar can watch and listen to slingbox tv.) 

After a bit of wrangling, I got the two-headed display to work the way I want. But I'm still stuck on the sound problem... I've got SlingPlayer running on the 2nd screen (under WinXP in VirtualBox) and right now the sound is coming out of the main/default device under KDE. So that half of the problem is solved (for now, at least...;-) 

The next step is to get Amarok (or some other player) working on the other sound device (or at least another channel on the same device, with its own plug and independent volume control). 

I'm not at the shop right now, so I can't provide any hard data on the hardware, etc., but I'll update this thread tomorrow. In the meantime, I thought I'd start a thread about this, and see if anything turns up on these questions... 

1. What docs should I be looking for? 
I spent a few hours googling and reading today, and learned a lot. But most info about multiple sound cards seems to be about combining them into a single virtual card. I want the opposite (separate, independent outputs for two different audio programs). If anyone knows of a tutorial or how-to about this, please let me know. 

2. Do I really need two sound cards for this? 
Is it possible to run two different audio programs on different channels of the same card? (IE: Could I plug the main speakers into the back and the SlingBox speakers in the front?) 

3. Is ALSA the best choice for this purpose? 
From what I've read, ALSA seems like the "Swiss Army Knife" of sound... it should be able to handle this task. But if there's another way to do it, I'm all ears... 

I'm sure there's a way to do this, and I reckon I'll figure it out on my own eventually. But if someone could give me a nudge in the right direction, I'd sure appreciate it. 

Thanks, 

--jrd

---

### Post by huwnet on 2008-09-23
What you want may be easier with Pulseaudio :)

---

### Post by markbuntu on 2008-09-23
You can do this easily with Pulse Audio:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

I have two sound cards and Pulseaudio makes my life very easy. It is simple to switch applicatione between the cards and control the individual volumes. I also have a virtual device that I can switch to to use both of them simultaneously with just a few clicks.

I also have a more extensive guide on sound in Ubuntu here. It is mostly a troubleshooting guide but explains a lot and has many many links to more info:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by taiwanjohn on 2008-09-25
Thanks, Mark, for your excellent instructions. That solved the problem for me. 

Actually, I had some trouble for a while, due to the Creative Audigy card (ca0106) not playing nice with the on-board Intel sound device. Finally I just pulled the Audigy out and bought an el-cheapo ($6) USB sound dongle. Everything worked on the first try. ;-) 

Cheers, 

--jrd

---

