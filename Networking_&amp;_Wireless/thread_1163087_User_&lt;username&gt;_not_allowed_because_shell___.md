---
title: "User &lt;username&gt; not allowed because shell   does not exist"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by mowgli24 on 2009-05-18
Hi All,

        I have a system with Ubuntu 8.04 installed in it and it is a client to a NIS server. Remote login to this client is failing and when I track the /var/log/auth.log file, I get the following error message(immediately when I ssh from another machine - even before entering the password)

<Date> <machine_name> sshd[8254]: User <username> not allowed because shell   does not exist
<Date> <machine_name> sshd[8254]: Failed none for invalid user <username> from <IP where I try ssh> port <port#> ssh2

I am not sure if I am missing some setting. None of the users who have their account in the NIS server is able to login to this NIS client.

Shell for my username in the NIS server /etc/passwd file shows /bin/tcsh and I have tcsh in my client as well.

Regards,
Mowgli

---

