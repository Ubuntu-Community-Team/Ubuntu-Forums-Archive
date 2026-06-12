---
title: "xfs or ext4 for mythtv recordings &amp; videos?"
date: 2009-10-30
forum: Mythbuntu
---

### Post by williammanda on 2009-10-30
Does mythbuntu still use xfs for video storage or has that been changed to ext4? I'm setting up ubuntu 9.10 then adding nythtv thru the control center.
Thanks

---

### Post by ian dobson on 2009-10-30
Hi,

Mythtv can use any linux compatible file system (ext2,3,4 XFS reiserFS). I think 9.10 uses ext4 for boot but I imagine you can use anyfile system you want. Mythbuntu sets the recording directory to /var/something which is usually on the root partition so it would be ext4.

Note: Mythtv includes an option to handle the really slow deleting of very large files on ext3 file systems.

Regards
Ian Dobson

---

### Post by scragar on 2009-10-30
I wouldn't use EXT4 for mythTV yet, because there are known bugs relating to large files being corrupted, since video tends to be large in size this would be far more vunerable than a standard system.

---

### Post by fenian on 2009-10-30
I've been using ext4 on my Mythttv setup for almost a year with no problems.

---

### Post by straxus on 2009-10-30
> **fenian said:**
> I've been using ext4 on my Mythttv setup for almost a year with no problems.

I believe the bug he mentioned is part of the 9.10 kernel, and only affects fresh ext4 installs.  It doesn't affect ext4 partitions upgraded from ext3.  They said a patch is coming post release.

---

### Post by mrand on 2009-10-30
The current state of the [EXT4 situation]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579") is:

[LIST]
[*] There have been approximately 3 people that have reported the problem.  They happen to have been on "created-by-Karmic" filesystems.
[*] With that few reports, it appears to be an extremely rare problem.
[*] If it is extremely rare, can't be said with any assurance that ext3 -> ext4 conversions are safe, or that 9.04 -> 9.10 conversions are safe.
[*] until the problem (if any - it could be hardware problems on all three systems that EXT4 is simply exposing) is better understood, there are no predictions on when a patch will be available to fix it
[/LIST]

The best thing the community can do is to keep an eye out for it - perhaps run a cron script that collects and logs md5sum's on all your largish (hundreds of megs) files.

[INDENT]Marc[/INDENT]

---

### Post by SiHa on 2009-10-30
Luckily, I just installed a new 500G drive for all my recordings, and set it to ext3. I did kick myself a few weeks later on finding that Myth was moving to ext4.

Kinda glad now...

---

### Post by williammanda on 2009-10-30
OK let me rephrase my question...what is mythbuntu using for recordings and videos....xfs or ext4?

---

### Post by SiHa on 2009-10-31
The default install is a single ext4 partition, I believe.

---

### Post by williammanda on 2009-10-31
Mythtv .21 and prior was:
/ ext3
swap
/var xfs

I went ahead and set mine up as:
/ ext4
swap
/var xfs

---

