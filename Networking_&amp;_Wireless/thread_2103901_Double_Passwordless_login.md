---
title: "Double Passwordless login"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by tuek on 2013-01-11
I am having problem with passwordless login. Here is the situation:

There are 3 machines, LAP (My laptop running ubutnu 12.04), OFF (office machine running Ubuntu 10.04) and SC (a supercomputer)

I can passwordless login from OFF to SC. But when I connect to OFF from LAP and then try to connect to SC from OFF using ssh, the machine ask for my password. 

I have another computer/s OFF2 (running Red Hat, another Ubuntu 10.04), and if I connect from LAP to OFF2, then I can connect from OFF2 to SC without password. Any help why I can't do the same from OFF. 

Thanks a lot.

---

### Post by SlugSlug on 2013-01-14
This is the guide I use for ssh keys

[http://paulkeck.com/ssh/](http://paulkeck.com/ssh/)

---

### Post by efflandt on 2013-01-15
Assuming you are using keys, it depends if you have **ForwardAgent yes** for that Host (or for catchall Host *) in ~/.ssh/config and whether **ssh-agent** is running on the computer you are on.  Typically in X ssh-agent is running, but it is probably not running by default if you launch ssh from a text console.

If you use any keys without a pass phrase, you should really limit what commands can be run with that key.  Otherwise if someone gets that private key, without any password they could do anything on the system that you can do.

Also once you have your keys on a destination it is best to set /etc/ssh/sshd_config to use keys only and not allow password login to avoid password crack attempts (especially if open to internet or unsecured wireless):

PermitEmptyPasswords no
PasswordAuthentication no

---

### Post by tuek on 2013-01-22
Thanks SlugSlug and efflandt.

I will try these solutions and post the results.

TuEk

---

