---
title: "Best way to mount user data drive"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Sigma47 on 2009-11-02
OK after sacrificing a wknd at home eating halloween candy I almost have almost arrived in dual boot utopia. I am now looking for the best way to mount user data so that all the permissions are correct and my gf won't delete my grad school career because she's not used to gnome or linux in general. So, I have a data drive with directories for me, her, and a share on this NTFS partition. I am mounting that in /mnt/data/ but I have it set up in fstab with my uid and a gid that both of our accts are included in. Problem with this is that we both have free reign over everything and I am the only one with a working trash can. So. whats the easiest route to success here? I thought about splitting the part into two, one for each and then mounting them separate with different perms. I need to have windows for work so I would like to keep it in NTFS but I also thought FAT may work too. In any event is there any thing Im over looking here a simpler way? Thanks in advance!

---

### Post by Sigma47 on 2009-11-05
Anybody with any input on this would be much appreciated...can't seem to mount ntfs with inherited permissions

---

### Post by shredder12 on 2009-11-05
I am not sure about ur problem but i use PySDM, it is a storage device manager, easily configurable..
give it a try..

---

### Post by Sigma47 on 2009-11-06
Thanks for the point to pySDM but it wasn't a winner as I have already tweaked fstab into next week... My problem is that I have 2 users on my computer and the data drive has 2 user directories on I want to be able to preserve permissions to some extent but the big thing to me is that there is no trash for both users, its none or one but not both. I can choose to mount it under my uid and I can delete with deletions moved to my trash but then when my lady friend logs on she will delete something and it will be deleted forever immediately. So, I'm a lil noided out about not having the trash as Im one to delete something and then want it back in a day.

---

### Post by shredder12 on 2009-11-06
I was a little confused about your issue so I created another user on my machine and tried to simulate the same scenario. 

I created the user from System->Administration->Users and groups, after that I gave it required permissions to access the externally storage devices.

I have a 40 GB windows partition (ntfs) on my machine and when I opened the other account it was already mounted with 777 permissions as root.
And I think that even though both of them had different trash folders but we can link them to a single folder.(accessible by both).

If it is of any help then this is how I mount my windows partition (my /etc/fstab entry)
```
/dev/sda1                                  /media/sda1  ntfs  defaults           0  0  
```

---

