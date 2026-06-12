---
title: "Single App Sound! Pulseaudio is FAIL!"
date: 2008-07-28
forum: Multimedia Software
---

### Post by pikseli@work on 2008-07-28
Problem:
Only single application has access to sound.

HW:
Intel 945 series Asus P3 Pundit.

Not happy. Is this 1996 or something? Please! I have tweaked to no end for about 3 months. Things worked so well on Ubuntu 7.04

I also have tried different flavours of 8.04: Ubuntu Studio, Xubuntu, tried installing different mixers as per advice online.

My conclusions:
- Theres something fundamentally flawed with Pulseaudio.
- Ubuntu Studio is TOTAL CRAP. It does not deserve its name "Studio". None of the RT apps worked (not on any buffer size/amount of tweaking). And the 'video editors' were a bad joke. 

Releasing OS like this as any other than Alpha is a JOKE!

- DO NOT waste your time on trying to do A) Sound recording, B) Video Editing on Ubuntu.

:mad:

---

### Post by xc3RnbFO8P on 2008-07-28
Read this:
[http://ubuntuforums.org/showthread.php?t=852822]("http://ubuntuforums.org/showthread.php?t=852822")

---

### Post by pikseli@work on 2008-07-28
Your tweak similar to what I have tried already.

Thanks, and sorry but what I need is a working audio driver layer, not tweaks that put my compu on its knees so that playing mp3 audio takes 50% of the 2.2GHz dual processor computing power.

Would you build your house with chewing gum and tape, too? 

I am dreaming that some day someone will tell me there is some new audio layer that works great fresh out the oven in a repo somewhere.

---

### Post by wolfen69 on 2008-07-28
i suggest trying [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") fix. it may be a bit involved, but works for alot of people. if you do not want to take 10 min to do this, perhaps windows is better suited for you. good luck.

---

### Post by pikseli@work on 2008-07-29
Thanks, Looks like I have not tried that solution. Not sure anymore what I have tried.

And dont get me wrong, I am not one of those people who cannot shovel the OS dirt. I am a developer. I have been using debian long before Ubuntu. But to release an OS that has such a crappy audio layer as final, thats next to lying. 

I am already thinking I need to move on from Ubuntu if I want to make music instead of spending my nights doing the same thing I do at work.

---

### Post by nekt on 2008-09-12
Yeah, what a joke of an idea to include pulseaudio.  The only thing less thought out then the notion to include the buggy piece of dung was the explanation as to why.  So developers don't have to code for windows and linux sound.  COME ON?  Break everything in an LTS release for future compatibility?

What it really sounds like is someone at debian got control of the leech ubuntu and decided to run it into the ground.  

Needless to say I have no faith in the security of the ubuntu repositories after a blunder as big as this.

---

### Post by markbuntu on 2008-09-12
You can read my guide here if you are really wanting a comprehensive fix for your audio problems:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

There are links to just about every troubleshooting and setup thread for sound problems. 

Pulseaudio works fantastic once you get it set up properly and have all the controls and plugins which for some unfathomable reason were left out from the basic Hardy install.

---

### Post by Hackbert's Celine on 2008-10-15
OMG who was it? Who did that damm thing into Ubuntu? There are so little improvements to a Desktop user, so WHY PUT IN IN THE TRUNK?????? Why not in Ubuntu Studio or why not write a usefull howto install it IF YOU WANT? I dont want it. I dont want my Porn to be played over Headphone while music is playing loud. I think in Hardy a lot of things gone worse then Gutsy and i have read a lot of posts like " ill go back to Gutsy".
If Ibex wont change that direction of roadmap, i will completely quit that lazy linux and go back to Debian stable or something.:(:(:(

PLEASE REMOVE PULSEAUDIO FROM UBUNTU PLEASE

---

### Post by markbuntu on 2008-10-15
Good luck with that. Almost all major desktop distributions have already moved to PulseAudio and for those who use them PulseAudio is not a big problem like in Ubuntu. This is not the fault of PulseAudio, it is the fault of Ubuntu.

The excuse of the ubuntu devs is that they did not have the room but really, like 27 stupid games are more important than basic sound functionality.

---

### Post by Endolith on 2009-05-30
The problem is that Ubuntu Studio is supposed to be capable of doing real time audio processing, and PulseAudio is not compatible with anything in Ubuntu Studio, right?

---

### Post by rookcifer on 2009-05-30
> **pikseli@work said:**
> Problem:
Only single application has access to sound.

HW:
Intel 945 series Asus P3 Pundit.

Not happy. Is this 1996 or something? Please! I have tweaked to no end for about 3 months. Things worked so well on Ubuntu 7.04

I also have tried different flavours of 8.04: Ubuntu Studio, Xubuntu, tried installing different mixers as per advice online.

My conclusions:
- Theres something fundamentally flawed with Pulseaudio.
- Ubuntu Studio is TOTAL CRAP. It does not deserve its name "Studio". None of the RT apps worked (not on any buffer size/amount of tweaking). And the 'video editors' were a bad joke. 

Releasing OS like this as any other than Alpha is a JOKE!

- DO NOT waste your time on trying to do A) Sound recording, B) Video Editing on Ubuntu.

:mad:


Welcome to the "I hate Pulseaudio" club.  You are not alone.

---

### Post by Endolith on 2009-05-30
Even the developer of PulseAudio calls it "the software that currently breaks your audio".

There is supposedly a JACK module for PulseAudio, but I can't find how to use it, how to get it, what it does, etc etc

---

### Post by Rhemat on 2010-02-22
I'm having issues with PulseAudio as well.  For a while it was fixed, but yesterday it decided to break my audio, mid-session, for no reason.  If it is broken again (like I think it is), then I will have to go back to removing it and then reinstalling it again, every two day.  What really makes this harrowing, is that the Ubuntu-Desktop package is referrenced as dependent upon PA.  Just think about that for a moment.  The Ubuntu Desktop depends upon PulseAudio.  If you uninstall the PulseAudio libraries, it unstalls the Ubuntu-Desktop Package.  There is no reason they couldn't have stuck with ALSA, or ESD, or something that was working just fine before.
If they're going to keep PA in Ubuntu, I would really appreciate a patch that fixes these issues.  Otherwise, let us dump PA.

---

