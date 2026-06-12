---
title: "Share folder to certain ip addresses only"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by longtom on 2009-12-11
Hi,

I did Google but somehow I hit a blank again and I can't find what I am looking for.

I am a Ubuntu machine on what is essentially a windows LAN network.  I want to share certain directories in such a way that only certain computers can see and/or access the directory.

All computers on the network have a unique ip address.

How would I go about it?

Any suggestions welcome.

---

### Post by longtom on 2009-12-11
Got the same text in the beginners forum.  If that is not allowed please feel free to delete.

Hi,

I did Google but somehow I hit a blank again and I can't find what I am looking for.

I am a Ubuntu machine on what is essentially a windows LAN network. I want to share certain directories in such a way that only certain computers can see and/or access the directory.

All computers on the network have a unique ip address.

How would I go about it?

Any suggestions welcome.

---

### Post by cariboo on 2009-12-11
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by longtom on 2009-12-12
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your two threads.

Sorry about that.  Their appears to be no answer anyway, so it was a pointless exercise.  Will refrain from multiple threads,

---

### Post by SlugSlug on 2009-12-12
you would want samab for the folder shares, and some for of iptable - maybe firestarter could help?? I've not played much with iptables

---

### Post by longtom on 2009-12-12
> **SlugSlug said:**
> you would want samab for the folder shares, and some for of iptable - maybe firestarter could help?? I've not played much with iptables

Thank you - I have samba and am happily connected to a network.  So that is not the problem.  It's more about the control what to share to who.  So far I can either restrict everybody on the network or allow everything to everybody with smb.conf.

Firestarter?  iptables?  I am off to research.

---

### Post by SlugSlug on 2009-12-12
Or you could look into ACL's for the shared folders... that would be the better solution I think.

and then create samba users / maybe tie into your domain windows accounts create groups say
gvideos
gmusic

and assign users to the groups of whom you want to access what...

---

### Post by longtom on 2009-12-12
> **SlugSlug said:**
> Or you could look into ACL's for the shared folders... that would be the better solution I think.

and then create samba users / maybe tie into your domain windows accounts create groups say
gvideos
gmusic

and assign users to the groups of whom you want to access what...

Could you elaborate on "ACL's"?  Assume I know nothing (which is as close to the truth as you get...)

---

### Post by SlugSlug on 2009-12-12
ACL's lets you control your folders you could have a group called gmusicusers and allow them read and execute access to /Music by
(edit; firstly adding the group $ sudo addgroup gmusicusers)
setfacl -m -R group:gmusicusers:rw /Music


this will allow the users in that group to open folders (execute) and read all the contents you could make it
:rwx   to allow them to add / delete files

I use this for shares on my PC - I share over SSH to other Linux users, windows can access file this way with a prog called winscp but I don't think thats best for local networks.

have a look over these two sites
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://aisalen.wordpress.com/2007/08/10/acls-on-samba/](http://aisalen.wordpress.com/2007/08/10/acls-on-samba/)


that should give you an idea

---

