---
title: "ssh problem"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by antmenj on 2011-05-05
I'm having trouble getting ssh to work.

I have a smoothwall box I can ssh into via places --> Connect to server.  I have built a ipcop box to replace it with the same ip but can't seem to ssh into it.

I get this when I try the following at the terminal:

```
~$ ssh -p 222 root@192.168.2.1
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
888888888888888888888888 <-- code edited.
Please contact your system administrator.
Add correct host key in /home/name/.ssh/known_hosts to get rid of this message.
Offending key in /home/name/.ssh/known_hosts:2
RSA host key for [192.168.2.1]:222 has changed and you have requested strict checking.
Host key verification failed.

```

Is there a password key (RSA key?) for that stored in my computer that I need to erase and if so how?  Or what should I be doing?

--------------------edit

Have renamed /home/name/.ssh/known_hosts and it now works.  Is this dangerous8-[

---

### Post by mhgsys on 2011-05-05
nah, you can safely remove or rename the  /home/username/.ssh/known_hosts file.
It will just ask you for (new) permission to connect to the remote host after removing/renaming the file and create the file again

---

### Post by antmenj on 2011-05-05
Cool:D  Thanks.

---

