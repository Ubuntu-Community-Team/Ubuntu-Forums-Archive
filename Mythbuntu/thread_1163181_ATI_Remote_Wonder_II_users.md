---
title: "ATI Remote Wonder II users?"
date: 2009-05-18
forum: Mythbuntu
---

### Post by tji on 2009-05-18
I have an ATI Remote Wonder II  RF based remote control hooked to my dual-boot Mac Mini (nvidia based).   It is recognized by default with Mythbuntu 9.04, and the mouse pad + arrow keys work.  But, I have not been able to configure the other keys to do what I want.   Basically, I'm trying to:

- Set keys to input values used by MythTV (at least for one of the modes of the remote)

- Make the big "remote wonder" button start mythfrontend

- Override the 'clock' key.   By default this locks the screen, I want to map it to 'escape'.

So, I'm wondering if there are others here that already solved this.   I'll post any updates as I have a chance to play with this.

---

### Post by phroman on 2009-05-18
I believe the file  ~/.mythtv/lircrc is used to map the buttons on the remote to their specific functions in Myth TV.  So, if the remotes works at all, that's a good start, look at that file and maybe you can make the adjustments manually.

---

