---
title: "Samba(?) keeps reseting session"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by Gorestrasz on 2013-05-14
Hello everyone. I'm not entirely sure if my problem is categorised under this forum's section. I'm sorry if i chose the wrong one.

I'm currently working on Win7 with Ubuntu-mini (13.04) on VMWare. I've installed the following: apache 2.2.22, samba 3.6.3, ssh 5.9 and i have changed the apache's default dir from /var/www/ to /home/dem/www/ and added the changed path to smb.conf (with permissions, users, hostname and all)

The problem i'm facing is that samba seems to reset the session in about  every 1 min, making it annoying (reconnecting) to work with file editing.

In /var/log/auth.log i get this spammed all around:
May 11 13:57:40 smbd[1093]: pam_unix(samba:session): session closed for user dem
May 11 13:57:42 smbd[1094]: pam_unix(samba:session): session opened for user dem by (uid=0)
May 11 13:58:52 smbd[1094]: pam_unix(samba:session): session closed for user dem
May 11 13:58:53 smbd[1095]: pam_unix(samba:session): session opened for user dem by (uid=0)

Any idea of what might be wrong?

Thank you in advance.

Edit: I just noticed that the sshd behaves the same way like smbd when a client is connected.. so it has to be a lower-level problem than deamons themselves.

---

