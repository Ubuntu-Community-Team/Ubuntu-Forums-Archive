---
title: "Softphones work one-way only: can't hear particular recipient"
date: 2009-01-12
forum: Multimedia Software
---

### Post by kriukov on 2009-01-12
I have been experiencing this in the past days. I use Gizmo to voice-talk to people. With one of the recipients (my mother), I have a problem: she can hear me perfectly and I cannot hear her. I tested Gizmo with other people and everything is fine; I tried restoring the partition backup or defaulting all settings -- no result. We also tried Ekiga and the situation was the same: only she could hear me. So, the problem is most likely on her side. She is not very computer-literate so I have to instruct her on this one-way connection and she replies via text. We tried changing the ALSA settings in gstreamer-properties and in Gizmo properties (on her PC); I checked all the volume properties and made sure everything is turned up 100% (on my PC). She tried two headsets with microphones. What could be the best thing to check here?

---

### Post by kriukov on 2009-01-12
Any advice? We are still upset we can't talk.

---

### Post by nator84 on 2009-02-12
mm i'm having the same trouble, with another softphone though.

---

### Post by kriukov on 2010-03-30
This is extremely frustrating. It's been more than a year and the problem still persists: I cannot talk free to my relatives abroad. However, I have managed to gather some interesting data about it.

 - It does not matter which softphone to use. I tried Gizmo, Ekiga, Skype, and QuteCom (WengoPhone). In any case, I am heard perfectly and I cannot hear the recipient.

 - It does not matter which OS to use. On my computer I tried Ubuntu 8.04 (my main system), Windows XP in VirtualBox on Ubuntu 8.04, and Ubuntu 10.04 beta 1 (real, not virtual). My Mom's computer has Ubuntu 8.04, but she tried once with another one with Windows XP. In any case, the situation is the same.

 - However, the location or proximity matters. When I was at home in my country, I could speak to my Mom without problems from my laptop to her desktop on Gizmo. However, when I try to do the same (same OS, same computers) when I come back to the US with my laptop, the problem reappears.

 - Also, I can use my softphones (mainly Gizmo) to speak from my computer to cell phones. It always works.

Thus, I am very confused. The only thought that comes to my mind is that there is some IP blocking policy between international clients so that they wouldn't be able to talk free. Can anybody relate to this?

---

