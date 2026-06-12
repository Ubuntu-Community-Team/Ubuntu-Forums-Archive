---
title: "Openshot: Launches in pause and won't play mp4"
date: 2016-03-12
forum: Multimedia Software
---

### Post by Bucky Ball on 2016-03-12
Hi all,

Strange problem. Have been hunting but found nothing to fix and very few clues. Attempting to post on the Openshot forum but can't figure out how to register! Anyway ...

New build, i7 6700, Nvidia GTX 970, 16Gb RAM, Xubuntu-core 15.10. 

Simple story: 
- Launch Openshot, starts in pause;
- Import 1080, 25fps mp4 file;
- Drop it into the timeline;
- Hit play;
- Nothing, just sits there. 

And that is all. Of course, as it started paused, I hit play numerous times for luck and still nothing. Have tried tweaking settings in Preferences, but no joy. 

Something is obviously not right from the get go as it's starting paused and it's also 'crashy', as in, it locks up at what seems like random times and eventually I get the 'program busy, would you like to terminate' window, if I haven't used 'xkill' to detonate it already. 

Any suggestions would be greatly appreciated. I can get around this with other software but Openshot would really save some time on the project I'm doing. Fire away if any info required.

[I have 16.04 LTS installed on another partition so I'll try on that, see if I get the same issue and report back. I don't intend to seek support with 16.04 on this thread, but trying it there may give clues as to where the problem is happening. If it works there, it is possibly a 15.10 thing. If it doesn't, maybe it's related to Openshot and a hardware issue/setting/thing!] 

PS: Using the same install I'm editing, previewing and syncing with audio the same mp4 video files using  Blender, Audacity and VLC and all that is working faultlessly and going swimmingly.

---

### Post by Bucky Ball on 2016-03-12
Update on this: Openshot works fine in a fully updated/upgraded 16.04 LTS install. Launch Openshot and it doesn't start in 'Paused', a good sign, hit play and it does so with audio all good. So that means the issue is probably 15.10 specific. Hmm. :-k

I'd really rather not be using a dev version for production stuff so back to 15.10 for a bit more digging between doing other things ...

I only ever usually use LTS releases but as this was a new build with new hardware thought I'd better go with the newest supported release. Should have installed 14.04 LTS as I've had nothing but weird anomalies with this interim (and others in the past, one of the reasons I stick to LTS).

---

### Post by Bucky Ball on 2016-03-12
Further update: Just booted back into 15.10 after testing in 16.04, launch Openshot and this time it doesn't open in 'Paused', plonk a clip in the timeline, hit play and ... it works fine!

Go figure. I have done absolutely nothing to it since yesterday when it wasn't working. Only just booted into 15.10 for the first time today. *shrugs*

Guess this little time-wasting trip down a dead-end side alley can be considered solved. Solution: Have a good night's sleep and completely ignore the issue for 24 hours. Boot the machine and it's fixed. Thankyou techno-elves that toil unseen and unheard in the wee hours to fix these things while I count sheep ...

* Unsolving. I was in 16.04 still! LOL. Anyway, that's not it. Booted back to 15.10 and, almost as oddly as I thought had happened, video ran fine, but no audio.

---

### Post by Linuxisfast on 2016-03-14
Hi which version of Openshot are you using. I use Openshot 2.06 installed via their PPA on Ubuntu 14.04.4 LTS. Works quite good even with 4K movies. I have a i7 4790 with GeForce 610 card.

---

### Post by Bucky Ball on 2016-03-14
Working fine now. Not interested in manually installing PPAs. I avoid that and don't see it as a fix unless the version I'm using is known to be broken for everyone, which it's not.

Have no idea why it is suddenly working, as I say, I simply went to sleep for the night and when I woke up, fixed. Maybe it was something I'd done a few hours earlier in the night and wasn't until I switched off it took effect.

I have realised why sound isn't working and that has nothing whatsoever to do with Openshot. Audio is actually working from that. Related to a rather obscure problem to do with my audio interface not waking after I bring the computer out of suspend. Another story.

Solved. Again.

---

### Post by Linuxisfast on 2016-03-14
Well for version 2.0 need the PPA. It is done by the author of Openshot so it works good.

---

