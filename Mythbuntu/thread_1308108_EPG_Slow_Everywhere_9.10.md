---
title: "EPG Slow Everywhere 9.10"
date: 2009-10-31
forum: Mythbuntu
---

### Post by uncle hammy on 2009-10-31
I just upgrade all my machines to 9.10 with clean installs.  I am using JYA's Karmic Testing Repos, which as I understand it mirror the Mythbuntu ones.

Anyways, on ALL my machines, the program guide is so slow, it's to the point of being useless.  It takes a good 5 seconds to load, and then you can only scroll horizontally.  Vertical scroll take 5+ seconds to respond.

It is like this on all themes, tried with 180 - 190 Nvidia drivers, and from any screen.  I.E. It doesn't make a difference if you load the guide from Manage Recordings, Live TV, Live TV with playback paused, etc.  The behavior is always the same.

My current version of the frontend shows as "branches/release-0-22-fixes (22676) in the Info Center.

The only catch for me is, I don't know if this is a 9.10 thing, or introduced in 0.22's latest update.  I did not have this issue yesterday with JYA's 0.22 testing repos on 9.04.

---

### Post by uncle hammy on 2009-10-31
OK, I'm slightly embarrassed.  The guide was being slowed down due to the fact that I forgot to restore my folder with all my channel logos.  Apparently it was looking hard for them, but they weren't there anymore.

As soon as I put them back in place, it seems fine again.

---

