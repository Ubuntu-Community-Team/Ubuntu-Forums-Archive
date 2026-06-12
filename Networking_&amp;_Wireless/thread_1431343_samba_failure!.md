---
title: "samba failure!?"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by csb346 on 2010-03-16
I've just installed an ubuntu 9.10 server at my office and configure apache, php and mysql without problems.
Now i need to share some directories in order to wed developers access to the websites files.
But when I try to share, ubuntu tries to install samba services, and I keep to get those errors:
"W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.0-3ubuntu5.4_i386.deb](http://pt.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.0-3ubuntu5.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.0-3ubuntu5.4_all.deb](http://pt.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.0-3ubuntu5.4_all.deb)
 Size mismatch"

Anyone can help me please?

---

### Post by johnson.d on 2010-03-17
You can try the following command to refresh the package list:

$ sudo apt-get update

Now you can try installing Samba package again.

---

### Post by csb346 on 2010-03-17
already done... and nothing solved :(
When I use the "update manager", it gives me the same errors.
I can't find anything about these erros on the web! No one else already had this problem?!

---

### Post by dmizer on 2010-03-17
Sounds like the repositories you're using aren't synced. Try changing the repos to something else like "us" instead of "pt".

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server)

---

### Post by csb346 on 2010-03-17
IT WORKED! :D THANKS!!!

unfortunately now there's another problem :(

When I try to share a folder, it says that it needs to change permissions. And send this error:
"Failed to execute child process "testparm" (no such file or directory)"

Anyone?



_________________

FORGET! I solved it ;) Thanks all.

---

### Post by csb346 on 2010-03-17
Well, now I have another wall to cross.

I'm able to share a folder in my "home folder", everything seems fine, but when I try to access it throught network from a windows xp; I get the error: 

"\\linuxws\teste refers to a location that is unavailable. It could be on a hard drive on this computer, or on a network. Check to make sure that the disk is properly inserted, or that you are connected to the Internet or your network, and then try again. If it still cannot be located, the information might have been moved to a different location."


And the other problem is that I still can't share the folder /var/www. :(

Does anyone know how to share that folder and be accessible from a windows computer on my network?

---

### Post by johnson.d on 2010-03-25
> I'm able to share a folder in my "home folder", everything seems fine, but when I try to access it throught network from a windows xp; I get the error:

"\\linuxws\teste refers to a location that is unavailable. It could be on a hard drive on this computer, or on a network. Check to make sure that the disk is properly inserted, or that you are connected to the Internet or your network, and then try again. If it still cannot be located, the information might have been moved to a different location."

You can try configuring Samba manually using the following procedure:

1) Edit the file /etc/samba/smb.conf. Append the following lines to file: 

```
[<share-name>]
path = /<share-path>
browseable = yes
read only = no
guest ok = yes
```


2) Restart the Samba service using the following command

```
$ sudo /etc/init.d/samba restart
```

Now try connecting from the windows XP

> And the other problem is that I still can't share the folder /var/www.

Does anyone know how to share that folder and be accessible from a windows computer on my network?

You can refer to the following thread for sharing the /var/www folder

[http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

---

