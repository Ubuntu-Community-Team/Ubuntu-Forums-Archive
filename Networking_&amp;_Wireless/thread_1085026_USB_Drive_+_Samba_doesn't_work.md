---
title: "USB Drive + Samba doesn't work"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by angelkiller on 2009-03-02
Ok. I thought this was going to be a simple task....

I have an USB external hard drive I want to share on my network. However, I've tried many many different ways to get Samba working, but none of them have worked. Windows computers can see the shares but I get an error: "[Share name] is not accessible. You may not have permissions.... <snip> Network access is denied" What's odd is that I have a folder in my home directory that I am successfully sharing. This leads me to believe my permissions are messed up somewhere.

I'd really like if someone would give me some steps to follow so if they don't work, someone could help me troubleshoot.

The drive is Fat32 formatted, and the computer is running Ubuntu 8.10.

Any help or advice is **greatly** appreciated. And if you need more info, like my smb.conf file or something, I'd be glad to give it! :)

---

### Post by wilbbe01 on 2009-03-02
You could try installing and using SWAT.  It is a web based frontend to configure samba, and might help get things working correctly.

---

### Post by angelkiller on 2009-03-02
**Edit: It's not working anymore**

So, I installed Swat. I also added the following two lines to my share in the smb.conf file:
```
force user = [My username]
force group = root
```

Looking through the status page of Swat tells me a couple of things. When accessing the share on the host machine (NOT through /media/[usb drive]) the share is accessed with "[my username]" and the group is "root". However, two Windows boxes and another Ubuntu box access the share with the username "nobody" and the group is "nogroup". 

Why won't the other machines connect with "[my username]" and "root"?

And how can I check to see all the samba users?

Thanks.

---

### Post by rcmn on 2009-03-02
Just to let you know , I have been using samba on linux/freebsd for years now. And any tools i used it never worked properly for the exact need i have(swat/gnomeadmin/kdeadmin/webmin/etc...). So i have a smb.conf that i keep preciously and adapte to my need. And i just have to know where is the userpassword file and the command "smbpasswd -a" to create my smb users.

---

