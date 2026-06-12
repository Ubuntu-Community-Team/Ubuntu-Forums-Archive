---
title: "How can normal user access network shares for saving files from openoffice"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by technocp on 2009-06-05
I have a network of ubuntu PCs. I want to have all my files saved on one Ubuntu PC. I also want that all those files can be accessed from any other Ubuntu PC logged in by normal user. Normal users should also be able to save files from openoffice.org directly to the shared folder on other network ubuntu PC. I have used normal right click sharing options and i can access files on network shares and also copy files on network shares but i want an fstab entry which can permanently mount a network folder on local Ubuntu PC and that can be accessed (read & write) by normal user logged in on local Ubuntu PC

---

### Post by regala on 2009-06-05
> **technocp said:**
> I have a network of ubuntu PCs. I want to have all my files saved on one Ubuntu PC. I also want that all those files can be accessed from any other Ubuntu PC logged in by normal user. Normal users should also be able to save files from openoffice.org directly to the shared folder on other network ubuntu PC. I have used normal right click sharing options and i can access files on network shares and also copy files on network shares but i want an fstab entry which can permanently mount a network folder on local Ubuntu PC and that can be accessed (read & write) by normal user logged in on local Ubuntu PC

"man fstab" should give you the answer.

---

### Post by technocp on 2009-06-05
fstab entry that i have made works fine with root user and now i am able to save my files from openoffice when i login using root but not with any other regular user

---

### Post by regala on 2009-06-05
> **technocp said:**
> fstab entry that i have made works fine with root user and now i am able to save my files from openoffice when i login using root but not with any other regular user

can you provide the output from mount and ls -ld <shared_folder_mountpoint> ?
and I am confused, what is the problem ? users can't write to the shared folder ? or users can't mount it ?

br, mathieu

---

### Post by technocp on 2009-06-10
I am trying to make it more clear..

See when I login as root I am able to mount ubuntu network shares and save my files from openoffice as well

But when I login as normal user I am able to mount ubuntu network shares but am not able to save files from openoffice

---

### Post by technocp on 2011-05-12
I finally made it. see we need to add fstab option in /etc/fstab file when we are defining any mount

Eg.

//192.168.1.99/<sharename> /mnt smbfs gid=<groupname>

in above example <groupname> is any group that is created in the ubuntu system. and all the users added to that group will get access to share mounted by root or any other user.

Please correct me if I am sounding incorrect or confusing

---

