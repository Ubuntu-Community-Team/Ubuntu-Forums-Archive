---
title: "Have a problem with passwd"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by jaiganeshc on 2009-03-12
I am trying to change the "root" passwd. I got the below message, but i couldn't able change.
passwd: password updated successfully

---

### Post by cantormath on 2009-03-12
:~$ sudo -s
your password

:~$ passwd

you shouldnt set a root users password, you are better off using sudo.

---

### Post by jaiganeshc on 2009-03-12
I have given a command in Ubuntu Server 8.10: sudo passwd root
But i couldn't..

ubuntu@gftp-server:~/testftp$ sudo -s
[sudo] password for ubuntu: 
root@gftp-server:~/testftp# passwd
passwd: password updated successfully
root@gftp-server:~/testftp#

---

### Post by jaiganeshc on 2009-03-12
I have given the below commands.

ubuntu@gftp-server:~/testftp$ sudo -s
[sudo] password for ubuntu: 
root@gftp-server:~/testftp# passwd
passwd: password updated successfully
root@gftp-server:~/testftp#

---

### Post by cantormath on 2009-03-12
and what is the problem?

---

### Post by jaiganeshc on 2009-03-12
"root" password not been updated.

---

