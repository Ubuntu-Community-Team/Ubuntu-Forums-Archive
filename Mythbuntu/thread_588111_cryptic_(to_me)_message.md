---
title: "cryptic (to me) message"
date: 2007-10-23
forum: Mythbuntu
---

### Post by meanmrmustard on 2007-10-23
Below is the tail end of dmesg.

While navigating to /etc/lirc.conf my alternate terminal suddenly produced the  line below (at the bottom)  every couple minutes.

This is a fresh install of the release candidate.
Anyone have a clue what's up?


[137737.653084] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[137737.653103] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[137737.653187] agpgart: Putting AGP V3 device at 0000:04:00.0 into 8x mode
[137785.444717] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[137907.363100] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[138029.265700] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[138151.168702] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by tgm4883 on 2007-10-23
That would be your broadcom wireless card.  In Ubuntu you have to jump though a few hoops with broadcom.  People have gotten them to work though.

---

### Post by meanmrmustard on 2007-10-23
Err...  I forgot that card was in there.
Thanks!

---

### Post by superm1 on 2007-10-23
> **tgm4883 said:**
> That would be your broadcom wireless card.  In Ubuntu you have to jump though a few hoops with broadcom.  People have gotten them to work though.
Hoops?

Doesn't restricted-manager grab the firmware for you nowadays?  Or am I just crazy in thinking that I read that somewhere?

---

### Post by tgm4883 on 2007-10-23
> **superm1 said:**
> Hoops?

Doesn't restricted-manager grab the firmware for you nowadays?  Or am I just crazy in thinking that I read that somewhere?

You know what.  I haven't tried it since feisty.  So perhaps it does.  I thought I just recently read that it didn't though, that you still had to use a firmware cutter on it.  Maybe that user was as illinformed as me :)

---

