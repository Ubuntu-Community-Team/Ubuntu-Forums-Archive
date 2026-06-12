---
title: "Trying to set ssh passwordless connection"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by ^_Pepe_^ on 2010-01-12
Hi all,

I'm just trying to connect passwordlessly to my server, and following this howto, 


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1075871](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1075871)

I generate my keygen in my laptop, and copy it to my server with

scp ~/.ssh/id_rsa.pub [email]user@remote.server.com:.ssh[/email]/authorized_keys

After this, I restart ssh server, and....

Nothing happens: ssh remote.server.com or ssh [email]user@remote.server.com[/email] asks me for the password.

Where can I find any information about what I'm doing wrong?

Thanks in advance

---

### Post by puppywhacker on 2010-01-12
Look at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

when you want to test your setup use "ssh -v [email]user@remote.server.com[/email]" because then you will see the debug information about when it tries (or not) to use the publickey. Also important is the file permissions, because the ssh server refuses to use keys that are world readable. Also the sshd_config should support have public key as a method enabled

---

### Post by ^_Pepe_^ on 2010-01-12
Hi!

Thanks again!

This wiki page is gold to me :)

ssh-copy-id <username>@<host> worked ok, but I also have to chmod ~/.ssh. I'm not sure what it was.

But no, it works!!

Thanks!

---

