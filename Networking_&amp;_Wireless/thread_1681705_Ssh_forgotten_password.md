---
title: "Ssh forgotten password"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by superninja on 2011-02-04
I am using 10.04 ubuntu and I have forgotten my password to login to a ssh tunnel. It is not the root password on my computer. 

Is there any way I can find the password out, change it, or just start over and create a new one?

I know it isn't a connection problem because I can't login to ssh from localhost either.

I've tried reinstalling ssh too.

Thank you :)

---

### Post by Iowan on 2011-02-04
On my machines, the SSH password is simply the user password. Root might be able to reset the password - or it can simply be deleted, and then reset by the user... if you have root access to the machine.

---

### Post by superninja on 2011-02-04
I have complete access to the machine. The password isn't the same as the root (the only user) password though. I have tried looking through some of the config files in /etc/ssh but I can't find anything that has to due with a password other than "PasswordAuthentication", which is set to no but it still requires a password...

---

### Post by superninja on 2011-02-11
Can anyone help? :)

---

