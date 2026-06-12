---
title: "NX Client - ssh: connect to host port 22: Connection refused"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by th0r_ on 2010-07-29
I have a Windows machine on which NX Client has been installed. I wanted to test if I could access my Ubuntu box. The Ubuntu Box has NX Server, Node and Client installed. When I try to log in from the Windows machine using NX Client with my Ubuntu username and password I get an error connection refused.

The following service is running:
OpenBSD Secure Shell server sshd

How can I resolve the issue? Please let me know if you guys need any additional information.

---

### Post by marc.verwerft on 2010-07-30
From your post it seems you only tried connecting to your Linux server using the NX client.
Can you log on from your windows box to the server using ssh (maybe even with -vvv)? If that works then your network setup is fine and you should concentrate on NX settings.
Otherwise try ssh from your server to your server. This will check your server's ssh installation.

Since Windows doesn't have a native SSH client, you should probably install cygwin or similar.

Regards,

Marc

---

### Post by th0r_ on 2010-08-01
> **marc.verwerft said:**
> From your post it seems you only tried connecting to your Linux server using the NX client.
Can you log on from your windows box to the server using ssh (maybe even with -vvv)? If that works then your network setup is fine and you should concentrate on NX settings.
Otherwise try ssh from your server to your server. This will check your server's ssh installation.

Since Windows doesn't have a native SSH client, you should probably install cygwin or similar.

Regards,

Marc

Thanks Marc.

I did try logging in with putty. Was successful.

Any suggestions?

---

### Post by marc.verwerft on 2010-08-01
Look at the sshd log file (probably /var/log/auth.log) - maybe that can indicate what's wrong.
Possibly you have to increase the log level - see [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Log%20More%20Information]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Log%20More%20Information")

---

