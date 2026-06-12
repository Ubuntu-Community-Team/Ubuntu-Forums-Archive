---
title: "Samba share for two users"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by skinney6 on 2012-10-25
ubuntu server with samba and a couple win 7 machines
i want two user to have access to their respective home dir's
easy, done
i also want those two to have access to a shared dir
kind of done. when user1 puts a file in the shared dir 
user1 is owner and group so user2 can't access it modify it
i've created a samba group, gave it ownership of this dir and added these users to the group but didn't help

#ls -l
-rw-rw---- 1 user2 user2  122368 Sep 18 19:12 doc33.doc
-rw-rw---- 1 user1 user1 238264 Aug 21 09:25 doc1.pdf

my conf

[share]
        comment = Ubuntu File Server Share
        path = /share
        valid users = @samba
        read only = No
        create mask = 0660
        directory mask = 0770

i guess what i need is to somehow give the group "samba" ownership of any files moved into this shared dir
so it'll look like this...
#ls -l
-rw-rw---- 1 user2 samba  122368 Sep 18 19:12 doc33.doc
-rw-rw---- 1 user1 samba 238264 Aug 21 09:25 doc1.pdf

or there must be another way (i'd rather not change to 'security = share')

just deleted valid users = @samba and both users access didn't change

---

### Post by ahallubuntu on 2012-10-25
Add this line to the share definition:

```
force group = samba
```

where "samba" is the group you created/added both users to.

---

### Post by skinney6 on 2012-10-26
perfect!
thank you!

---

