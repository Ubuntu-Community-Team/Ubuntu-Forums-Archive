---
title: "Combine Rsync and SSH Pass Problem"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by indrao88 on 2011-05-13
I made a script to backup file from each host with general password in local network. This script using SSH Pass and Rsync with this syntax:

[LIST]
[*]rsync --rsh="sshpass -p password ssh -l root" host:path destinationpath
[/LIST]
Everything is okay under 9.10 version until I migrate to Ubuntu 11.04, there is always give an error:

[LIST]
[*]rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(541) [Receiver=3.0.7]
[/LIST]
I am using bash version: GNU bash, version 4.2.8(1)-release (i686-pc-linux-gnu) and 2.6.38-8-generic kernel

Please Help


Regards,
Indra

---

### Post by Lars Noodén on 2011-05-13
Here are some notes on using [rsync and openssh](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup) for backup.

I'd recommend using key-based authentication instead of storing the password in a script.

---

### Post by indrao88 on 2011-05-14
Sorry for late reply, thanks for your advice Lars. Actually i still more suit for this password method on my system. Do you know how to solve it?

---

### Post by Lars Noodén on 2011-05-14
[sshpass](http://manpages.ubuntu.com/manpages/natty/en/man1/sshpass.1.html) is new to me and I am not able to get it to function as described in your example.  It just sort of sits there, without actually logging in, until I break the connection.

The ways I've used rsync are described in the [cookbook of OpenSSH](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup)

---

