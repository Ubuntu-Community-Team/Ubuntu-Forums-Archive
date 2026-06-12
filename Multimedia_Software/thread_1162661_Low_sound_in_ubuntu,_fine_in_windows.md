---
title: "Low sound in ubuntu, fine in windows"
date: 2009-05-17
forum: Multimedia Software
---

### Post by lufo4 on 2009-05-17
hello, i recently installed ubuntu on a friends computer, as per his instructions i reformatted the drive, erasing windows, according to him, the sound was good in windows, however, the sound is really low, when the speakers are at full and so is the system volume, nothing can be heard from programs like firefox. ive gone into the sound settings and the tests produce great sound,

---

### Post by Just_SomeGuy on 2009-05-17
> **lufo4 said:**
> hello, i recently installed ubuntu on a friends computer, as per his instructions i reformatted the drive, erasing windows, according to him, the sound was good in windows, however, the sound is really low, when the speakers are at full and so is the system volume, nothing can be heard from programs like firefox. ive gone into the sound settings and the tests produce great sound,

I had the same problem.
Not sure if this will work for you but...
On my system for some reason the volume control for "front" wasn't tracking the correct value.
In the gui it was all the way up.
When I launched alsamixer it was only ~75%

Open a terminal, run:
alsamixer

Check that they are truly cranked all the way up.

---

### Post by Xsecror on 2009-05-17
I also have that exact problem and haven't found any solution to it. What I do now is using Windows when I need to watch a movie or listen to some music file. It's really annoying having to switch between OS, but what else can I do?

I'm gonna try buying a new sound card or maybe reinstalling Ubuntu.

---

### Post by VastOne on 2009-05-18
> **Just_SomeGuy said:**
> I had the same problem.
Not sure if this will work for you but...
On my system for some reason the volume control for "front" wasn't tracking the correct value.
In the gui it was all the way up.
When I launched alsamixer it was only ~75%

Open a terminal, run:
alsamixer

Check that they are truly cranked all the way up.

Thank you for this...I have been looking for a solution to my low sounds for quite some time and you have provided it. 

Appreciate it...

---

### Post by lufo4 on 2009-05-21
Thank you, Some Guy, that really helped my friend has been waiting ages to be able to watch Hulu.

---

