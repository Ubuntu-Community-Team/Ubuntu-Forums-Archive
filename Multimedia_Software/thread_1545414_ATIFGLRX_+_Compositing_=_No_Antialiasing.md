---
title: "ATI/FGLRX + Compositing = No Antialiasing"
date: 2010-08-03
forum: Multimedia Software
---

### Post by BinaryBulge on 2010-08-03
I'm at wit's end with this.

I just upgraded my hardware, almost completely.

What I had (let's call it system A):

- 10.4/Lucid
- Intel Core 2 Conroe 2.66 GHz
- Gigabyte P35 Motherboard
- ATI Radeon HD 5670
- WD Caviar Black 500 GB HD

With system A, I could enable antialiasing (and anisotropic filtering, etc) no problem.

What I upgraded to (let's call it system B):

- 10.4/Lucid
- AMD Phenom II X4 965 3.4 GHz
- ASRock AMD 870 Motherboard
- ATI Radeon HD 5670 (same graphics card from system A)
- 2 x WD Caviar Blacks (RAID0)

Oddly, whatever I do to enable antialiasing on the new system B, it won't work.  This is weird, considering the same graphics card pulled it off in system A.

I've tried many/most of the various aticonfig/xorg.conf settings.  I've tried 32 and 64 bit Ubuntu.  I've tried multiple versions of the Catalyst driver (from 10.4 to 10.7/current).  Nothing changes.

So what's going on here?  The main differences are obviously the CPU and the architecture.  (Well, and the fact that I'm now using dmraid/RAID0... but that probably wouldn't effect this...)

I just now tried shutting off Compiz (disabling desktop effects) and turning on compositing in Metacity directly.  That seemed to speed things up significantly (RSS screensavers fly whereas they hiccupped horribly in Compiz), and gave me window transparency, but still no Antialiasing (I enabled it all in AMDCCCLE).

My next move was to try some Kernel tweaks, but I really feel like I'm grasping at straws here.  Any suggestions?

---

### Post by BinaryBulge on 2010-08-03
Enabling "Unredirect Fullscreen Windows" in CompizConfig -> General allows for antialiasing and full rendering speed in full-screen windows.  Was this "ON" by default in Karmic?  Perhaps that was the difference between my new system and the old (for system A, I upgraded Karmic with Lucid... System B was a direct Lucid install).

So it would appear Compiz doesn't allow for antialiasing in OpenGL when compositing.  Is that correct, or is my system funky somehow?

---

### Post by cromat on 2010-10-27
Did you ever find an answer to this?  I am currntly have the same issue and it is rendering Cairo Dock with Open gl and not smoothing out the edges.

---

