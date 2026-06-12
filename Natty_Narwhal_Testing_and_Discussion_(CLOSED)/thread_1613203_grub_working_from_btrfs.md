---
title: "grub working from btrfs ?"
date: 2010-11-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bladerunner6 on 2010-11-04
has anyone got grub working from a btrfs drive yet in natty
i c support has come into gparted 0.70

---

### Post by kahping on 2010-11-04
Not so fast, I think. If it has I'm sure there'd be big news by now

---

### Post by gnomeuser on 2010-11-04
There is a patch but since it is derived from the kernel's GPLv2 source it cannot be applied to GRUB2's GPLv3+ codebase.

Isn't it good that the FSF are protecting us from such evil freedom hating applications of code?

---

### Post by nerdopolis on 2010-11-04
They can't put gpl 2 code into gpl 3 code? Am I misinterpreting something here? Please correct me if I am

> This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, **or (at your option) any later version**.

( I added the bold)

---

### Post by seeker5528 on 2010-11-04
> **nerdopolis said:**
> They can't put gpl 2 code into gpl 3 code?

If it's GPL code with the 'or later' clause it could be.
Kernel stuff is GPL 2 only.

Later, Seeker

---

### Post by bladerunner6 on 2010-11-06
an update, i am using btrfs, finding it slow writing small files compared to ext4 at the moment

---

### Post by dext on 2010-11-06
only way you can really use **BTRFS** is if you use grub-legacy. this is probably why Fedora wont go over to Grub2 not by default anyway

---

### Post by whoop on 2010-11-06
I find this a bit odd, legacy grub was way too old to be maintainable, the code is not manageable any more we need a newer version so we can expand functionality (==grub2)...

All I get is that people find grub 2 harder to use and it has less functionality (aka no btrfs support etc..).

The reason I heard that btrfs was not supported is that btrfs is still subject to change (although grub legacy doesn't seem to mind).

I don't really care; an ext2 boot solves all the woes...

---

### Post by dext on 2010-11-06
> **whoop said:**
> I find this a bit odd, legacy grub was way too old to be maintainable, the code is not manageable any more we need a newer version so we can expand functionality (==grub2)...

All I get is that people find grub 2 harder to use and it has less functionality (aka no btrfs support etc..).

The reason I heard that btrfs was not supported is that btrfs is still subject to change (although grub legacy doesn't seem to mind).

I don't really care; an ext2 boot solves all the woes...

Grub2 is still Experemental so the functionality will not be there till its finished. reason why BTRFS cannot be used in Grub2 is because of the License between the 2. Grub2 = GPLv3 . BTRFS= GPLv2 . i cant see Linus Torvolds budging being ignorant as he is.

---

### Post by whoop on 2010-11-06
> **dext said:**
> Grub2 is still Experemental so the functionality will not be there till its finished. reason why BTRFS cannot be used in Grub2 is because of the License between the 2. Grub2 = GPLv3 . BTRFS= GPLv2 . i cant see Linus Torvolds budging being ignorant as he is.

I heard it was a waste of time because btrfs was subject to change, nothing else, but that was about a year ago, so maybe things changed...

---

### Post by dext on 2010-11-06
with Grub2 1.99 expected to be out before Christmas i think, im not sure if the Licensing issue has been resolved

---

