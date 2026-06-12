---
title: "Lost xserver after failed video card upgrade attempt"
date: 2009-12-21
forum: Multimedia Software
---

### Post by dsmithhfx on 2009-12-21
9.04 and 9.10 X86_64 (both) on same, multiboot pc:

I attempted to replace my Radeon 9550 with an HD 4650 (AGP).

Although the new card worked in vga mode in both win and lin, I could not install drivers for it in XP Pro, and xserver failed to load in Jaunty & Karmic (even from live CDs), opensuse, and Mandriva 2010. 

I read there are windows driver issues with the card (I tried 'hotfix'. catalyst drivers, which didn't work either), but didn't expect anything like this.

So I pulled the new card and restored the old (9550), which had been working fine in all Linux distros previously.

Now however only 1 distro will start the xserver: debian-based sidux.

As with the 4650, both the Ubuntu 9.04 and 9.10 hd-installs and live cd's either can not load the xserver anymore and boot into a cli, OR boot into a black screen with the pc only responsive to alt-prt scrn-s-u-b (to reboot), even though they were both working fine from this card before I tried the upgrade. 

I messed around a little with 9.04's minimal xorg.conf, trying to force it to load the free radeon driver, but no joy.

I'm really perplexed why even the live cds, which never had any previous issues with the 9550, are now failing to boot into a graphical display, with no other intervention than having swapped in the new card, failed boot, then replacing the old.

I should add I got the drivers for the old card reinstalled and working in xp, so it apparently isn't a hardware issue.

Thanks for any help or insights out of this mess!

---

### Post by Yellow Pasque on 2009-12-21
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by dsmithhfx on 2009-12-22
I did not have fglrx drivers installed.

---

