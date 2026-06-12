---
title: "sshd running but can't connect?"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by DiagonalArg on 2013-06-19
Hi all.  I did the following at a terminal (ctl-alt-F1):

```
sudo aptitude install openssh-server
sudo /etc/init.d/ssh restart
```

```
pgrep sshd
``` does give me a process id, but when I try ssh'ing into the machine, I just get a time-out.  

Thoughts?

(I should explain that I have a machine with some kind of video issue.  I can input to this terminal, but I can hardly see the output.  I am trying to get into the machine from another via ssh from my laptop.  Also, I can't reboot since I'm trying to get some work back.)

----------

Ubuntu 12.04

---

### Post by Toz on 2013-06-19
Firewall?

What does the following return?
```
sudo ufw status verbose
```

Also,
```
sudo netstat -tupan | grep LISTEN
```

---

### Post by DiagonalArg on 2013-06-19
Hm.  Ok, good point. I'll turn ufw off, since I can't actually read the terminal output....

---

### Post by Toz on 2013-06-19
> **DiagonalArg said:**
> Hm.  Ok, good point. I'll turn ufw off, since I can't actually read the terminal output....

You could also allow ssh through instead of disabling the firewall:
```
sudo ufw allow ssh
```

---

### Post by DiagonalArg on 2013-06-19
It worked!!  I can log in.

Now I've got a gedit running over there and I really need to save the (as yet unsaved) file before rebooting.

Unless you have bright ideas, I'll just start another thread.

(Edit: I meant to say, Thanks!)
(Edit: Can't figure out how to mark "solved" - it's not under Thread>>Tools the way it's supposed to be, and I am logged in....)

---

