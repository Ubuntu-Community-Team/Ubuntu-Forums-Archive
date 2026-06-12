---
title: "samba share mounting permission problem"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by technocp on 2010-02-02
Dear all,

This is regarding samba and its mount on other machine, please guide me if iam posting my thread in a wrong category,

I have created a samba share and mounted the share with /etc/fstab on another machine. This share is supposed to be a fully public share i.e. i have different share where different permissions are set but on this particular share i intend to have full read write and execute rights to all the users on my mounting machine.

The problem is that I get only owner and group rights for write on directories that i create due to which all my users can create files in my mount directory but when they create a folder they cannot create any file inside that folder.

can any one give any Idea where I am going wrong

Thanks in advance

---

### Post by superprash2003 on 2010-02-02
on the local machine , right click on the folder which you are sharing and click on properties , then go to permissions and under OTHERS allow to create and delete files

---

### Post by technocp on 2010-02-03
thanks superprash2003 for the suggestions

But this is some thing beyond just right clicking and selecting permissions the thing is that my samba is setting some permission and SGID on public share that I have created and when that share is mounted on another Linux machine the permissions are changed as per Linux system where the share is mounted. I want that the public folder which is mounted should maintain the permissions set by samba. So that when ever any user creates any file or folder samba permissions should be applied to them also. This means that when some other user on Linux machine where share is mounted, tries to open files they should not be in read only mode. any user should be able to use, modify, delete any file or folder available or created on the mount.

Thanks in advance for any help

---

