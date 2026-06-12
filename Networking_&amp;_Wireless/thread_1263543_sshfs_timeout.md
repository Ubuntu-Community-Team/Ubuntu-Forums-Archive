---
title: "sshfs timeout"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-09-11
Hi, question: Whenever I mount a remote filesystem via sshfs, it timeouts if I don't use it for some time.

Now the problem is, sshfs doesn't disconnect, but it doesn't work anymore once it timeouted.

You also cannot just reconnect. You first have to pkill sshfs and then restart it.

Now I've never encountered the timeout in the local network, so I suppose this is only over internet.

Can I configure the timeout somewhere, possibly to never, or tweak the config somewhere, or is this a bug in sshfs?

---

### Post by WitchCraft on 2009-09-13
bump.

---

### Post by WitchCraft on 2009-09-16
bump

---

### Post by WitchCraft on 2009-09-18
bump.

---

### Post by WitchCraft on 2009-10-03
bump.

---

### Post by WitchCraft on 2009-10-11
bump.

---

### Post by WitchCraft on 2009-10-15
bump.

---

### Post by simonz on 2009-11-24
I am having the same problem.  Running Xubuntu 9.10

Bump.

---

### Post by simonz on 2009-11-25
[http://www.cyberciti.biz/tips/open-ssh-server-connection-drops-out-after-few-or-n-minutes-of-inactivity.html]("http://www.cyberciti.biz/tips/open-ssh-server-connection-drops-out-after-few-or-n-minutes-of-inactivity.html")

On the client side I made the following changes.  It no longer disconnects.

Another option is enable ServerAliveInterval in the client's (your workstation) ssh_config file.
# vi /etc/ssh/ssh_config
Append/modify values as follows:
ServerAliveInterval 15
ServerAliveCountMax 3

simonz

---

### Post by WitchCraft on 2009-11-26
> **simonz said:**
> [http://www.cyberciti.biz/tips/open-ssh-server-connection-drops-out-after-few-or-n-minutes-of-inactivity.html]("http://www.cyberciti.biz/tips/open-ssh-server-connection-drops-out-after-few-or-n-minutes-of-inactivity.html")

On the client side I made the following changes.  It no longer disconnects.

Another option is enable ServerAliveInterval in the client's (your workstation) ssh_config file.
# vi /etc/ssh/ssh_config
Append/modify values as follows:
ServerAliveInterval 15
ServerAliveCountMax 3

simonz

Very good, thank you!

---

