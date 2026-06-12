---
title: "problem in configuring ssh server"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by piyush.neo on 2010-09-28
i have installed openssh-server on my ubuntu 10.04 machine.Now when i am trying to connect it i am getting the following message and the connection terminate...
```
iyush@piyush-laptop:~$ ssh piyush@localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is f5:aa:5c:1e:0b:00:48:05:07:9f:f5:11:e4:fa:85:78.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
piyush@localhost's password: 
Linux piyush-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

12 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

```Any idea..?

---

### Post by SeijiSensei on 2010-09-28
Do you not get a terminal prompt after that?  Is that the problem?  What you've posted here is the correct result after logging in.  You'd see the same result if you booted into a text-mode session rather than the graphical desktop and logged in there.

---

### Post by piyush.neo on 2010-09-28
Sorry..its working..its my machine so i realized it latter that i am connecting to my machine...

---

