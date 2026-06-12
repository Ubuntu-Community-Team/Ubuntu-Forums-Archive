---
title: "BTRFS is hella slow"
date: 2010-07-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by blazemore on 2010-07-20
I've installed Maverick with a 60GB BTRFS / partition (See screenshot)
The entire system is incredibly slow, like wading through treacle.

Image thumbnails load 1 by 1, so do menu icons.
Small applications take an age to install (Arista transcoder >10 minutes)

Is there anything I can do to improve this? Same system on ext4 absolutely flies.

---

### Post by donniezazen on 2010-07-20
> **blazemore said:**
> I've installed Maverick with a 60GB BTRFS / partition (See screenshot)
The entire system is incredibly slow, like wading through treacle.

Image thumbnails load 1 by 1, so do menu icons.
Small applications take an age to install (Arista transcoder >10 minutes)

Is there anything I can do to improve this? Same system on ext4 absolutely flies.

I have all my partition in btrfs except /boot and only file transfer is slow not the whole system. This could be a bug.

---

### Post by gnomeuser on 2010-07-20
I'm not currently on btrfs but after a recent update everything got every pokey. 

Though specifically for dpkg there might be some issues with how it uses the disk that is causing btrfs to be slow, bugs should be filed.

---

### Post by ratcheer on 2010-07-20
> **gnomeuser said:**
> 

Though specifically for dpkg there might be some issues with how it uses the disk that is causing btrfs to be slow, bugs should be filed.

Someone on dslreports made a similar comment, that btrfs was slow for dpkg. I'll try to find it and post a link.

Tim

---

### Post by ratcheer on 2010-07-20
> **ratcheer said:**
> Someone on dslreports made a similar comment, that btrfs was slow for dpkg. I'll try to find it and post a link.

Tim

See the post by jdong in this thread:

[http://www.dslreports.com/forum/r24523668-Anyone-using-btrfs](http://www.dslreports.com/forum/r24523668-Anyone-using-btrfs)

Tim

---

### Post by blazemore on 2010-07-20
I filed a new bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/607632](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/607632)

---

### Post by VastOne on 2010-07-20
Those of you that have successfully implemented btrfs, did you have to use the alternate maverick CD to get it loaded?


Sorry if I am hijacking....:oops:

---

### Post by donniezazen on 2010-07-20
> **VastOne said:**
> Those of you that have successfully implemented btrfs, did you have to use the alternate maverick CD to get it loaded?


Sorry if I am hijacking....:oops:

It's available in desktop ISO. Just choose btrfs while manual install.

---

### Post by blazemore on 2010-07-20
> **soham_1207 said:**
> It's available in desktop ISO. Just choose btrfs while manual install.

Just like choosing ext4 in Jaunty.

---

### Post by VastOne on 2010-07-20
> **soham_1207 said:**
> It's available in desktop ISO. Just choose btrfs while manual install.

Yep...been trying that but it errors out and kicks me out of the install right at the point of creating/format the btrfs drive

I am going to try now with the alternate.

Thanks

---

### Post by donniezazen on 2010-07-20
> **blazemore said:**
> Just like choosing ext4 in Jaunty.
 
Yes go to manual installation make sure you create a ext2/ext3 /boot partition. All other partition like /, /home and swap can be btrfs.

---

### Post by VastOne on 2010-07-20
> **VastOne said:**
> Yep...been trying that but it errors out and kicks me out of the install right at the point of creating/format the btrfs drive

I am going to try now with the alternate.

Thanks

I used the alternate to create the btrfs but it failed to retrieve files.

Went back to the desktop iso and since the btrfs is there it is now installing.

I will head over and file a bug on this...

---

### Post by jfernyhough on 2010-07-21
> **blazemore said:**
> I filed a new bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/607632](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/607632)I reckon it's more likely a btrfs bug/feature than something to do with dpkg; it may be load-balancing across the disk after each package or something odd like that.

---

### Post by gnomeuser on 2010-07-21
It does seems that dpkg might be the problem, it appears to, at least in some versions, fsync() quite a lot. Ext4 (and btrfs for that matter) famously has performance issues with certain fsync() usage, and dataloss problems without it.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/570805](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/570805)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/537241](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/537241)
[https://bugzilla.kernel.org/show_bug.cgi?id=15910](https://bugzilla.kernel.org/show_bug.cgi?id=15910)

---

### Post by jfernyhough on 2010-07-21
Ah, right!

---

