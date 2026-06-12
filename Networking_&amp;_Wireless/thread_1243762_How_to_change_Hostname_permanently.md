---
title: "How to change Hostname permanently?"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by mukul_s on 2009-08-18
Hi,

I am running Kubuntu Jaunty. How can I change my hostname permanently so that people can access my shared folders, on intranet, by my hostnames??

---

### Post by spd106 on 2009-08-18
It sounds like you're trying to connect to a Windows network and they use their own form of name resolution rather than DNS. You'll probably want to install Samba and Winbind, there are various tutorials out there to help you.

E.g. [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)


Otherwise, you can do it from a terminal with the hostname command, see **man hostname**

---

### Post by mukul_s on 2009-08-18
I am actually trying to host a "Kablink Teaming" for my small team.
So there's no involvement of windows. It's all Debian systems only.

---

### Post by Iowan on 2009-08-18
IF you change the hostname, change */etc/hosts* at the same time - otherwise **sudo** complains.

---

### Post by mukul_s on 2009-08-18
> **Iowan said:**
> IF you change the hostname, change */etc/hosts* at the same time - otherwise **sudo** complains.
But I read somewhere that doing that will cause problem with KDE. So I need to change in all the files in ~/.kde

---

### Post by Iowan on 2009-08-19
Once again, I missed the [kubuntu] tag... one of the versions I haven't tried. Sorry for any misdirection.

---

### Post by mukul_s on 2009-08-20
C'mon guys, are there no Kubuntu users who ever changed the "hostname" of their machines?
What about support from Dev team...
Help <screaming>

---

