---
title: "how to ssh w/out password as different user"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by j_galt on 2010-12-04
I've made this work before, but for the life of me I cannot get it to work right now, despite ~ an hour of searching forums & Google - please help.

I'd like to ssh into an Ubuntu server as user "sysadmin", from a Kubuntu client when logged in as user "dan", without using a password.

ssh from client (as dan) to server (as dan) (w/out a password) works perfectly.

ssh from client (logged in as dan) to server (trying to access user sysadmin directly) fails, with the message "permission denied (public key)"

I've tried using the id_rsa.pub key generated as dan (copied to ~sysadmin/.ssh/authorized_keys on the server).  I've tried generating a second id_rsa-sysadmin.pub key, copying it to the ~sysadmin/.ssh/authorized_keys file on the server, then using <ssh -i .ssh/id_rsa-sysadmin sysadmin@server>.

The permissions for ~sysadmin/.ssh are 700, and for ~sysadmin/.ssh/authorized_keys are 600 (both on the server...).

What am I doing wrong?

Thanks in advance for any help you can provide.

---

