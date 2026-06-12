---
title: "Lvm"
date: 2010-11-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by psusi on 2010-11-09
I wrote a Wiki entry on LVM.  If you like to test development releases, you probably will find it very useful.  If you already are familiar with LVM, check it out and offer any criticism you have here.

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by psusi on 2010-11-10
Seriously?  Nobody has anything to say?

---

### Post by dino99 on 2010-11-10
hey, im the first :)

good job, clearly explained.
Some questions and requests:
- what about installing a LVM over an existing installation built classicaly without erasing data ?
- what about mixing LVM and classic installation or raid ?
- what about grub2 and uuid ?

---

### Post by psusi on 2010-11-11
> **dino99 said:**
> 
- what about installing a LVM over an existing installation built classicaly without erasing data ?

Nope, you can't upgrade an existing volume to LVM.  If you have enough unpartitioned space, you can set up LVM, then copy all of the files over, delete the original partition, and expand the volume group I suppose.

> **dino99 said:**
> 
- what about mixing LVM and classic installation or raid ?


They mix just fine.  At one point I was using a partition on my dual 36 gig 10k raptor fakeraid raid0 as an LVM PV.  The other held Windows.

> **dino99 said:**
> 
- what about grub2 and uuid ?

Works just fine, though I think I have mine set not to use the uuid since it isn't really needed since the lvm device names are stable.

---

### Post by keypox on 2010-11-14
good read, I will use LVMs on next install 11.04

---

