---
title: "Out of Range????"
date: 2008-12-02
forum: Multimedia Software
---

### Post by Jim Lewis on 2008-12-02
I tried to reset my Nvidia accellerated graphics drive (version 173) to a lower resolution setting  and got a black screen with a rectangular box that drifts diagonally across the screen saying something like Setting out of Range.

I can't back out of it.  ESC doesn't do anything.  Control Alt Delete doesn't.  I'm using the live session off the disk for 8.10 to post this question.  Hopefully, there's something that can get me back to where I was so I can chnge the range back?????

---

### Post by realgt on 2008-12-02
you'll want to reset your xorg.conf

boot into a command prompt and run this command:

**sudo dpkg-reconfigure xserver-xorg**

that should reset your xorg.conf file, then reboot.

---

### Post by Jim Lewis on 2008-12-03
Thanks.  I did that.  Didn't work.  

Blindly, not knowing what would happen (dangerous, I know), I also went into recovery mode and tried to fix X server that way.  Got back to the basic 800 x 600 resolution that I've been trying to fix for days now.

That's where I am now.  

System - Hardware Drivers gives me 2 choices.  NVIDIA Accelerated Graphics Drivers 173 and 177 (recommended).  Both give me flickering screens whenever a command is executed, and too-limited a number of optional refresh rates to fix it.  version 177 is much worse.

It was while I was searching for a lower resolution in version 173 that I got this "out of range" problem.

I've scoured these forums, read the Binary Driver How-To NVIDIA file, and am at a loss.

---

### Post by Jim Lewis on 2008-12-03
No further suggestions?

---

