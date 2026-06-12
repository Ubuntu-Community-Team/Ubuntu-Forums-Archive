---
title: "Rhythmbox hates me"
date: 2008-05-19
forum: Multimedia Software
---

### Post by scottie_000 on 2008-05-19
Rhythmbox keeps closing on me, without warning!

I get this in the log:
rhythmbox[13969]: segfault at 280 rip 7fd873f1ee45 rsp 423f4770 error 4
and it only seems to happen when openoffice is open

please help :(

---

### Post by prule on 2009-02-07
I have a similar problem - RhythmBox closes after starting. I'm using it for downloading podcasts.

I see this in /var/logs/messages:

Feb  8 08:44:05 dell1525 kernel: [19947.956411] rhythmbox[26702]: segfault at 6964656d ip b70005c8 sp b3362260 error 4 in libgobject-2.0.so.0.1800.2[b6fd7000+3c000]

(using ubuntu 8.10, RhythmBox 0.11.6)

---

