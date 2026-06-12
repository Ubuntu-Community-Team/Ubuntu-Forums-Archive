---
title: "strange sound gliches"
date: 2010-10-09
forum: Multimedia Software
---

### Post by catlover2 on 2010-10-09
hi, 

i have this odd problem, 

when i play *any* audio in ubuntu (youtube, rhythmbox, ect)
there is this skipping sound and then the audio pauses for a split second.

this happens every 5-20 seconds.

i have a: Intel 82801DB-ICH4 sound card

thanks, catlover:)

---

### Post by catlover2 on 2010-10-10
update: it happens in a livecd too.

---

### Post by reidi on 2010-10-10
I have what appears to be the same sound card and the same problem.  If I run Rhythmbox and System Monitor simultaneously while streaming audio or playing local MP3s, I can see that every 10 seconds I get the pause ("hiccup") in the audio.  CPU useage goes from ~42% to ~64% at that same point.

The stuttering is worse with streaming radio than when streaming MP3s across my home network or playing MP3s located on the laptop.

If you find a solution please post - I will do the same!

---

### Post by catlover2 on 2010-10-10
ok, IF that is, i get a solution.

---

### Post by msm120 on 2010-10-11
I have the same issue with Meerkat 10.10:

lspci
```
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```

---

### Post by catlover2 on 2010-10-11
ah, yes

lspci```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```

---

### Post by reidi on 2010-10-11
You might want to go to this Launchpad bug and add your input:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/658747?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/658747?comments=all)

[ICH4 - Intel 82801DB-ICH4] Playback problem 
Ubuntu “alsa-driver” package Bugs Bug #658747

Let's try and elevate this so the developers take note.

---

### Post by msm120 on 2010-10-12
@Reidi: Thanks for the advice; just added mine to your report.

---

