---
title: "2nd hard drive not showing up"
date: 2009-07-12
forum: Mythbuntu
---

### Post by BigBig5 on 2009-07-12
I just install Mythbuntu on my 1st hard drive, but when loged in I can't get my 2nd hard drive to show up. The hard drive has things on that I don't want to lose.

---

### Post by klc5555 on 2009-07-12
> **BigBig5 said:**
> I just install Mythbuntu on my 1st hard drive, but when loged in I can't get my 2nd hard drive to show up. The hard drive has things on that I don't want to lose.

Mythbuntu by default is a single-drive install, single-drive aware system. Having installed and configured Mythbuntu, you have to do the usual Linux stuff to incorporate your second drive. Namely, since the drive is obviously already partitioned and formatted, you need to set up a mount point in your filesystem somewhere to mount the main partition on the drive, and then mount it there. 

If you then wish the 2nd drive to be mounted at this point on the filesystem at every bootup, you'll need to manually edit (carefully!) the /etc/fstab file to reflect the change. 

There are innumerable internet guides on how to do this sort of thing, if you have never done it. One of them is here: [http://www.skullbox.net/newsda.php](http://www.skullbox.net/newsda.php)

Skip all the partitioning and formatting sections, which don't apply to your case, and go straight to the paragraph "Mounting".

---

