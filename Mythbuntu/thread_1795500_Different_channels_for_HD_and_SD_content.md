---
title: "Different channels for HD and SD content?"
date: 2011-07-02
forum: Mythbuntu
---

### Post by movieman on 2011-07-02
Since we got OTA HD here I've noticed that the HD shows on the HD channel show up in the listings with an 'HD' flag and presume that the shows which don't are upconverted SD. Is there any way to tell MythTV to automatically choose the HD channel for the shows that are flagged as HD and the SD channel for shows that aren't?

I'm running 0.23 on Ubuntu 10.04 at the moment but could upgrade if it's available in a newer release.

---

### Post by movieman on 2011-07-02
Ah, Ok, figured it out. I set the priority of the HD channel to one less than the priority of the SD channel and then set the HD flag to increase priority by two. Now it's switching between them correctly.

---

