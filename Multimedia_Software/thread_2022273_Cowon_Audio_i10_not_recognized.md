---
title: "Cowon Audio i10 not recognized"
date: 2012-07-10
forum: Multimedia Software
---

### Post by Kiljaeden on 2012-07-10
Hi everyone,

I've just bought a Cowon Audio i10, and I have a problem : it's not recognized under Linux (whether Ubuntu 12.04 nor Fedora 17), even if it is supposed to work with Linux.
The battery is charging, but nothing more. The Cowon doesn't ask me to "Charge+Sync" or "Charge+Play" as it is supposed to on Windows.
The only info i have is that i should have "Sfile transfer" enabled, but i don't know what it is.

I hope you could help me.

---

### Post by Vakman on 2012-07-21
Does anything happen at all when you plug it in other then the battery charging? As in does Ubuntu try to mount anything? 
Can you see any additional drive in GParted?

---

### Post by awatekiran on 2012-10-08
> **Kiljaeden said:**
> Hi everyone,

I've just bought a Cowon Audio i10, and I have a problem : it's not recognized under Linux (whether Ubuntu 12.04 nor Fedora 17), even if it is supposed to work with Linux.
The battery is charging, but nothing more. The Cowon doesn't ask me to "Charge+Sync" or "Charge+Play" as it is supposed to on Windows.
The only info i have is that i should have "Sfile transfer" enabled, but i don't know what it is.

I hope you could help me.

Try these steps :-
-----
Settings >> System >> USB mode
-----
Default is MSC. Change it MTP and try connecting Cowon iAudio 10.

These steps worked for fedora 17. Hope it works for Ubuntu also.

---

