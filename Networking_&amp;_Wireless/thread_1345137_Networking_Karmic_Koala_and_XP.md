---
title: "Networking Karmic Koala and XP"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by WordConjurer on 2009-12-03
Hello,

For weeks I have been trying to set up a home network, but to no avail. 

I have a 2wire router: 2701hg-b (provided by AT&T)
A Dell Desktop using Windows XP
A Dell Laptop using Karmic Koala (Ubuntu 9.10)

My Desktop and Laptop are in the same room, both connected to the router via Ethernet. (But for some reason I am starting to believe this is wrong...) 

I do not have Samba installed because last time I turned my Karmic laptop into a server, and it's my XP that is directly connected to the printer I am attempting share. 

I can see my Workgroup, and the computers within, but when I try to connect to the XP, it says "Failure to mount server list shares..." or something to that effect.

Please, any help in this matter is most appreciated. I just want to share files and the printer between these machines, but I didn't think it would be this difficult. :confused:

---

### Post by Iowan on 2009-12-03
The Samba client should already be installed in Ubuntu - so you should be able to see shares on the XP box. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that may help with some of the issues.

---

### Post by WordConjurer on 2009-12-05
> **Iowan said:**
> The Samba client should already be installed in Ubuntu - so you should be able to see shares on the XP box. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that may help with some of the issues.

Samba is not installed, according to my terminal output. And last time I installed Samba, somehow I turned this laptop into a server?, when it's my windows XP that has the printer.

---

### Post by WordConjurer on 2009-12-05
> **Iowan said:**
> The Samba client should already be installed in Ubuntu - so you should be able to see shares on the XP box. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that may help with some of the issues.


Well, I installed Samba, and for some reason I still cannot access my XP's files. I can access Ubuntu files from XP, but that's not the goal here. 

So I'm back to thinking I should have installed smbfs instead....and I don't know what to do with my Samba that's now installed.

All I am trying to do is get my Ubuntu to print from the printer used by the XP  desktop...

---

### Post by Iowan on 2009-12-05
The client *should* be pre-installed - if you wish to share files FROM Ubuntu TO Windows - the server will need to be installed. Some threads suggest that smbfs needs to be installed as well.

---

