---
title: "NFS + Autofs: Challenging question"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Savita Eli on 2009-08-03
Hi,

I am trying to [COLOR=Blue]automount[/COLOR] NIS user's home dirs from server to client.
[COLOR=Red]The nisuser's home dir on server is in /myhome/users/nis1, /myhome/users/nis2 & so on.
The need is to mount it in client as /myhome/nis1.[/COLOR]

How to [COLOR=Blue]automount using autofs[/COLOR] this multi-dir onto client in single home dir.

Here are the details:
1) NFS share: /myhome/users  *(rw,sync)

2) The home dir on server is in: /myhome/users/nis1

3) The home dirs of NIS users on client should be in : /myhome/nis1, /myhome/nis2 & so on.

4) Only the home dir of the user who gets logged in should be mounted,not others.

Ex: If nis1 logs in, only nis1's home dir should be mounted as /myhome/nis1 on client & not all the users home dir's.

---

### Post by Savita Eli on 2009-08-03
The auto.* entries which i tried and did not work:

/etc/auto.master :
------------------------------------
/myhome  /etc/auto.mhome

/etc/auto.mhome :
-------------------------------------
*       -fstype=nfs     172.168.1.132:/myhome/users/&

And when i restart autofs & login, I get the following error & placed in"/" :

[root@ftprhel ~]# ssh -l nis1 172.168.1.131
nis1@172.168.1.131's password: 
Creating directory '/myhome/users/nis1'.
Last login: Sun Aug  2 19:39:51 2009
Could not chdir to home directory /myhome/users/nis1: No such file or directory
-bash-3.2$ 


Plz help me asap.I am looking for the solution from past many days..

Cmon ppl... try it out.

---

