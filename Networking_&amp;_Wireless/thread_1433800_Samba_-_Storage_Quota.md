---
title: "Samba - Storage Quota?"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-19
Is there a way I can set a storage quota for samba shares, so that way a user can only store up to 2gb of data in a certain share?

---

### Post by jrssystemsnet on 2010-03-19
> **Roasted said:**
> Is there a way I can set a storage quota for samba shares, so that way a user can only store up to 2gb of data in a certain share?Yes and no - Samba doesn't implement quotas of its own, but any *filesystem* quotas you may have in effect will be honored.

With that said - filesystem quotas under pretty much anything but ZFS (which you can't have on Linux) are probably more of a PITA than you want to deal with.  You can't set a filesystem quota on a folder, only on an entire partition - so you'd actually have to have either entire partitions, or virtual filesystems set up for each "folder" you wanted a quota for.

A quick google brought up a how-to you can look at [here](http://souptonuts.sourceforge.net/quota_tutorial.html) to decide if you need this badly enough to go through implementing it. :)

---

### Post by Roasted on 2010-03-19
I'm just wondering how people use Linux file servers with Samba if they need to manage quotas in some way shape or form. It just seems like one of those features that's just kind of "duhhh" that it would definitely be implemented.... kind of surprised it's not...

---

### Post by jrssystemsnet on 2010-03-19
> **Roasted said:**
> I'm just wondering how people use Linux file servers with Samba if they need to manage quotas in some way shape or form. It just seems like one of those features that's just kind of "duhhh" that it would definitely be implemented.... kind of surprised it's not...By using filesystem quotas, of course.  Windows is the same way - there are no share quotas, only disk quotas (which cover an entire partition).

ZFS is the only filesystem I'm aware of which allows dynamic quotas on a smaller basis than entire filesystems; in ZFS you can instantly create a "pool" within a filesystem, and then set a quota on that.  But you can't have ZFS on Linux; only on Solaris or FreeBSD.

And either way, the quotas are *still* at the filesystem level, not the network sharing level, so there you go. :)

---

### Post by Roasted on 2010-03-20
> **jrssystemsnet said:**
> By using filesystem quotas, of course.  Windows is the same way - there are no share quotas, only disk quotas (which cover an entire partition).

ZFS is the only filesystem I'm aware of which allows dynamic quotas on a smaller basis than entire filesystems; in ZFS you can instantly create a "pool" within a filesystem, and then set a quota on that.  But you can't have ZFS on Linux; only on Solaris or FreeBSD.

And either way, the quotas are *still* at the filesystem level, not the network sharing level, so there you go. :)

Then I'll have to see how we have disk quotas on our Windows servers at work. I know we don't have NTFS partitioned out 400 times...

---

