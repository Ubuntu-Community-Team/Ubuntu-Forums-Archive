---
title: "Can't record sound with any program"
date: 2008-05-19
forum: Multimedia Software
---

### Post by arno1991 on 2008-05-19
hi
i have a problem with my computer. I can't record sound. When I plug in my microphone, I can hear myself trough my speakers, but I can't record it. When I go to my Volume Control, I have 5 or 6 different soundcards, while, in real life, I only have one in my computer. In Volume Control everything is turned on. The strange thing is, I can choose in audacity between two different OSS cards, two ALSA cards and two or three HDA INTEL cards. I don't know why.
Please help me! I'm in a band and i really need some recordings...

thanks,

Arno De Pachter

---

### Post by VanillaMozilla on 2008-05-19
Those aren't sound cards.  Those are drivers or logical devices or something.  I think the task is to figure out which one is the right one.  It might be easiest just to try each of them.  Or you may even have to install a logical device or something.

I'm replying because I have exactly the same problem, but I haven't had time to figure it out either.

---

### Post by arno1991 on 2008-05-19
that is one part of the problem too... I don't know which device, and I tried to record with all the drivers that are possible on my computer but still... No recorded sound...
thanks anyway :)

arno

---

### Post by arno1991 on 2008-05-19
anybody help please?

---

### Post by VanillaMozilla on 2008-05-20
The Windows Audacity has a little source switch that I don't see on the Linux version.

Here are some places to look:
System > Preferences > Sound (there's a list of devices, which may be irrelevant)
Audacity > Help > Audio Device information
Audacity > Edit > Preferences > Audio I/O

Also consider using the Sound Record program.

Sorry, I have no more information on this.  Still no time to research it for now, but I still need to find the answer.  Try Google.  Search for ALSA and OSS, and anything else you can think of.  Sorry, that's pathetic, but it's the best I can do for now.

---

