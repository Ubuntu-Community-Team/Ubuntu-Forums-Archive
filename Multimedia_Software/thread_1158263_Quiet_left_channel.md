---
title: "Quiet left channel"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Tarvok on 2009-05-13
Since I've updated to 9.04, I seem to be having worse sound problems than I had before. The problem is that same old one: the left channel has extremely low volume. In the past, I've been able to fix this by raising the left channel volume up to maximum and waiting for the proper volume to be restored; then I could bring it back down to where I wanted it. I generally didn't need to do this more than once per session.

But now, that left channel seems to be all but disappearing every few minutes, and sometimes (like now) it doesn't seem to matter how long I leave it at maximum: left channel audio is just plain screwed up.

I'd like to formally report this as a bug, but I am under the understanding that I'd need to know what package the problem is located in, and I don't know whether the problem is in alsa, the kernel itself, or some other package I don't know about. How can I go about figuring this out?

It also seems that this issue is common, but not universal. Any ideas on why?

I'm running Ubuntu 9.04, 64 bit
AMD Sempron 64
Radeon 9200 Pro
nVidia nForce 3

---

### Post by Tarvok on 2009-05-14
I know its not a hardware problem. I've got my MP3 player plugged into the speakers right now, and the balance is just fine. Is there any additional information I should provide?

EDIT: Since jacking up the master volume wasn't helping (I'd get brief bursts of clarity, followed by drops regardless of whether I dropped the volume back down to match the right or left it in place), I tried messing with the PCM left channel. That seems to have worked... for now.

Wait, no. It dropped again as I was typing. Since messing with the source volume helps, I'm going to see if it does the same with audio coming through the mic port and the line-in.

I'd still like to file a proper bug report, but what package is this error likely to be located? Or do I even really need to know that for something like this?

---

