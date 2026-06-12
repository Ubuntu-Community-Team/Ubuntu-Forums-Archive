---
title: "Mythbuntu New Setup"
date: 2008-02-03
forum: Mythbuntu
---

### Post by bman on 2008-02-03
*I am wanted to setup a backup/media server in my home. I have many questions to this so I was not sure what to call the thread.*

1. I am going to be having all my media on the drives, is it safe to setup raid on those drives? I'd really like to be able to keep on expanding my drives once I can get more drives, how can I do that and is it safe?

2. Are there instructions on how to allow other computers to access this Mythbuntu media server? Even windows computers?

3. I am going to be using a

[B][I]ASUS M2N32-SLI Deluxe motherboard
AMD Athlon 64 X2 2.4Ghz CPU[/I][/B]

How much RAM is suggested to use for HD content, I am assuming 3GB but if 1GB enough? Any other suggestions to hardware?

4. I already got a Satellite Card but I was wondering what the majority say is the best tuner and remote out there for linux at least? How expensive is it to get.

I think that is all the questions for now, I will update when more comes to mind.

---

### Post by wo_shi_big_stomach on 2008-02-04
1. I am going to be having all my media on the drives, is it safe to setup raid on those drives? I'd really like to be able to keep on expanding my drives once I can get more drives, how can I do that and is it safe?

Yes, you can set up RAID on those devices. But given your other requirement of expandability, then LVM (Linux Volume Manager) might be a better choice. It's *really* easy to set up. Just see the sticky instructructions at the top of the mythbuntu forum page, or section 9.5 of this alternative:

[http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html")

LVM makes multiple disks (or even multiple parts of multiple disks) look like a single logical volume. It does not give you any redundancy. For that you need RAID.

Some random thoughts about RAID:

a. RAID and LVM can be used together, with RAID providing disk redundancy and LVM spanning multiple disks.

b. If you've got the budget, go for hardware RAID (3Ware, LSI Logic, among others) which is faster than software RAID.

c. There are many different RAID levels. Do NOT use RAID0, which is functionally similar to LVM and buys you nothing in terms of protection from disk failure. RAID1 is better, in that it mirrors the contents of even numbers of disks. RAID5, which requires three or more disks, gives you N+1 of disk capacity (where N is your disk count) but disk access is slower than RAID1. Personally I use RAID1 for machines that need fast disk I/O and RAID5 for everything else. Streaming video counts as an application that would benefit from RAID1.

> 2. Are there instructions on how to allow other computers to access this Mythbuntu media server? Even windows computers?

Yes. Samba allows *nix machines to look like a Windows file server to Windows machines. It's a fast way to share files. 

If you're asking about running myth from other machines, read the documentation at mythtv.org about setting up separate machines for front-end and back-end myth servers.

> 3. How much RAM is suggested 

As always -- get as much as you can possibly afford, and then double that :-)

> 4. I already got a Satellite Card but I was wondering what the majority say is the best tuner

sorry, no idea

/wsbs

---

### Post by bman on 2008-02-04
Thanks for the reply.

I will have more questions when I am closer to the time when I will be setting the server up. For now I guess I would have to ask how would I do a RAID & LVM together, would I need to RAID the drive first, and then what....

I know I will have more questions about the other items you replyed to but at the moment I don't. I will post back later on.

---

### Post by wo_shi_big_stomach on 2008-02-04
*For now I guess I would have to ask how would I do a RAID & LVM together, would I need to RAID the drive first, and then what....*

Yup, RAID first, and then LVM on top of that.

But before either one, first ask what you're trying to do. 

If you want to save your data from loss, neither RAID nor LVM are the right thing. Only a backup (including at least one copy off-site) will help  there.

RAID will help protect you when a disk dies; you can hot-swap in a new disk and the RAID controller will recreate the partition on the fly.

LVM will help you carve out multiple sections of multiple disks so that they look like one partition to Linux. 

For data protection, backup is BY FAR the best of these. The others are nice to have (and hardware RAID can improve performance) but they won't help if -- heaven forbid -- your box goes up in smoke.

/wsbs

---

### Post by bman on 2008-02-04
I do want to save my data from loss, that is always a consern. Yet I also want to be able to expand, and be able to swap a new drive in if one dies without any loss. I will of course get backup drives for the RAID - LVM Drives of course, but at the moment I can't.

LVM, is it like an installation I do within linux? Or how is it done?

---

### Post by ridshack on 2008-02-04
One high point to RAID is you will help prevent downtime due to a failed drive. Can you imagine loosing your for any amount of time?

Rid

---

