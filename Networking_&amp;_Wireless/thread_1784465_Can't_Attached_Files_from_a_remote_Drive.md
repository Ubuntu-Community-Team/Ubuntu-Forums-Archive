---
title: "Can't Attached Files from a remote Drive"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by juanbisente on 2011-06-17
Hi!

I'm trying to attach a file from a remote disk to my email. I already mounted the disk, but every time I need to attach a file from the remote disk I can't find the mounted disk at the side pane.
Please help

Thanks

---

### Post by An Sanct on 2011-06-17
> **juanbisente said:**
> Hi!

I'm trying to attach a file from a remote disk to my email. I already mounted the disk, but every time I need to attach a file from the remote disk I can't find the mounted disk at the side pane.
Please help

Thanks

Have you tried to look for the mounted disk in this location: '/media/..'?

Is the file too large to copy to your desktop and attach it from there?

---

### Post by juanbisente on 2011-06-17
no, I could not find it in /media.

I always do that, copy it to my desktop, then attached it. That's why I'm looking for a way to attached file from the remote disk w/o copying it to my desktop

I mounts the disk by pressing ctrl + L on my desktop and typing smb://"the ip address"/"name of folder

---

### Post by An Sanct on 2011-06-17
> **juanbisente said:**
> no, I could not find it in /media.

I always do that, copy it to my desktop, then attached it. That's why I'm looking for a way to attached file from the remote disk w/o copying it to my desktop

I mounts the disk by pressing ctrl + L on my desktop and typing smb://"the ip address"/"name of folder

I don't know if a SAMBA share ( smb: ) could be called a "mounted drive" ... but, have you tried to do that in the edit box, where the file name should be?

---

### Post by juanbisente on 2011-06-18
How can I make a link to a Samba share? If it is not a mounted device it can't be seen /media

```
but, have you tried to do that in the edit box, where the file name should be?     
```Where is that edit box? And what should I Edit?

Thanks

---

### Post by An Sanct on 2011-06-19
> **juanbisente said:**
> How can I make a link to a Samba share? If it is not a mounted device it can't be seen /media

```
but, have you tried to do that in the edit box, where the file name should be?     
```Where is that edit box? And what should I Edit?

Thanks

The "edit box" is where the file name should be, if you want to upload a file, it should give you the option to type in the file name into the dialog.

---

### Post by juanbisente on 2011-06-21
> The "edit box" is where the file name should be, if you want to upload a  file, it should give you the option to type in the file name into the  dialog. 	

I've tried it but I cant type to the dialog box, it only offers to browse items to be attached. Is there a way to attached file from a samba share device.

Thanks

---

### Post by juanbisente on 2011-06-22
I already got the solution.
I've read a thread about it. Samba Shares can be found in /home/name_of_home/.gvfs.

thanks an sanct

---

### Post by An Sanct on 2011-06-22
Great :)

Please be so kind and mark this thread as solved, so others can find and use the solution, that worked for you....

Cheers!

---

### Post by juanbisente on 2011-06-22
Sure

Thanks for your help. this the thread where i found the solution:
[http://ubuntuforums.org/showthread.php?t=1547030&highlight=attach+samba+shares](http://ubuntuforums.org/showthread.php?t=1547030&highlight=attach+samba+shares)

Thanks

---

