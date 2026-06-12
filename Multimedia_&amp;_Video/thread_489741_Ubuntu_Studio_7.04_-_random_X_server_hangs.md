---
title: "Ubuntu Studio 7.04 - random X server hangs"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by morgan_greywolf on 2007-07-01
I keep getting random X server hangs on Ubuntu Studio, but only when using the low latency or realtime kernels. Here's my system:

MSI KT600-based motherboard
AMD Athlon 1800+ XP
nVidia GeForce 5700 8X AGP video card
1 GB DDR 266 DRAM
300 GB SATA HDD

This happens whether I use the nvidia, nvidia_new, or the unaccelerated 'nv' driver  If I use the generic kernel, the problem doesn't occur, near as I can tell.  It looks at first glance like the old 'Athlon/AGP bug', but adding 'mem=nopentium' to the kernel parameters in grub.conf doesn't seem to prevent the crashes.  I've also tried 'mem=nopentium pci=noacpi noapic', which didn't help either.  No problems with any driver using the generic kernel.

I'm not using Beryl or Compiz.

Can anyone please help?  I'm about at the end of my rope here.
:(

---

### Post by morgan_greywolf on 2007-07-03
Bump.  C'mon, someone has to have seen this ...

---

### Post by morgan_greywolf on 2007-07-06
Bump.  Am I the only person to experience random X server hangs with the realtime kernel?

---

### Post by PositiveK on 2007-12-09
I use Gutsy and have experienced some random hangs of the system.  I am not sure it's X or something else.  In any case, at times I have not figured out how to reproduce, all the windows, desktop, etc. freezes and cannot be interacted with.  The mouse cursor, however, is still able to *move*, but I cannot click on anything.  The system monitor on my Gnome panel at the does NOT freeze, however.  I notice, though, that ever so often my CDROM drive LED (on my laptop) blinks.  This is the LED on the system board (there is none on the drive itself).  I am not sure what that means or why it's blinking.  It blinks briefly every ~2seconds.  I cannot switch desktops either.

Hangs occur approximately 1-per-40hours.??

My only recourse at that point is to press <Ctrl>+<Alt>+<Backspace> to restart the X server.  So, something's still responsive, obviously.

Linux mymachinename 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
Gnome + Compiz
Ubuntu Gutsy Gibbon w/ std. software updates.

---

### Post by morgan_greywolf on 2008-01-16
Ok, last bump. And partial solution:

I tracked the problem I was having with the standard and low-latency kernels to a problem with the VIA KT600 chipset.    Everyone who's had problems with the NVIDIA or ATI drivers who are running boards based on the VIA  KT600 chipset might want to know this factoid:

The VIA KT600 chipset does **not** implement 8X AGP properly.  It's broken.  Many, many 8X video cards will not work right with that chipset.  I found this out by hunting through in the NVIDIA forums for a few days.

This was very difficult to find out, because it took much searching. I found it buried in some post where I found out a Windows users was having the same problems.  Argh.

Now that I've helped out a *few hundred people* on this forum, can someone please, please at least try to help me?  I still have random lockups and freezes with the realtime kernel while running the NVIDIA drivers.  My symptoms are exactly what the last poster above describes.

So I've since upgraded to a VIA K8M800 chipset board (yes, I'm a glutton for punishment from VIA, I guess) And my new setup is:

Athon 64 x2 3800
1 GB DDR2 RAM -- dual channel (2x 512MB DIMMs of the same density)
300 GB Seagate SATA 150 HDD
VIA K8M800 Chipset
same NVIDIA 5700 8X AGP card.

Just to clarify -- the freezes ONLY occur on the realtime kernel and NOT on the low-latency or standard kernels now.  (Been running for 2 months without a hitch)

---

### Post by paulexander on 2008-02-22
You are not alone, but I see the discussions appear to be in other locations in the forum.

I have an older rebuilt Toshiba Tecra 9000, with ATI video - this confounded thing won't even boot the RT kernel; it just hangs at the same spot.

No one seems to be terribly interested in figuring out a workaround or fix. Others mention that they have the same problems, but appear to be resigned to not using the RT kernels

---

