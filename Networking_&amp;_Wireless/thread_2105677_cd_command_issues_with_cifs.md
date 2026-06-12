---
title: "cd command issues with cifs"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by axiagame on 2013-01-16
Hi everyone,

First, I hope I am at the right place to ask the question, if not I'm sorry for the inconvenience it may have caused.

I recently installed a command-line ubuntu on a new PC I just built, and am now trying to access files on my NAS server (to get source code for compilation).

My NAS has 2 accounts, the admin account and a guest account. The folder I am trying to cd into is reserved to administrators (owner = admin, owner_group = administrators, and rights are read, write and execute for the owner and the group).

So, I mount my NAS shared folder using cifs with the following command line
sudo mount -t cifs //192.168.0.12/NAS /mnt/nas -ouser=admin

+ I type my password.

All works fine, but when I try to do a cd on the said directory, ubuntu tells me I am not allowed to do so. However, I am correctly connected as administrator, since I have the right to write and delete files in the other folders (guest use has none of these rights). I also connected to the GUI of my NAS using my windows web browser, and it says my ubuntu is connected as admin.

I also tried to add mode=0777 at the end of the mount command, but still same problem.

Does anyone have an idea ?

Thanks in advance for your answers :)

@xi@

---

### Post by chadk5utc on 2013-01-16
Im guessing your using admin as an example?

---

### Post by dannyboy79 on 2013-01-16
what are the permissions on the /mnt/ folder and /mnt/nas/ folders prior to mounting your share there?

---

### Post by axiagame on 2013-01-17
@chadk5utc : no, it is not an example. But in the future, I'll create a user on the NAS only for this ubuntu OS. I'm now just trying to make this work ^^

@dannyboy79 : /mnt and /nas are both chmoded 0777

---

