---
title: "Samba Authentication. Permission or Password?"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-29
So, I have a samba server running. Someone in IRC suggested that I really don't need the two layer authentication I currently have, because my permissions on my samba shares are set up properly on my Linux box.

/media/storage = samba shares directory, owned by jason:samba with 770 permissions. Members of "samba" include pam, curt, tyler, jason, user.

So, here's the rundown. ALL permissions of ALL directories is 770.

/media/storage = jason:samba

/media/storage/tyler = jason : tyler
/media/storage/curt = jason : curt
/media/storage/pam = jason : pam
/media/storage/jason = jason : jason

Problem is, unless I have a "valid users = ------" tag underneath each share path in the smb.conf, the user "user" can go... anywhere. Linux permissions are simple. Take curt for example. Jason:Curt. User is not a member of the group Curt, so for  User to get access, he'd get access from the "Others" category. But wait, we have 770 permissions. So how can User access the shares and write to them? Is it because /media/storage is 770 with samba being the group and user is an active member of the group samba?

I don't get it. When I applied 770 permissions to /media/storage, that's where I want them. When I assign jason:samba ownership to /media/storage, that's where I want it. As a result, when I apply different permissions to sub directories, I'm putting them there for a reason. So it's frustrating to have /media/storage/curt with the proper permissions set up to keep "User" out of the picture, yet User has full blown do-whatever-he-wants rights to it.

So, that brings me back to my original point. To effectively have solid permissions on a Samba network, does "valid users = --------" come across as a requirement in your eyes to apply the best security?

I just thought I could set up Linux permissions intelligently enough to not need to worry about Samba-level access restrictions. But it seems like it may be a requirement.

So, to sum everything up, I basically have 2 questions:

1 - Does the fact that the group "Samba" have RWX permissions have anything to do with why "User" can read/write/execute to /media/storage/curt even though User is NOT a member of Curt and there is NO permissions for all others to even be in that directory in the first place?

2 - To have effective and intelligently laid out security with Samba, is utilizing the "valid users = -----" option pretty much a requirement?

---

### Post by Roasted on 2009-11-30
any takers?

---

