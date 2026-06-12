---
title: "could not connect ssh server"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by ssilayaraja on 2008-12-05
Hi all,
      This is my first question in this forum.i hope u will give best solution for my problem.

i have installed ubuntu8.10 in my system and and i have installed openssh-server i can login ssh locally throgh this command 
> #ssh localhost

but i could not login from another linux system in my network. i getting following error message
> #ssh 180.192.6.165
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
03:82:ae:f4:b1:30:a3:b0:f9:d2:8f:99:36:e1:25:8d.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:16
RSA host key for 180.192.6.165 has changed and you have requested strict checking.
Host key verification failed.


even i deleted the kown_hosts file from /root/.ssh folder
i am getting the same error

plz give me a solution

---

### Post by Iowan on 2008-12-05
On which machine did you delete the *known_hosts* file? I presume it *should* be on the client(???).

---

