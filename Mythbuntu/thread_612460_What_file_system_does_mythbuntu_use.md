---
title: "What file system does mythbuntu use?"
date: 2007-11-13
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-13
and if it isn't something fast like xfs, can it be changed to xfs?

---

### Post by uopjohnson on 2007-11-14
You can change it to whatever you like by partitioning your drive and mounting an xfs volume.  I mount mine as /storage - I then I have a recordings, videos, and music subfolder that I configure myth to store in.  You will see the place to configure where recordings are stored in the general setup tab in mythtv-setup.

---

### Post by ubnewbie2 on 2007-11-14
> **uopjohnson said:**
> You can change it to whatever you like by partitioning your drive and mounting an xfs volume.  I mount mine as /storage - I then I have a recordings, videos, and music subfolder that I configure myth to store in.  You will see the place to configure where recordings are stored in the general setup tab in mythtv-setup.

Ok thanks.  I am a long term Knoppmyth user, and I am considering using mythbuntu next time (I am about to upgrade my hardware).  I find ext3 to be intolerably slow, especially when deleting large files, hence I want to use xfs.

---

### Post by uopjohnson on 2007-11-14
I would never use ext3 for my recordings directory as i agree with you, it is intolerably slow. I think you will be pretty happy with mythbuntu it is as easy as knopmyth, just way more up to date and customizable.

---

### Post by ubnewbie2 on 2007-11-14
Thanks, I have downloaded it and I am trying it in a vmware virtual machine - just to see how it installs.

I have already discovered that it doesn't like xfs for the root file system (it says the grub install will fail and it will use lilo), not that it matters, as ext3 is fine for the root, I just want the storage directories with big video files to be xfs.

Looks good!

---

### Post by uopjohnson on 2007-11-14
Yea you can could xfs for your root, but then you have to rebuild your ramdisk and no one wants to do that unnecessarily.  Besides ext3 is more suited to the root file system with its numerous small files.

---

