---
title: "What port does Samba communicate on"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2009-09-23
Trying to share with a Windows Box with Norton Security Suite. The computer don't even appear on the network. I'm sure we just need to open a port on the firewall. Never worked with Norton's Firewall. :confused:

---

### Post by yabbadabbadont on 2009-09-23
According to [http://www.oregontechsupport.com/articles/samba.php](http://www.oregontechsupport.com/articles/samba.php) it uses 137-139 and 445.

---

### Post by theozzlives on 2009-09-24
> **yabbadabbadont said:**
> According to [http://www.oregontechsupport.com/articles/samba.php](http://www.oregontechsupport.com/articles/samba.php) it uses 137-139 and 445.

Thanks I'll try to open those ports, it's my neighbor's Rent-A-Center computer. How do I restrict his access to just ozzie-laptop/home/ozzie/public and not the whole network?

---

### Post by JKyleOKC on 2009-09-24
> **theozzlives said:**
> How do I restrict his access to just ozzie-laptop/home/ozzie/public and not the whole network?
It's done in the smb.conf file, by creating a share for him to use. You can call it "public" or use his name for it, as you prefer. For the content of that share, copy what's in the default "homes" share, except change the path to "/ozzie-laptop/home/ozzie/public" and that'll do it. Be sure to shut down Samba and re-start it after saving the smb.conf file, to put the changes into effect.

---

### Post by theozzlives on 2009-09-25
> **JKyleOKC said:**
> It's done in the smb.conf file, by creating a share for him to use. You can call it "public" or use his name for it, as you prefer. For the content of that share, copy what's in the default "homes" share, except change the path to "/ozzie-laptop/home/ozzie/public" and that'll do it. Be sure to shut down Samba and re-start it after saving the smb.conf file, to put the changes into effect.

[http://ubuntuforums.org/showthread.php?t=1274950]("http://ubuntuforums.org/showthread.php?t=1274950")

[https://wiki.ubuntu.com/LoCoTeamHowto]("https://wiki.ubuntu.com/LoCoTeamHowto")

---

### Post by theozzlives on 2009-09-30
> **JKyleOKC said:**
> It's done in the smb.conf file, by creating a share for him to use. You can call it "public" or use his name for it, as you prefer. For the content of that share, copy what's in the default "homes" share, except change the path to "/ozzie-laptop/home/ozzie/public" and that'll do it. Be sure to shut down Samba and re-start it after saving the smb.conf file, to put the changes into effect.

So in otherwords, I need create him as a user on my system to restrict access?

---

