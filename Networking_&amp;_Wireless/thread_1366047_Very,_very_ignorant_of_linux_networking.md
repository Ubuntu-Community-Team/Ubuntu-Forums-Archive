---
title: "Very, very ignorant of linux networking"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by amille41 on 2009-12-28
Ok, so I've got a pretty wide range of systems on my network that I'd like linux to talk to. The first task would be a linux to linux connection (a Kubuntu 9.10 x64 to a SuSe 11.2 x64), and later a linux to windows XP.

I know you're supposed to find the drive or partition and mount it through samba under linux, but more than that I really don't know what to do or how to start.

Hey, and thanks for all the help! Even pointing me to a general FAQ or something like that would be great!

---

### Post by griffinjones on 2009-12-28
Mount the system(s) on the network and attempt to auto recognize them via the GRUB network (I can't remember) booter.

That's my first try.

---

### Post by amille41 on 2009-12-28
But how do I mount them on the network? I can ping their IP addresses and the computers respond fine.

---

### Post by felipe51 on 2009-12-28
> **amille41 said:**
> Ok, so I've got a pretty wide range of systems on my network that I'd like linux to talk to. The first task would be a linux to linux connection (a Kubuntu 9.10 x64 to a SuSe 11.2 x64), and later a linux to windows XP.

I know you're supposed to find the drive or partition and mount it through samba under linux, but more than that I really don't know what to do or how to start.

Hey, and thanks for all the help! Even pointing me to a general FAQ or something like that would be great!


first try right-click your directory and then "Sharing options". It will help you out to install the necessary files if needed. 
Then on the other computer just try to access your files through the filemanager, look for names like networking, connect to server, etc.

best regards

---

### Post by Iowan on 2009-12-28
It's a bit involved, but [this]("http://ubuntuforums.org/showthread.php?t=288534") one may help.

---

### Post by amille41 on 2009-12-29
> **Iowan said:**
> It's a bit involved, but [this]("http://ubuntuforums.org/showthread.php?t=288534") one may help.

Haha, thanks for the link. I'm a student on winter break right now, so I'll give that a shot and tell you how it goes.

UPDATE: Ok, I've followed through the tutorial you linked, and I'm setting it up for permanent mounting with smbcredentials. When I execute "sudo mount -a" at the end of the tutorial, I get this message:


amiller@p6:~$ sudo mount -a
mount error(13): Permission denied
Refer to the mount.cifs(8 ) manual page (e.g. man mount.cifs)

Any idea what could be up?

---

