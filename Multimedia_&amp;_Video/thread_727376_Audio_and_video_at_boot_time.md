---
title: "Audio and video at boot time?"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by ygolohcysp on 2008-03-17
Okay, I have two separate but kind of related issues/questions.  Before I get started, I'm trying all of this on an AMD 32 bit XP#### (forgot the number) on a dual boot with XP and Ubuntu 7.10, with an ATI Radeon 9550, a Creative Fatality Xfi, and other hardware that works fine.  I actually have the ATI working fine with compiz, and the Xfi I think as good as I'll get for now with OSS.

Issue #1
On boot up, the framebuffer driver forces the card, and my SyncMaster LCD into a resolution that the LCD doesn't like.  That makes the LCD throw up a warning on it's own letting me know that it doesn't like the resolution, and that I should really switch to 1440x900 at 60hz.  It used to do this during the splash screen at shut down too, but changing the resolution in /etc/usplash.conf fixed the shutdown problem.  I've looked at everything I would be able to figure out on my own and then some.  There's no obvious way of changing the resolution in vesafb or in the usplash modules when pulling apart the kernel's initrd image.  I've booted into recovery and used hwinfo to dump framebuffer into a logfile.  There apparently isn't any support within the framebuffer for 1440x900, though there are three text mode resolutions listed that I haven't seen on the table for the grub settings on these boards.  I'm wondering if it's possible to get the ATI driver loaded into the initrd image.   ... OH!!!  I just found the same /etc/usplash.conf inside the initrd image.  Maybe I'll have to try that and recompressing it.

Issue #2
Is it possible to get OSS support built into the initrd image just so I can pretend that my sound card is configured with a real driver by hearing the login sounds?

Admittedly, these aren't problems which prevent the computer from working.  I'm mostly having fun and learning more about Linux.  Thanks for any help.


I know ... :-({|=

---

### Post by ygolohcysp on 2008-03-17
Okay, I tried altering the /etc/usplash.conf inside the cpio archive (initrd.img-2.6.22-14-generic), and then actually figured out how to remake the cpio archive and then recompress it.  It didn't work.  The mahine still booted, but trying to force that resolution just made the splash screen not work.  On the plus side, when I compressed the archive, I actually got it smaller than the original, so that with the absence of the splash screen did effectively remove the warning from my LCD.  I just get to watch the booting procedures instead of the splash screen, which was covered by the LCD's warning anyway.  It also boots faster.

I'd still like to get better driver support during the initial boot off the ramdisk though.

---

