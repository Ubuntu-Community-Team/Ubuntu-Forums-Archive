---
title: "Ubuntu not recognizing my sound card"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by snkngshps on 2008-03-09
Yesterday I installed ubuntu 7. This was my first time using Linux. It was recognizing my sound card but I wasn't able to get any sound to come out (I checked and made sure nothing was muted, channels up, switches right, etc.) So I decided I would just go ahead and upgrade to Ubuntu 8.04 and see if that happened to fix it up. Now it recognizes the card but not as a sound card. How do i set it as a sound card? The sound card is a Sound Blaster Audigy 2 ZS Notebook. Here is what it gives me when I put the command "sudo lshw -class sound":

*-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=20 mingnt=2

---

### Post by Marzhall on 2008-03-09
Hey!
According to [this,]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/200182") it seems like this problem actually has to do with the linux kernel's alsa (sound) driver- I'm not too good with fixing stuff, but I'd give this bug a good google search. After that, if nothing shows up, then I'd switch to a version of ubuntu with an older kernel until something does- you should then have sound on the older kernel.

Also, welcome to ubuntu! You're about as lucky with your first computer as I was when I started about two years ago- I had an ATI chip set and I didn't even know what the hell that meant :P. Good luck!

---

### Post by superprash2003 on 2008-03-10
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by snkngshps on 2008-03-10
**Marzhall** thanks for that info! After doing some searching I don't see any fixes for this.. I guess I'm going to have to revert back to Gutsy 7.10. Is there a quick terminal command that will go back to this older version?

**superprash2003** I appreciate the response. The only thing is, when I try to open up my sound settings it tells me there are no sound devices installed, so there is nothing there for me to play around with.

---

### Post by khuxtable on 2008-03-10
I'm running Gutsy 7.10 andI have a similar problem with the ALC889a onboard sound in my Gigabyte GA-73PVM-S2H mobo.

Doing "sudo lshw -class sound" I get

  *-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

I recompiled and installed ALSA (version 1.0.16) and have no /proc/asound directory.

This doesn't seem right. Doing "modprobe soundcore" reveals the presence of soundcore.

Others have gotten this to work. Why can't I?

---

### Post by khuxtable on 2008-03-10
Okay, I'm working now. Removing/purging the alsa stuff and reinstalling it did the trick. I'd swear I've done this before...

---

### Post by snkngshps on 2008-03-10
I tried that a few times but I've had no luck. I went through the troubleshooting guide (the sticky post in this category) and I get to one part and I hit a dead end. I'm pretty sure I need to build a driver for my sound card.. the problem is, I have no idea how to do that. If anyone can help me, [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1) My sound card is the Sound Blaster Audigy 2 ZS Notebook. What do I do from here?

---

### Post by Marzhall on 2008-03-10
> **snkngshps said:**
> I tried that a few times but I've had no luck. I went through the troubleshooting guide (the sticky post in this category) and I get to one part and I hit a dead end. I'm pretty sure I need to build a driver for my sound card.. the problem is, I have no idea how to do that. If anyone can help me, [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1) My sound card is the Sound Blaster Audigy 2 ZS Notebook. What do I do from here?

Out of curiosity, at what part did you hit the dead end?

Also, building a driver may be tough- I've never really tried it before. I'd think seriously about your skills before attempting that, and how much time you have to devote to learning how to do it. Hopefully, we can find out a work-around before you're left with that option.

---

