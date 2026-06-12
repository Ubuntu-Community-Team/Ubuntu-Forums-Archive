---
title: "K9copy not working fine"
date: 2008-06-03
forum: Multimedia Software
---

### Post by papuaq on 2008-06-03
hi all,
I installed k9copy, in Ubuntu hardy. But i think there's something missing, because of the xserver. How to fix the problem??
Its showing some error msg like
> There was an error setting up tinter-process communications for KDE. the message returned by the system was:
Could not read network connectionlist.
/home/usname/.DCOPserver_usrname_0

Please check that the "dcopserver" program is running

---

### Post by papuaq on 2008-06-03
help please

---

### Post by xc3RnbFO8P on 2008-06-03
Try this:
> Re: Dcop issues :-(
by Dale Arey on Wednesday 09/Jul/2003, @09:02
I found the following issues that resolved the .DCOPserver_??__# problem.
In the directory of the user under .kde/ you'll find these files:
~socket_servername
~tmp_servername

I deleted these two files and restart kde and everything began to work as it should.
> Re: Dcop issues :-(
by Svein Liby on Thursday 24/Aug/2006, @15:23
The problem is related to a mismatch between the PID number you'll see in the task-manager for dcopserver and the number you'll see in line 2 in both the /root/.DCOPserver_boreas__0 -files, and the two similar files in your and maybe other users HOME-dir. These files can safely be deleted as dcopserver creates them at boot time if they doesn't exist, and thus fixes the problem for you. - Delete the files and reboot! 

---

