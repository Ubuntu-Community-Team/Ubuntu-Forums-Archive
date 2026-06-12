---
title: "ssh keys work with on but not another server"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by daveuu on 2009-09-15
Hi

I'm after trouble-shooting advice for the following problem:

I have a client that can log in via ssh with dsa keys to one server but not another (using the same keys - the password is prompted instead). On each server the /etc/ssh/sshd_config are identical including:

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys2

~./ssh/authorized_keys2 are identical on both servers. All three are Jaunty, OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007

The problem server did have lsh-server installed which I removed but that didn't help. Other differences: the problem server user@server:~$ prompt is in black text but in green on the passwordless server; the former is 32-bit 2.6.29-1-netbook #0array1 SMP Eeebuntu the latter 2.6.28-13-generic #45-Ubuntu SMP; they are on different networks via different network interface cards.

Help! I'd like keys to work with both but I've run out of ideas.

DaveUU

---

### Post by grotesk on 2009-09-15
Some thoughts:
[LIST]
[*]~/.ssh/authorized_keys2 is generally deprecated for recent versions of OpenSSH. Typically, the default file is simply ~/.ssh/authorized_keys.
[*]Be sure that the file ~/.ssh/authorized_keys and the directory ~/.ssh are owned by the user connecting to the system and are chmod 0700 and 0600 respectively.
[*]Check /var/log/secure and /var/log/messages for details on failed logins; OpenSSH's logging is generally outstanding. Feel free to paste relevant log lines here for further help.
[/LIST]

---

### Post by daveuu on 2009-09-16
Your suggestion re ownership set me on the right trail.

Although the owner and mode were correct the groups were a bit messed up. It worked nicely after a chgrp -R from the home folder (.ssh and authorized_keys2 being the ones that made the difference no doubt).

Thanks

---

