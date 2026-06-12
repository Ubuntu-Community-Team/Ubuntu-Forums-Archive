---
title: "automount network folder"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2009-10-15
If I execute this command :-

 sudo mount -t cifs //192.168.2.4/ubuntu -o user=bill,password=**** /mnt/xp

the folder is mounted OK.

I've edited /etc/stab with the following line at the end:-

//192.168.2.4/ubuntu    /mnt/xp username=bill,password=****   0       0

but the folder doesn't auto mount at startup.

Where am I going wrong?

Bill Lancaster

---

### Post by uncle-c on 2009-10-15
Hi Bill, 
To auto mount at start up you have to use the "auto" directive in your fstab file.

[http://ubuntuforums.org/showthread.php?t=1139646](http://ubuntuforums.org/showthread.php?t=1139646)

Read the last post and it will give you a an idea on how an fstab file should look like.

---

### Post by bill-lancaster on 2009-10-15
Thats great!

//xxx.xxx.x.x/ubuntu    /mnt/xp cifs    auto,username=bill,password=****

works a treat

Thanks for the help,

Bill

---

### Post by AntonJ on 2011-08-05
Hi,
 I can&#8217;t figure out permissions.
My etc/fstab line:
//10.0.0.10/IT/Windows_folder /home/anton/Server smbfs auto,user,rw,username=anton1,password=pass1 0 0
The folder actually auto-mounts, but it is read only. At least from my  login (default administrative privileges). The folder is writable only  from root :(.
Server-side config:
windows XP machine
configured username &#8211; anton1
configured password &#8211; pass1
Client-side config:
Ubuntu 10.10 machine
configured username &#8211; anton2
configured password &#8211; pass2
 I have no problems to access folder using nautilus and ditect path (smb://10.0.0.10/IT/Windows_folder)
But I can&#8217;t write to mounted folder (/home/anton/Server)
Looks like mounting gives me read-only privileges. How can I diagnose  this? Did I forgot something? Is there other configurations that I  forgot to edit?
I have browsed all over the web no luck :(

---

### Post by AntonJ on 2011-08-05
SOLVED!!!

As I understud, mount gives rw privileges to root and "anton1", so I have to add "uid=1000" (the uid for anton2, pass2). :)
finaly:
//10.0.0.10/IT/Windows_folder /home/anton/Server smbfs auto,user,rw,username=anton,password=pass,uid=1000 0 0

I think 3 users can write to folder now:
1) root
2) anton1, pass1
3) user with uid=1000 (anton2, pass2)

---

