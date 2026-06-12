---
title: "Existing Backend migration to MythBuntu"
date: 2008-03-19
forum: Mythbuntu
---

### Post by davilla on 2008-03-19
I have an existing Ubuntu backend that I'm considering migrating to a MythBuntu 7.10 install. I hosed it a few days ago doing AppleTV development and testing games, opps. I need to update it anyway so I'm not too concerned.

The database was backed before the incident so it should be pretty easy to bring backup. The backend was also a more recent svn but behind the 0.21 fixes release.

The question concerns video capture devices. I run two PVR-150 with IR blasters to two Dish301 receivers. Getting the PVR-150 IR blasters working can be a pain, how well does MythBuntu handle them?

I also run my own channel changer script (command-line app really) because it's real fast compared to the other scripes that I have found. So I'll want to run my own lirc config and channel changer script, easy, possible, hard?

And I run custom udev rules so the two PCV-150s are always correctly identified by slot and not probe order.

Comments please.

Thanks
Scott

---

### Post by davilla on 2008-03-20
Well, that was not too bad. 

0.21 fixes is terrible for 1080i xvmc on the AppleTV compared to svn a few months ago. Now I get to figure out what was done to make it so bad.

---

