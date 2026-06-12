---
title: "How to Watch LiveTV in Myth with HD 5500"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by underfunded on 2007-07-05
Hello All,

I've spent the last 2 days trying to get my Myth box up and running, but so far, I've been unsuccessful.  At the moment, I'm having trouble getting Myth to recognize my HD 5500 card as tuner 1.  My goal is to watch live tv using the HD 5500, and record using PVR 150.  Right now it sees Myth only sees the HD 5500it as DVB:0 and not tuner 1.  I know all there drivers are correct and I know that I set up the cx88 module in /etc/modules.   I keep trying to play around in Myth, but I'm totally out of ideas.  Any help would be greatly appreciated.

UF

---

### Post by NT4usB on 2007-07-05
I don't know how far you are into setting up mythtv-backend but that's where you would define the tuners, etc.
Doesn't matter which tuner (number) you choose to watch live TV with. I have tuner 1, tuner2, and tuner 18 on my system. (15 failed attempts to set up the A180 *g*.) Live TV (which I never watch, btw) would be on whichever tuner happened to be selected for the last recorded program or live show. It doesn't default back to tuner 1 every time I start live TV.
You can set the 150 to a higher priority so the first recording will always be on it.
When you're not recording anything, can you toggle between tuners while watching live TV ('y' on the keyboard)?

---

### Post by underfunded on 2007-07-05
Thanks NT4,

I'm going to start from the beginners and see if I can get things working.

---

### Post by underfunded on 2007-07-06
Would anyone know how to configure Myth to work with my cable box?

---

