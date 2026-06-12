---
title: "no sound on Ubuntu though software acts as if normal"
date: 2011-02-17
forum: Multimedia Software
---

### Post by EthioJOB on 2011-02-17
Hi,

I installed Windows &  Ubuntu for dual-boot on my PC once and but the sound didn't work. Well I had the hard disk formatted and installed both OSes again, and the sound came back. Its working for Windows. However, there is no sound for Ubuntu, even though the software acts as if the sound is playing normally. Video shows normally, volume indicators act as if the sound is playing normally but there is no sound whatsoever. Doesn't look like a hardware issue; otherwise it  wouldn't have been working for windows. Any suggestions?

---

### Post by EthioJOB on 2011-02-21
hey, its been a while could someone please help me out with the sound issue? Thanks

---

### Post by aeiah on 2011-02-21
problems like this often come down to a channel being muted. i know you looked in volume control, etc.. but maybe all of them weren't shown. try alsamixer in the terminal. my soundcard mutes if i have SPDIF turned on, which i discovered through fiddling with alsamixer...

---

### Post by SleepWalkerX on 2011-02-21
1) Open up System -> Preferences -> Sound.

2) Go to the Hardware tab.  Do you see your audio device listed?  Click on "Test Speakers".  Do you hear audio?

3) If so, play an audio or video file.  Now go over to the Applications tab.  Do you see your application?  Is the volume high enough?

---

### Post by EthioJOB on 2011-02-26
> **aeiah said:**
> problems like this often come down to a channel being muted. i know you looked in volume control, etc.. but maybe all of them weren't shown. try alsamixer in the terminal. my soundcard mutes if i have SPDIF turned on, which i discovered through fiddling with alsamixer...

 How do I open alsamixer in terminal? I typed alsamixer but doesn't recognize it. (I'm an offline user, so if it happens to need an internet connection we'll need something else).

        > 1) Open up System -> Preferences -> Sound.

2) Go to the Hardware tab.  Do you see your audio device listed?  Click on "Test Speakers".  Do you hear audio?

3) If so, play an audio or video file. Now go over to the Applications tab. Do you see your application? Is the volume high enough?My audio device is an onboard one - ICH7 chipset. The hardware list doesn't seem to list it but I'm not sure the list refers to the specific devices themselves; just saying. Video plays normal. "Test Speakers" doesn't bring any audio. Audio ***acts*** as if it plays normal; as I said, all the volume controls act as if the sound is normal (i think its called dummy sound) but no sound comes out from the speakers or anything.

---

### Post by raidflex on 2011-02-26
I have the exact same issue. Everything appears to be working properly and I can play audio files and nothing is muted but I do not hear any sound.

---

### Post by EthioJOB on 2011-02-28
Seems that there are more others with this issue. Would really appreciate any help.

---

### Post by EthioJOB on 2011-03-01
Bump.

---

### Post by EthioJOB on 2011-03-03
Guys I would really appreciate if anyone could help me with this sound problem.

---

### Post by EthioJOB on 2011-04-28
Its been a while, but still, BUMP.

I really need to get the sound working on Ubuntu, otherwise all I've got is an ornamental OS installation.

---

### Post by EthioJOB on 2011-05-11
bump

---

### Post by EthioJOB on 2011-05-11
Hi,

Its been a while. OK, so the sound just stopped working in my Windows partition. I suspect that the hardware might me a little faulty, though software or failing to recognize the sound hardware seemed to be a problem for Ubuntu. My question is, will installing a sound card solve my problems, whether its hardware or software, so that it will solve once and for all the sound problems on both OSes?

---

### Post by EthioJOB on 2011-06-01
Hi

Just wanted to say that my sound problem was solved. In case there is someone who has a similar problem, try out this [link in launchpad answers]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/159105"), or ask a question there.

---

