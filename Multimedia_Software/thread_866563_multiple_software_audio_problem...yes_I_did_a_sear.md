---
title: "multiple software audio problem...yes I did a search"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Dasani on 2008-07-21
Hi,
My Hardy doesn't play audio from more than one source at a time depending on the software. For example, if I have listen music player running and I start firefox, no video (flash or other) will play sound. All search results on the subject pointed the problem with flash. But I confirmed that this was not the issue as I started audacity with listen already on (firefox off). And when I pressed play in audacity, it said the device was busy. On the other hand, with listen, mplayer has no trouble playing sound.

I know it has something to do with alsa mixer or something, but none of the solutions I found in several posts solved my problem. And from what I read, a lot of people have this problem. I would appreciate a soulution.

Just in general, I don't know how reasonable my statement is, but I think permanent solutions to problems like these are key in the mainstreaming of ubuntu. Out of curiosity, does it have something to do with most hardware being closed sourced?

---

### Post by Dasani on 2008-07-27
bump

---

### Post by Gigopepo on 2008-07-27
I'm having almost the same problem, my audacity can record audio but can't play it.

I tried every possible combination in the audio settings of the softwares and of the OS itself, but with no success...

Anybody?

---

### Post by Matrix_NEU on 2008-07-27
Having similar problems.  If I use flash after starting up, I cannot play audio in rhythm box until I restart.  If I play audio box, flash cannot play sound. Nothing I've seen has addressed this issue.

---

### Post by Dasani on 2008-07-28
well this issue certainly needs more attention.

---

### Post by markbuntu on 2008-07-28
Addressing your problem is difficult because the Linux/Ubuntu audio system is such a mess.  Without knowing in detail the current setup of your audio system it is almost impossible to give good quick advice about remedies.

However, there is a serious problem with flash 9 and its use of pulse audio. This can be partially fixed with flash 10b but not with flash 10b2 which is very buggy. Audacity has its own set of problems.

There is also a number of difficulties in setting up a proper sound system that will play all the various applications that use pulse audio, alsa, and oss at the same time. Each one will try to grab the sound system for its own use and will shut out the other applications unless you are set up just so and this seems to be variable.

As an example it took me about 3 weeks of following all the how-tos and guides that just seemed to make things worse and worse until I finally got everything working together. Many many people have had success with the guides at the top of the page and the How-Tos in the how to forum and the Almost Perfect Pulse Audio Setup thread. I did not.

So, once I figured out what works for me, I made a guide and put up a thread, a few people have tried it and have had some success. Anyway, it does provide some explanation about how pulse audio and alsa work and can be managed so you may learn a little about that.

Good Luck.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Dasani on 2008-07-30
very nice...I'll check out your thread.

thanks for the help

---

