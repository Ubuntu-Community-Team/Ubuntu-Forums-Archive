---
title: "network storage access"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by styven on 2009-05-04
Hi all,

I appreciate that this topic is not a new one and i have read many threads on it, but with no real success in actually successfully accessing folders on other pcs or on network storage. I have been able to access a windows pc from an ubuntu pc, but that's it.
Most threads seem to assume Windows shares, I am only interested mainly in accessing from various linux machines.

So I am trying plan ahead and maybe clarify some points before I embark on the following...............

I want to put a 250gb hdd into a network enclosure and attach it to my router.
I want all pc's (three ubuntu,1 x ps3) to be able to see it and access the data on it.

What do i need to look out for in the specs for the enclosure?
Can i use NFS instead of Samba, does the hdd enclosure need to support NFS?

Any tips appreciated.

Steve.

---

### Post by gooligan on 2009-05-04
Most consumer network-enclosures come with Samaba/Windows shares. I have WD MyBookWorld that has it and I am able to access it remotely from Ubuntu.
Here is the entry from my /etc/fstab that works (for me)

```

# Mount MyBookWorld:/PUBLIC to /mnt/MyBookWorld
//MyBookWorld/PUBLIC	/mnt/MyBookWorld		cifs	defaults,user,noauto		0	0

```

Keeping Samba as your share allows native access from Windows PCs

---

### Post by styven on 2009-05-10
Well, after years of trying top get SMB or NFS to work, instead tried SSH today and within 10 minutes I was able to access all my home pcs and indeed my external drive that is plugged into one of them.

Ridiculously easy, even my wife will be able to cope with this, why use SMB of NFS?

---

### Post by bayvista on 2012-12-14
To Gooligan: I have no problem accessing the Public shares, but cannot write to the private shares. When I added myself as a user of MyBookWorld, it created a folder for me. However, the permissions won't allow access from Ubuntu. Any ideas?

---

