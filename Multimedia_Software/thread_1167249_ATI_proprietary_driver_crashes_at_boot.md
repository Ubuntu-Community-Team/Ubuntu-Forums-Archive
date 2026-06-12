---
title: "ATI proprietary driver crashes at boot"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Tomatosoup on 2009-05-22
Hello,

I've installed Ubuntu 9.04 (64-bit) on my external hard drive.

The default (open-source) video driver works but has a slow frame rate.

Tried the restricted ATI driver, but then the system crashes when X is started, leaving my screen with a bit of garbled graphics.

Also tried downloading the latest ATI Catalyst driver from the ATI site. But it still crashes.

Because of the slow frame rate I can't watch videos decently. It plays choppy.

I have an ATI 3870 X2 video card.

Anyone know of a solution?

Thanks in advance!

---

### Post by Tomatosoup on 2009-05-23
I've read that it might crash because of a wrong MTRR table...
See this topic:
[http://ubuntuforums.org/showthread.php?t=815521](http://ubuntuforums.org/showthread.php?t=815521)

This is my MTRR table:
reg00: base=0x000000000 (    0MB), size=65536MB, count=1: write-back
reg01: base=0x0bff00000 ( 3071MB), size=    1MB, count=1: uncachable
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable

Does seem like kind of an odd table...

But I don't know what it should be like.

I've used the utility mtrr-uncover, which automatically tries to determine a correct MTRR table. Then I do not crash when starting X, but it does fail.

The MTRR utility returns this:
Initial MTRR configuration:
 0  0x000000000-0xfffffffff write-back
         1  0x0bff00000-0x0bfffffff uncachable
         2  0x0c0000000-0x0ffffffff uncachable

Final MTRR configuration:
 0' 0x000000000-0x07fffffff write-back
54' 0x080000000-0x0bfffffff write-back
         1  0x0bff00000-0x0bfffffff uncachable
53  0x100000000-0x1ffffffff write-back
52  0x200000000-0x3ffffffff write-back
51  0x400000000-0x7ffffffff write-back
50  0x800000000-0xfffffffff write-back

Commands for /proc/mtrr to make these changes:
disable=0
disable=2
base=0x000000000 size=0x080000000 type=write-back
base=0x080000000 size=0x040000000 type=write-back
base=0x100000000 size=0x100000000 type=write-back
base=0x200000000 size=0x200000000 type=write-back
base=0x400000000 size=0x400000000 type=write-back
base=0x800000000 size=0x800000000 type=write-back


I've also read that changing to 32-bit Ubuntu might help...
But then of course I cannot access all of my 4 GB of RAM.

---

### Post by Tomatosoup on 2009-05-23
Damn. Changing to 32-bit Ubuntu 9.04 doesn't work either.
I've got the same MTRR table.

---

### Post by Tomatosoup on 2009-05-24
Hm, it doesn't give me any error when I do:
dmesg | grep mtrr

---

### Post by Entity` on 2009-05-24
> **Entity` said:**
> I used mtrr uncover, but I don't know how to fix my mtrr table.

```

0 0x000000000-0x07ffffff write-back
1 0x080000000-0x0bffffff write-back
2 0x0c0000000-0x0cffffff write-back
       3 0x0cff00000-0x0cfffffff uncachable
4 0x100000000-0x11ffffff write-back
5 0x120000000-0x12ffffff write-back

```

Where do I go from here?

Thats what I posted in the linked thread.  I don't know where to go cause im not very good at linux commands.  Be aware that I am using the 32bit version of ubuntu.

PC config:
Gigabyte GA-MA790xt UD4P motherboard
HIS Radeon 4850 video card
AMD Phenom II X3 @ 2.6GHz
4GB of G.Skill Ram @ 1366MHz

---

### Post by Tomatosoup on 2009-05-24
> **Entity` said:**
> Thats what I posted in the linked thread.  I don't know where to go cause im not very good at linux commands.  Be aware that I am using the 32bit version of ubuntu.

PC config:
Gigabyte GA-MA790xt UD4P motherboard
HIS Radeon 4850 video card
AMD Phenom II X3 @ 2.6GHz
4GB of G.Skill Ram @ 1366MHz

I'm using the 32-bit version also now, because I thought it could change things (read it somewhere). But things didn't change.

If you want to access all of your 4 GB of RAM, you should install the 64-bit version of Ubuntu.

---

### Post by Tomatosoup on 2009-05-31
Hm. I think I can watch videos fluently now...
Still using the open-source driver though.
The proprietary driver crashes.

---

