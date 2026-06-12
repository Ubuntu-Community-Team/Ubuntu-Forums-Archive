---
title: "Selecting Cipher for SSH when &quot;Connect to server&quot;"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by aneganov on 2009-10-19
Hi,

I want to select blowfish chipher for sshfs communications in Ubuntu when mounting remote server via ssh via Connect To Server feature.
How to do this?

thanks in advance

---

### Post by aneganov on 2010-01-30
up up up

---

### Post by Lars Noodén on 2010-01-31
[sshfs](http://linux.die.net/man/1/sshfs) should be able to accept any of the [configuration options](http://linux.die.net/man/5/ssh_config) available to ssh.  The full list is found in [ssh_config(5)](http://linux.die.net/man/5/ssh_config), but one guess would be like this:

```

sshfs -o "Ciphers=*blowfish-cbc*" ...

```

Why do you want to force only blowfish?   

The default is to try the following in order of preference: aes128-cbc, 3des-cbc, blowfish-cbc, cast128-cbc, arcfour128, arcfour256, arcfour, aes192-cbc, aes256-cbc,aes128-ctr, aes192-ctr, and aes256-ctr.

---

