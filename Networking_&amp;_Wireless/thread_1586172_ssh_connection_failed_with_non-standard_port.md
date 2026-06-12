---
title: "ssh connection failed with non-standard port"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by krohn on 2010-10-01
I recently had Ubuntu Desktop installed on a machine and turned it into a server. I had OpenSSH installed using a non-standard port and everything worked fine.
 
Installed Ubuntu Server 10.04 64-bit today. Re-installed OpenSSH and changed the port to a non-standard port, say 3022 (did this by editing the /etc/ssh/ssh_config file). This command gives me a "connect to host localhost port 3022: Connection refused":
 
ssh -p 3022 username@localhost
 
However, if I change it back to port 22, this works fine:
 
ssh username@localhost
 
I'm borderline new at this and not sure what the problem is. Any advice is appreciated. Thanks.

---

### Post by SeijiSensei on 2010-10-01
You need to make the change in /etc/ssh/sshd_config on the server.  /etc/ssh/ssh_config contains the client settings.

---

### Post by psusi on 2010-10-01
And you have to restart the server for it to read the new settings.

---

### Post by krohn on 2010-10-01
> **SeijiSensei said:**
> You need to make the change in /etc/ssh/sshd_config on the server. /etc/ssh/ssh_config contains the client settings.
 
Very nice catch.  I was editing the wrong file.  Made the change and it worked great.  Thanks for the help.

---

### Post by Iowan on 2010-10-01
You can mark the thread [SOLVED] using the Thread Tools pulldown.
(Select "Mark this thread as solved")  :)

---

