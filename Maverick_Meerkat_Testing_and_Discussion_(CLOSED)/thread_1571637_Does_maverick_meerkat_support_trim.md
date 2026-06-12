---
title: "Does maverick meerkat support trim?"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by josephellengar on 2010-09-09
I asked this a while ago and was told that MM will most definitely support trim, but now that the beta is out, what is the consensus? Also, if I do an upgrade directly from LL to MM and have a SSD as my main hard drive, will trim be automatically enabled, or do I have to do something to enable it?  I am thinking about doing the upgrade now on a netbook that I have gutted and added an SSD to for the sake of testing, but I wanted to be sure of this feature first.  So, what do you think?  Is trim enabled?  MM does use a post-2.6.33 kernel, correct?  Thanks!

---

### Post by BwackNinja on 2010-09-10
Yup, been in the kernel since 2.6.33, and maverick is using 2.6.35.

---

### Post by vishalrao on 2010-09-10
It looks like you still have to manually put in the "discard" mount option in /etc/fstab - though this may be possible during installation via the alternate image.

---

### Post by josephellengar on 2010-09-10
> **vishalrao said:**
> It looks like you still have to manually put in the "discard" mount option in /etc/fstab - though this may be possible during installation via the alternate image.

So when I upgrade, as long as I add "discard" to the fstab, it will work?

---

### Post by vishalrao on 2010-09-10
I believe so, yes, but I don't know how to confirm this. I have it in my fstab for my SSD :) Perhaps some SMART numbers off smartmontools?

---

### Post by josephellengar on 2010-09-12
Anybody done any tests about this?  I would but my current SSD is well-used so benefits from trim won't show up for quite a while.

---

### Post by andrewabc on 2010-09-12
Argh, so TRIM is not enabled by default when ubuntu installed to a SSD?

This is stupid. The amount of threads that are/will be created about SSD support over next 6 months will be crazy. Expecting SSD owners to edit fstab to enable TRIM since TRIM has been out since late 2009 makes ubuntu/linux look bad. win7 does it (and alignment) automatically, and I believe it did it when released October 2009.

And as asked in every SSD thread, anyone confirm proper alignment when installing to SSD?

---

### Post by a-user on 2010-09-13
i can confirm that trim works with discard as mount option. i enver tried it without.

---

### Post by MacUntu on 2010-09-13
> **andrewabc said:**
> And as asked in every SSD thread, anyone confirm proper alignment when installing to SSD?

Todays installer aligned to 2 MiB, so yes, it should work fine.

---

### Post by josephellengar on 2010-09-13
> **MacUntu said:**
> Todays installer aligned to 2 MiB, so yes, it should work fine.

Okay, here's a question.  I originally installed W7 (which does align) and then installed Karmic.  So presumably mine should be aligned correctly.  Would I get any benefit out of doing a clean install of Maverick over LL?  (Not now of course, just when the RC or stable version comes out)

---

### Post by andrewabc on 2010-09-13
> **MacUntu said:**
> Todays installer aligned to 2 MiB, so yes, it should work fine.

So it works as 512kb alignment block size?
[Partition alignment for OCZ Vertex in Linux](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

Or is that 2mib block size?

@rossholley
There are lots of benefits of a fresh install.
If you don't mind fresh install it should work better than upgrading. As to whether it will impact SSD stuff, I don't know. Apparently no matter what you do you'll have to manually add discard to fstab, and alignment would depend on if aligned before. Although I would think if you wiped the ntfs partition, you would have to tell it to start at proper block to be aligned, it should not remember that.

Sorry I'm confusing.

---

### Post by recluce on 2010-09-13
> **rossholley said:**
> Okay, here's a question.  I originally installed W7 (which does align) and then installed Karmic.  So presumably mine should be aligned correctly.  Would I get any benefit out of doing a clean install of Maverick over LL?  (Not now of course, just when the RC or stable version comes out)

That depends on whether you really want to move from Lucid to Maverick in the first place. If yes, a fresh install tends to be slightly more reliable than an upgrade. I would probably back up everything with Clonezilla (in case the upgrade goes badly), fix possible dependency issues with aptitude and try to upgrade. If the upgraded system works satisfactory, than the question becomes purely academic.

If you don't plan to upgrade to Maverick or would like to wait a little longer, you can run 2.6.35 on Lucid just as well as on Maverick. Just add the Ubuntu kernel ppa to your sources and use the package manager of your choice to install the newer kernel (don't forget to update GRUB).

---

### Post by MacUntu on 2010-09-13
> **andrewabc said:**
> So it works as 512kb alignment block size?
[Partition alignment for OCZ Vertex in Linux](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

Or is that 2mib block size?

Oops, forget the crap I posted. The first **sector** is 2048 at 512 byte/sector - so it's aligned at 2048*512/1024/1024 = 1 MiB, a multiple of 512 KiB, a multiple of 4 KiB.

---

