---
title: "Sound card not playing in stereo"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by dgray_from_dc on 2006-10-10
IBM Netvista 6790
with an Intel 82801BA-ICH2 sound board (or at least that's what KMix says)


I've been using Kubuntu for nearly a year now.  I started with Breezy and upgraded to Dapper pretty much as soon as I found out about it.  Anyway, I don't know if this problem has been here all along or not but my sound sound card is only using one channel for audio output.  I recently played an MP3 and noticed that I could only hear one channel.  I looked in KMix, configured to see both channels and played with the mixer and discovered that both channels were coming through both speakers and the right channel is very low in amplitude.  I have to steer the sound all the way to the right and rail the volume to hear it at all.  This machine is dual boot, I use XP for gaming  and have no problems on that side.  I don't know where to start, could it be a driver issue, application issue, or something else?

---

### Post by Jason711 on 2006-10-11
run alsamixer from the command line...  i have that problem with my revolution 5.1.  i just turn up the volume on both channels and use the physical speaker volume.

---

### Post by dgray_from_dc on 2006-10-12
I don't think I was clear.  The left channel comes through both speakers **and** the right channel comes through both speakers.  But, the right channel is super low.  I want to separate them and fix the amplitude on the right channel.

Update:

Upgraded to Edgy, the problem is still there.

---

