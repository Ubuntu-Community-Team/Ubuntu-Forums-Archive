---
title: "Remote shell - help"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by pindari on 2009-01-28
I am trying to execute a command on a remote machine without being prompted for a password. The user account exists on both machines with the same password and I created a .rhosts file in the home directory of the user on the remote machine with the FQDN of the local machine, but still I am asked for a password ... when I enter the password the command is executed, but I need to do this without the password prompt.

Any help appreciated ...

user1@local:~$ *ssh user1@192.168.2.39 ./run_me*
**user1@192.168.2.39's password: ************
user1@local:~$

---

### Post by Javich on 2009-01-28
You can set a key in the remote server, so you add a parameter in your ssh command to use that key to access that server. You can get the idea from here: [http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/](http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/)

---

