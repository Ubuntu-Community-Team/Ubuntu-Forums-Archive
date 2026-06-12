---
title: "No sound on tuxguitar"
date: 2009-05-12
forum: Multimedia Software
---

### Post by tegnoto89 on 2009-05-12
I did a clean install of Jaunty a week or two ago, and since then I've been unable to get sound working on Tux Guitar.  I know that I had done some tweaking with midi on hardy before I made the upgrade; can somebody please help me get my sound going?

---

### Post by tegnoto89 on 2009-05-14
Does anyone have any suggestions at all?

---

### Post by DwalerXIII on 2009-05-15
I just installed Tuxguitar and I'm facing the same problem.
Anyone knows a solution please?

---

### Post by SoylentSteak on 2009-05-15
In the terminal, type: sudo apt-get install timidity

Go to system>preferences>startup applications, and add this command: timidity -iA -Os

In TuxGuitar, use the TuxGuitar sequencer, and try different timidity ports until you get one that works.

---

### Post by ellgor on 2009-05-16
Hi,

Had similar problems, found out that a new version was at the Tux site- 1.1 (updated from 1.0) fixed the sound for me.

Regards, Ellgor.

---

### Post by DwalerXIII on 2009-05-18
SoylentSteak,

with Timidity tuxguitar sounds great!

Thank you

---

### Post by SoylentSteak on 2009-05-18
Glad to be of service. 8-)

---

### Post by gothicfan on 2011-07-08
Thanks a lot! Had the same problem and after I installed Timidity worked for me too. Love ya guys! :guitar:

---

### Post by psychok7 on 2011-12-07
timidy worked for me also with my fast track pro, but i would like to know wht does it do exactly? if i leave it on start up with it affect my overall sound?

---

### Post by SoylentSteak on 2011-12-07
> **psychok7 said:**
> timidy worked for me also with my fast track pro, but i would like to know wht does it do exactly? if i leave it on start up with it affect my overall sound?

It's just a way of getting MIDI to work. It's never affected the rest of the sounds on my system, and I've been using it for years, across several releases of Ubuntu.

---

### Post by checoimg on 2012-01-10
> **SoylentSteak said:**
> It's just a way of getting MIDI to work. It's never affected the rest of the sounds on my system, and I've been using it for years, across several releases of Ubuntu.

Great I just needed this. But doesn't work on My Oneiric.

---

### Post by checoimg on 2012-01-17
Ok Now I got it working Thanks ! In soound settings Timidity port 128:0

---

### Post by btoogood on 2012-05-31
timidty worked for me on my powewrpc thanks :guitar:

---

