---
title: "Files are not visible in mounted windows share"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by falconed7 on 2010-01-19
I have a password protected share and have added it in /etc/fstab

ie.
```
//192.168.0.17/share  /home/jamie/share  cifs  username=user,password=password  0  0
```

I have mounted it successfully however when I open the folder there are no files visible.

I have installed smbfs so there is no problem there. I am certain there is no problem server side as my windows computers can access the share with no problems.

Anyone have any ideas on where a problem could be?

Any help would be greatly appreciated!

---

### Post by falconed7 on 2010-01-20
Bump.

I forgot to add that I can successfully connect and see the files when going Places>Connect to Server.

Does anyone have an idea on whats wrong? Google doesn't seem to be very helpful either.

---

### Post by user1397 on 2010-01-20
So let me get this straight.  You have some files or folders in /home/jamie/share but if you open that up they don't show up, even though they show up if you connect to server and from your windows box?

---

### Post by falconed7 on 2010-01-20
> **ubuntuman001 said:**
> So let me get this straight.  You have some files or folders in /home/jamie/share but if you open that up they don't show up, even though they show up if you connect to server and from your windows box?

Yes. Is this hard to believe? /home/jamie/share has mounted fine (ie. it has shown on the the desktop, Yet when I open it it shows nothing is in there.

I have attached and image.

---

### Post by johnson.d on 2010-01-20
You can edit the /etc/fstab file and add replace the entry as

//192.168.0.17/share /home/jamie/share cifs username=user,password=password,uid=userid,gid=groupid 0 0

Where the userid is your Linux uid and the groupid is your Linux gid.

This will result in the files/directories showing up as owned by that uid/gid and you will be able to eliminate any permission related issues on the client.

Also you can switch the user to root and try to list the files in the mounted folder, again to check if there are any permission issues on the client.

Please let me know how it goes.

---

### Post by user1397 on 2010-01-21
> **falconed7 said:**
> Yes. Is this hard to believe? /home/jamie/share has mounted fine (ie. it has shown on the the desktop, Yet when I open it it shows nothing is in there.

I have attached and image.
/home/jamie/share is not the directory for that...it seems to be an external drive of some sort, which is probably mounted at /media/something

What filesystem does this external drive have?  there are some filesystems linux can't read and/or write (i think)

also, type ```
df -h
``` in a terminal and post the output (this will show you the filesystem types of all drives connected to your pc)

---

