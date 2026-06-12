---
title: "Sudden buzzing noise from speakers"
date: 2008-11-30
forum: Multimedia Software
---

### Post by linuxmart on 2008-11-30
I have been using Ubuntu for about 2 years, and am mostly happy with it.
I had been using Ubuntu 8.04 since it's release. After 5 months of use, all of the sudden one day when I was going to play an MP3, a annoying load buzzing noise started coming out of the speaker. I have a base with 2 speakers system. Since 8.10 was coming out soon, I didn't bother fixing. After installing 8.10, the problem was gone for a month, until yesterday. I had the firefox open, but wasn't doing anything and all of the sudden, that same buzzing noise was back. I rebooted, and the speakers were quiet until the mouse pointer appeared on the light brown background, before the desktop was loaded. Same thing happens after every reboot.
  It's a constant buzz. When system sounds (or mp3s) are played, they sound like an empty FM station (hissing noise) mixed with the system sound that's played. After the system sound or song stops playing, the hissing noise goes away, but the buzzing noise keeps going. If I plug the speakers into the front headphone jack, it works fine, the buzzing only is in the rear sound port. In Windows XP the rear sound port works fine, so I know it's not the sound card or the speakers.
  Again, it worked fine for a month, then it started.

This is my lspci result:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Can someone please help me?

Thanks.

---

### Post by linuxmart on 2008-12-01
I forgot to add, that there is a crackling noise on top of the buzzing sound when I move the mouse or resize a window.

---

### Post by zebulon M on 2009-03-28
Late reply, but i'll answer if anyone searches and finds this...

I solved this exact problem on my computer by opening the volume control and turning everything off that wasn't necessary. The microphone was the culprit in on my computer.

---

### Post by linuxmart on 2009-03-28
> **zebulon M said:**
> Late reply, but i'll answer if anyone searches and finds this...

I solved this exact problem on my computer by opening the volume control and turning everything off that wasn't necessary. The microphone was the culprit in on my computer.

Thanks for you response. I reinstalled Ubuntu 8.10 shortly after, and haven't had the problem since. I don't have a microphone plugged in right now. Maybe I had at the time of the problem. I can't remember right now.

Thanks again. I will keep this in mind if I have the problem again in the future.

Linuxmart

---

### Post by no_one_of_consequence on 2010-09-15
Wanted to chime in here with my experience too, as I've had the same thing happen to me while running Ubuntu 10.04.

I use a USB headset (speakers/mic) and would get the buzz/crackling noise after about an hour or so of use. I ended up having to disable my internal speakers by setting it's profile to Off. After that, the USB headset is working fine (so far anyways).

---

