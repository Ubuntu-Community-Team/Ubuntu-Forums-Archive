---
title: "Creative Labs VF0400 Microphone sounds like chipmunks"
date: 2010-05-21
forum: Multimedia Software
---

### Post by sir_christopher on 2010-05-21
Hey all,

I just installed Lucid Lynx on a Thinkpad X60 last night in order to wring every last drop of utility out of it, and so my wife might have a notebook that she can use for Skype. I couldn't get the built-in microphone to pick anything up, but figured it didn't matter because I planned to use the one with the Creative Labs VF0400 camera. The problem is, using both Skype's test call, as well as the Sound Recorder program, the sampling rate may be out of whack because playback of anything recorded with the microphone sounds like the chipmunks (as in Alvin, Simon, Theodore) -- it sounds as though the playback has been sped up, though the Skype test call operator sounds just fine. If I can't get the microphone working, then that pretty much kills what I was going to use this computer for, so I was hoping someone might have some insight.

Thanks

---

### Post by shoryuken on 2010-10-25
> **sir_christopher said:**
> Hey all,

I just installed Lucid Lynx on a Thinkpad X60 last night in order to wring every last drop of utility out of it, and so my wife might have a notebook that she can use for Skype. I couldn't get the built-in microphone to pick anything up, but figured it didn't matter because I planned to use the one with the Creative Labs VF0400 camera. The problem is, using both Skype's test call, as well as the Sound Recorder program, the sampling rate may be out of whack because playback of anything recorded with the microphone sounds like the chipmunks (as in Alvin, Simon, Theodore) -- it sounds as though the playback has been sped up, though the Skype test call operator sounds just fine. If I can't get the microphone working, then that pretty much kills what I was going to use this computer for, so I was hoping someone might have some insight.

Thanks

Hi,
I'm having the same problem with VF0400 mic making recorded or streamed voice sound like a chipmunk or like a fast playback. Have you been able to solve this problem?
I'm running ubuntu 10.04 kernel 2.6.32.24.

Cheers

---

### Post by jqdennis on 2011-02-14
Ubuntu 10.10, Creative VF0400, but mine is off in the other direction, vvveeerrryyy   ssslllooowww

---

### Post by sredna on 2011-03-05
i have the same problem as you guys.

i think it has to do with that the device is recognized as having a stereo input, while it actually is in mono.

but i don't know where to fix this.

anyone?

---

### Post by xczxc on 2011-03-08
I have the exact same webcam and the exact same problem, except than when I'm in videocall it works fine. It a normal call (no video) is where the problem starts.

---

### Post by ryanomara on 2011-04-09
Fixed:  Under the Skype -Options -Sound Device turn off the option to 

Allow Skype to adjust my mixer levels.

I also went through the playback devices to change them all to mono, but they were already all set.  The original idea to change this was from this thread: 

[https://help.ubuntu.com/community/SkypeTroubleshooting#Skype%20Audio%20Device](https://help.ubuntu.com/community/SkypeTroubleshooting#Skype%20Audio%20Device)

I was having trouble getting the mic to even work, but through the app Sound Recorder I tried adjusting levels and then suddenly the mic was recognized, but had this crazy playback.  After making the change in Skype -Options "everything" -even Sound Recorder started to work ....

---

### Post by ryanomara on 2011-04-09
Sorry whatever I said fixed the problem, was some sort of glitch which worked, but after shutting down and logging in doesn't.  I am back to no sound....  Sorry again.

---

