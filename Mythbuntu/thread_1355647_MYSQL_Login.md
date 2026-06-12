---
title: "MYSQL Login"
date: 2009-12-15
forum: Mythbuntu
---

### Post by rhartinger on 2009-12-15
Hi,
Im new here and want to install the 9.01 Beta. The System ask me for Mysql Login and Password. Where can I find it?

---

### Post by stevanbt on 2009-12-15
Hi,
The official release of Mythbuntu 9.10 has been out for a few months (guessing 9.01 is a typo).

Thanks, Steve.

---

### Post by rhartinger on 2009-12-15
Yes sorry

---

### Post by dgoosens on 2009-12-15
well you should have defined username and password when you installed it...
right ?

anyways... the default username should be root
and you might try to use your system password... just in case

---

### Post by SiHa on 2009-12-15
Just a thought. Are you trying to use the install disk as a Mythbuntu LiveCD?

This is only possible if you already have a functional Mythbuntu backend (server)  on the network, then the LiveCD session can be used as a remote frontend (client). In this case, you will be asked for the MySQL username and password, so that this new frontend can communicate with the backend. I think that this maybe your problem?

It may be unintentional. When I was trying out the pre-release 9.10 stuff, I found that anything between the beta and the final release (including the RC) would not install. Selecting 'Install Mythbuntu' from the boot menu, actually just ran a LiveCD session, giving you the XFCE desktop, with an 'Install Mythbuntu' icon, which does nothing. There is a MyhtTV Frontend menu option as well, I think, which will present you with the MySql questions.

If you just want to dip your toes in and give Mythbuntu a try, I'm afraid the only way is to actually install the whole thing so you have the backend/frontend on the same machine.

Maybe you should try with the final 9.10 release.

However, if all this is rubbish, and you do have a backend that you want to talk to, you will find the MySQL username / password in **/etc/mythtv/mysql.txt **on that backend.

HTH,

Simon

---

