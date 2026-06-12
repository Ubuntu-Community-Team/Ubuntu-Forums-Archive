---
title: "Simple SSH from within and outside"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by jesse.melhuish on 2011-03-10
Ok, I've read a lot about what SSH does, and how to do it on some networks, but none of them quite cover how to do it on just a network with a bunch of computers on it.  I have no server or anything, just a router with some computer connected through ethernet or wireless.  All of the Ubuntu computer have me as a user, and I want to be able to access any specific one.  How do I do this?  Also, if I'm not at home, how can I access any of my accounts from whichever computer I wish to access?

Thanks in advance!

---

### Post by cjhabs on 2011-03-10
The machines you want to ssh into must have the ssh server (sshd) running.
Example use:
ssh -X -l user remote_machine
The -X allows tunneling of windowed apps over ssh - so you can run for example:
gedit file
and it will run gedit on the remote machine and display on yours
-l user is not required if your username is valid on the remote computer

You will now be logged into the remote machine and can run both command line and windowed apps on it.
Very cool!

---

