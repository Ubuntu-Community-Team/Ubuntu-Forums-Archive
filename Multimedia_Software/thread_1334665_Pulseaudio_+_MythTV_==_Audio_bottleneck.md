---
title: "Pulseaudio + MythTV == Audio bottleneck"
date: 2009-11-22
forum: Multimedia Software
---

### Post by hambone79 on 2009-11-22
I have an Ubuntu 9.10 desktop with dual monitors and I frequently use my 2nd monitor to display MythTV while I browse or read mail in the first monitor. This setup has work fine from Ubuntu 7.10 through 9.04, but since I upgraded to 9.10 I suddenly have an extremely annoying issues with Pulseaudio. It seems that no matter what I do, using MythTV causes all of the system/application sounds (i.e. Rhythmbox, Skype, Pidgin, Thunderbird sound notification, etc.) to be placed in some sort of queue until MythTV is closed. As soon as MythTV is closed, an awful mix of about 30 different sounds tries to play all at once.

Anyone know how to make MythTV and Pulseaudio play nice together?

---

### Post by Uncle Spellbinder on 2009-11-22
Pulse Audio seems to be really screwing things up regarding TV. You're not alone. TVTime gets no sound at all. Can't find a fix at all.

Hopefully, Lucid will have this ironed out. Sad not to be able to use something that worked on previous versions of Ununtu without issue. I had hoped that each version would be an improvement on the previous. As far as sound/tv goes, Karmic is a mess.

---

### Post by cross157 on 2009-12-07
Same issue here, so I'm bumping this thread. Please help anyone.

---

### Post by wilberfan on 2009-12-20
"Never mind..." I thought I was having the same problem.  Turns out only flash audio in firefox 3.6beta6pre stops working when mythtv frontend is running... Flash audio is fine in Firefox 3.5.6 and Chrome.  Audacity, Listen, Rhythmbox are all okay, too...  I happened to have killed pulseaudio following [this post]("http://ubuntuforums.org/showpost.php?p=8522446&postcount=14"): Have no idea if that helped, or not....]

---

