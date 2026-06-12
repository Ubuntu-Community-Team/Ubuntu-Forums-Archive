---
title: "Passwordless SSH Doesn't Work"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2009-03-22
Okay, so here's everything I've done and all the information I've gotten.

I have a desktop and a server, no prob.  Desktop is intrepid, server is mythbuntu 8.10.  I can ssh w/ a password to the server no problem.  I'm trying to setup no password login and have run:


```
$ mkdir -p $HOME/.ssh
$ chmod 0700 $HOME/.ssh
$ ssh-keygen -t dsa -f $HOME/.ssh/id_dsa -P ''

```

This creates two files, id_dsa and id_dsa.pub.  I copied the .pub file to my server and then, on the server

```
$ cat id_dsa.pub >> $HOME/.ssh/authorized_keys2
$ chmod 0600 $HOME/.ssh/authorized_keys2

```

Also done

```
$ cat id_dsa.pub >> $HOME/.ssh/authorized_keys
$ chmod 0600 $HOME/.ssh/authorized_keys

```

Just to be sure.  Then to ssh from the Desktop to the server I run

```
$ ssh -i $HOME/.ssh/id_dsa 192.168.0.102 // I have the same username on the desktop as the server

```

But it still asks me for a password.  Even after totally restarting the server to make sure all the settings are applied.  Any ideas?  Thanks!

Edit:
Attached are my /etc/ssh/ssh_config and sshd_config files, I'm pretty sure they're configured properly, but lemme know if anybody sees anything.

---

### Post by kevdog on 2009-03-23
Just to be sure. Then to ssh from the Desktop to the server I run

Code:

$ ssh -i $HOME/.ssh/id_dsa server


Wouldnt this be ssh -i .... <user>@<ip_address>

Fill in the blanks where appropriate!

---

