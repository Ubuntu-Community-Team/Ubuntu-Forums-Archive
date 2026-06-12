---
title: "Sound is back - ludicrously simple!"
date: 2011-08-18
forum: Multimedia Software
---

### Post by kle on 2011-08-18
I'm not saying that this is the solution for everybody, but... I thought I'd just mention it because I have a fresh install of Ubuntu Lucid (10.04), after having emigrated from a fresh install of Kubuntu 10.04 - and neither Kubuntu nor Ubuntu gave me sound from the laptop speakers, just from the mini jack and USB speakers. 

What I'm saying is that I did not trash the sound, it simply went away after I forget what kernel update, and no reinstall of Kubuntu or Ubuntu would bring it back.

I have been fretting about this for some weeks. Today I revisited this page: 

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
Fairly far down the page I find this: 
[INDENT]In System/Administration/Users and Groups, make sure that your normal user and the root user are members of the following 5 groups:

pulse

pulse-access

pulse-rt

audio

video [/INDENT]

Well, would you believe it: I was not a member of any of these groups. The groups are there. My name is listed below, but the check box beside my name is not checked. 

So if you have had sound before, and suddenly lost it, go check your users and groups. You may have been "unchecked" as a member of the above groups during a kernel update.

---

