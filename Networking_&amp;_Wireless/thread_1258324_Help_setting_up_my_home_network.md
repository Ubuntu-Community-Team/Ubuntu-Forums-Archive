---
title: "Help setting up my home network"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by noelc on 2009-09-04
Hi,

I have two desktops both run ubuntu9.04 and both are wired to the same router for access to the web. I want to network these I can transfer files between them while also installing Synergy as I only have one key board and mouse.

I,m struggling to find out how to do this, Can you help.

---

### Post by bear24rw on 2009-09-04
To transfer files you have a bunch of different options one of which is ssh:

on both computers

$ sudo aptitude install openssh-server filezilla

then you can use filezilla to connect to the other computer or instead of filezilla you can go to "Places > Connect to server" and enter the ip of the other computer and it will mount the other computer as a folder on your desktop

---

### Post by noelc on 2009-09-05
> **bear24rw said:**
> To transfer files you have a bunch of different options one of which is ssh:

on both computers

$ sudo aptitude install openssh-server filezilla

then you can use filezilla to connect to the other computer or instead of filezilla you can go to "Places > Connect to server" and enter the ip of the other computer and it will mount the other computer as a folder on your desktop

OK Thanks is filezilla an icon? Is so would you know the path as I can not locate it?

Thanks

---

### Post by shredder12 on 2009-09-05
> **noelc said:**
> OK Thanks is filezilla an icon? Is so would you know the path as I can not locate it?

Thanks

Filezilla is a graphical ftp client..
you can find it at Applications -> internet -> filezilla

for this you will probably need to install a ftp server..
you can try installing vsftpd

try this guide to help u install vsftpd [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)


> **noelc said:**
> Hi,

I have two desktops both run ubuntu9.04 and both are wired to the same router for access to the web. I want to network these I can transfer files between them while also installing Synergy as I only have one key board and mouse.

I,m struggling to find out how to do this, Can you help.

Have u already installed synergy??
If not then you can try this how to
[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

Hope this helps

---

### Post by bear24rw on 2009-09-05
> **shredder12 said:**
> Filezilla is a graphical ftp client..
you can find it at Applications -> internet -> filezilla

for this you will probably need to install a ftp server..
you can try installing vsftpd



It is also an sftp client so it will work when connecting to ssh..

---

