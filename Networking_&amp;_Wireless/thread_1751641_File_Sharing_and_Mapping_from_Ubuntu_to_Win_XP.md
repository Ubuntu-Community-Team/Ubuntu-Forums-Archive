---
title: "File Sharing and Mapping from Ubuntu to Win XP"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by zander x on 2011-05-06
Hello.

I'm in a dilemma. I have 4 computers/users and we need to put all the files on a central server. The server is running Ubuntu 10.04. What is the best way for these 4 XP users to see the files that will be stored on the server?

Or basically, how will I either share or map the files *from* Ubuntu *to* XP? Also, the users will be reading, writing, creating and deleting files on the server.

---

### Post by cjhabs on 2011-05-06
You want samba on the server - this makes the Ubuntu server appear as a windows server on the network. There is LOTS of information about how to configure it - I have found that sometimes it works straight away and sometimes you need to fiddle a bit - the good folks here will help you sort out any problems you may encounter.
This link will help get you started:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

---

### Post by zander x on 2011-05-11
> **cjhabs said:**
> You want samba on the server - this makes the Ubuntu server appear as a windows server on the network. There is LOTS of information about how to configure it - I have found that sometimes it works straight away and sometimes you need to fiddle a bit - the good folks here will help you sort out any problems you may encounter.
This link will help get you started:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Thanks for the info!

I almost got all the way through, but I'm running into a few problems (all from the WinXP side):

I cannot delete files -- everything is set to "read only"
I cannot access any files I create

My username is "staff" and in the Samba config, I have made myself an admin user (in smb.conf, it says "admin users = staff").

Also, I can get it to show up in the network browser, but I can't get it to map to a certain drive letter.

---

### Post by Iowan on 2011-05-11
Check ownership of the share. My (rather dated, now) Samba Unleashed book suggests that a subdirectory owned by **root** will be readable - but not writable - by an admin user... or I might be misreading the section. 

Is each user to have their own directories/folders or are the files to be commonly shared?

---

