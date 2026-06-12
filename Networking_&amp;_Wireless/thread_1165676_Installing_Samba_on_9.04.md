---
title: "Installing Samba on 9.04"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by moebob24 on 2009-05-20
Ok, I have done this before but I haven't worked with my Linux box in about a year and just reformatted to 9.04. I am having some problems getting samba up and running again so I can connect to and use my XP to Ubuntu share folders. 

If someone could type out a step by step on installing samba and connecting to XP for file transfer. 

Thanks.

---

### Post by cariboo on 2009-05-20
Ubuntu connects to windows shares by default, you don't need to install samba. The only time you need samba if you are sharing files the other way eg: Ubuntu-->Windows. Just make sure both computers are in the same workgroup. Ubuntu defaults to WORKGROUP, while depending on what version of Windows you are using. The Home versions use MSHOME while the Pro, Office and Ultimate versions use WORKGROUP.

If you already have samba installed the easiest way to change the workgroup is to edit it in /etc/samba/smb.conf.

---

### Post by moebob24 on 2009-05-21
I am trying to share both ways.

---

### Post by Iowan on 2009-05-21
You'll probably want to install samba-server (called **samba** in Synaptic's package list).  Dunno if **smbfs** needs to be added, too. After that, the setup fun begins.  ;)

---

### Post by superprash2003 on 2009-05-22
heres a small guide [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by swerdna on 2009-05-22
If you post here your Samba config file, we could advise you better. You can open it with this command:```
gksudo gedit /etc/samba/smb.conf
```
and then copy/paste it here.

---

