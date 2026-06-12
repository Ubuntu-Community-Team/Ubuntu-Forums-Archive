---
title: "selective mounting of samba share"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by firfin on 2009-02-12
I am using a line in /etc/fstab to mount a samba share on the network. I need this so I can access the files on the share with firefox. For example to upload files or to attach files when using webmail. This works like a charm.:)

However .. now the share shows up for all the users on the system. Including the guest account, I do not want this as the share contains some sensitive information.:(

So my questions:
1 Is there a way to mount a samba share in a way that only some users have access to it? Or a way to prevent the guest account to use the share?

2 Is there another way to connect to samba shares automatically. In such a way that all programs can access it? Opening it in Nautilus does make it available to many programs, unfortunately not to for instance firefox.

---

### Post by firfin on 2009-02-13
Nobody knows of a way to either:

- make samba shares usable for firefox?

- how to make a mounted drive available for some users only?

---

### Post by ohgodnotanother1 on 2009-02-13
Have a look at this: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by firfin on 2009-02-13
Thank you for replying to my question. Unfortunately I don't quite see how that post applies to my problem? Can  you elaborate?
The thread is about setting up a samba server and share. I have already done this and can connect to it.

I have also added a line in my fstab to automount the share at startup. In this way even (non-gvfs-aware) programs like firefox can use the share. 
My problem is that the guest account can also access it.

Or I need to find another way (based on logged in user) to connect to the share

---

### Post by firfin on 2009-02-23
I have also asked the question here. 

[http://ubuntuforums.org/showthread.php?p=6786444](http://ubuntuforums.org/showthread.php?p=6786444)

Maybe it makes more sense to some people,

---

### Post by capscrew on 2009-02-23
> **firfin said:**
> T... I need to find another way (based on logged in user) to connect to the share

Use the following in the share definition:
```
  valid users = login_name 
  valid users = +group_name
```

The use of +groupname allows all users of the group access.
There are variable substitutes for user_name

---

### Post by firfin on 2009-03-12
Thank you for your answer. Unfortunately that does not help me very much. The problem is that I use fstab to mount the drive. In fstab the user and password for the share are already set.  I need to mount the share else it will not be available in non-gvfs programs (e.g. firefox)

So using a username check on the share will not work, as the client always connects with the same username (the one in fstab)

---

