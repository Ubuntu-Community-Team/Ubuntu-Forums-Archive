---
title: "User permissions in FTP Ubuntu?"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by chechelopez on 2009-01-28
I configured an user aweevraa.com.. and other named slug.com.mx

Then I have in my home folder
home/
>aweevraa.com/
>slug.com.mx/

I configured vsftpd for a FTP Server, I can access with both users writing in his home folder but... I can access freely(read access) through all the server folders... and I just want that aweevraa.com can only watch the content of his home folder

How can I achieve this ?

---

### Post by BrandonBan6 on 2009-01-28
I'm not sure I follow, you want user 'aweevraa.com' to see /home, and not 'slug.com.mx'?

---

### Post by chechelopez on 2009-01-28
I want aweevraa.com to see just his home folder

aweevraa.com

actually this is the initial directory when I connect with that user to FTP but... then with the same user I can go to home folder and then see slug.com.mx files...

That is the behavior I want to avoid :(

---

### Post by BrandonBan6 on 2009-01-28
Sounds like all you need to do then is remove read, write. execute permissions from groups and others for the specified file.

```

sudo chmod go-rwx /home/slug.com.mx

```

the same code for any other file where you only want a specific user to have access to.

---

### Post by chechelopez on 2009-01-28
Yeah this works for that folder

but... That user also can see

/bin
/boo
/cdrom
/dev
/etc
/home

All the tree structure

what do I have to do for the user in order to achieve this.. just aweevraa.com can see his files and nothing else... 

With Filezilla Im achieving to connect and see the content of /bin for example...

---

### Post by BrandonBan6 on 2009-01-28
Ah, I see where you are going with that. Okay, that's simple too, just a matter of group permissions. Let me think this out a second...

---

### Post by yknivag on 2009-01-28
There is usually a way in the FTP server daemon to "lock users to their home directories" - I've done it before but I've never used vsftpd.

A quick search suggests you simply add:
```

chroot_local_user=YES
chroot_list_enable=YES

```
to your /etc/vsftpd/vsftpd.conf file but you may want to check that out in the vsftpd docs...

---

### Post by chechelopez on 2009-01-28
Actually the answer was this

chroot_local_user=YES 

edited in /etc/vsftpd.conf 

Thanks a lot a lot :KS

---

