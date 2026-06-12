---
title: "How to Home Network and two PCs of Ubuntu?"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by saidbakr on 2009-09-09
Hello,

I read more and more about getting two Ubuntu's PCs to get file sharing and I could not able to complete the task.

Please I need a step by step guide that tells how to get two Ubuntu's PCs in a local area network to establish file sharing.

---

### Post by uncle-c on 2009-09-09
You can use Samba. Here is a guide :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by saidbakr on 2009-09-09
Hello,

As you stated in the resource you regarded :
> 
Samba is a set of tools to share files and printers with computers running Microsoft Windows.


In my case, I don't need Microsoft Windows. I just have two PCs running Ubuntu and I need them to share files among them.

---

### Post by Iowan on 2009-09-09
You can still use Samba - but other options include NFS or SSH(FS).

---

### Post by saidbakr on 2009-09-09
I think there is something wrong! I'd like to know how to completely remove Samba and then I will try to install it again?

---

### Post by saidbakr on 2009-09-09
The Windows Network does not open. It is just prompt 
> 
[B]Unable to mount location
Failed to retrieve share list from server
[/B]

---

### Post by adm1968 on 2009-09-09
> **saidbakr said:**
> Hello,

I read more and more about getting two Ubuntu's PCs to get file sharing and I could not able to complete the task.

Please I need a step by step guide that tells how to get two Ubuntu's PCs in a local area network to establish file sharing.
[FONT="Georgia"]Take a look at [URL="http://ubuntuforums.org/showthread.php?t=1261824&highlight=sshfs"]http://ubuntuforums.org/showthread.php?t=1261824&highlight=sshfs

It is INCREDIBLY simple to make it work!
:)[/URL][/FONT]

---

### Post by alpage2 on 2009-09-09
I have always found NFS to be straightforward - works fine with my 4 linux machines on my network.

The NFS HOWTO can be viewed at the Linux Documentation Project:

[http://tldp.org](http://tldp.org)

Alan

---

