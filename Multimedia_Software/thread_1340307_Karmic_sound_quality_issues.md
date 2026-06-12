---
title: "Karmic sound quality issues"
date: 2009-11-28
forum: Multimedia Software
---

### Post by plafuro on 2009-11-28
Hello!!

I've been looking for a while for information in different forums but i coulndn't find anything like the issue i'm experiencing.

I've been using a AC97 soundcard for a long while in different versions of Ubuntu. Since I installed Karmic I have had very annoying sound issues: All playback sounds like a very highly compressed audio, like a very high-pitched tone replacing the frequence that should be there... i'm sorry but i cannot explain this any better, but it is a very annoying issue.

I have noticed that this problem is "fixed" when, under the sound preferences applet i change to 4.1 oudio output instead of 5.1 (again, i've used 5.1 audio for a long while without any issues), or funny enough, when i turn sound to exactly 53% (-16.58db). We are talking about an out of the box set up here.


Any ideas what could this be?

Thank you very much in advance!!

---

### Post by plafuro on 2009-12-01
bump

---

### Post by plafuro on 2009-12-01
Ok, for the record, i found out that actually the coincidence that the sound is clean when it is turner do 53% is that, for some reason, when changing the volume through the sound applet in th google pannel, the PCM channel changes from 100% to 97% (checked this running alsamixer when changing the volume), so actually the noise is generated because the PCM channel is most of the time at or very close to 100%.

I found [a bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/485530") about a similar problem and Daniel T Chen replied right away with a workaround.

---

