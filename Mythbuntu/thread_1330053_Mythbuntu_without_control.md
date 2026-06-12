---
title: "Mythbuntu without control"
date: 2009-11-18
forum: Mythbuntu
---

### Post by IceCap on 2009-11-18
I have a ~1 year old Mythbuntu setup (8.04) which has worked pretty well (PVR-350 based).  But gradually I have been "loosing control" over it and gotten to the point I cannot access it.

  First, I had the issue of the front-end starting even with a ACPI wake-up (known issue) and I followed the directions found on these forums (can't remember where) where you disable the desktop.  Not a huge problem by itself since I didn't use it.  Except, the keyboard didn't work anymore (CapsLock and NumLock lights work fine but X doesn't seem to be getting any signals, tried both USB and serial keyboards neither work).
  Well, this wasn't a huge problem because I preferred to ssh (ssh -X) into the Mythbox from my Linux laptop or my Mac mini and do any maintenance through that.
  Then I upgraded my wireless network from a Trendnet Wireless G to an Apple Airport Extreme (the Trendnet was having issues, couldn't log into it (Linux or Mac) after a while, had to restart).
  Then I connected the Mythbox to the Airport with an ethernet cable, and on my Mac (through ssh -X) opened up wicd (Network Manager could never connect to the Trendnet router) and had it connect to the Airport wireless.  That would always freeze wicd (see where this is going?).  So, I just had wicd connect to the Airport automatically, disconnected the ethernet cable and rebooted hoping it would work.  No, it didn't, and the wired ethernet connection doesn't work either (MythTv works fine).  Looks like wicd is hanging in the beginning.  So now I'm without network connection AND I can't repair it.

  So I'm stuck.  I can't remember what the grub screen looks like, but can't I somehow have it boot into a "terminal" because I believe I can edit out the "Autojoin Network" selection for wicd using vi on the config text file (but I'm not sure then the keyboard will work).
  What I really need is to backup my recordings and the database so that I can upgrade to 9.10 (with some hardware improvements).   If I hook the drive up to my Mac can I do the database dump from it (there is this specific MySQL command to do that that I've seen around here).

  Thanks

  IC

---

