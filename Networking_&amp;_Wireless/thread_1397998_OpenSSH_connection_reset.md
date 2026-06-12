---
title: "OpenSSH connection reset"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by DigitalKhaos on 2010-02-03
Greetings folks,

I was hoping to find some help with a problem I am having.  I am running Ubuntu (Karmic) and did the command: "sudo apt-get install ssh", In an attempt to download, install and setup OpenSSH.

This installed both the client and server and during setup actually brought the daemon up and running as well.

I then attempt: "ssh <myusername>@localhost"
and it prompts me with a password.  I enter the password, hit enter and immeditaly see the following results:

Read from remote host localhost: Connection reset by peer.
Connection to localhost closed.

I'm fairly certain that it is not on the client end as I can connect to other machines through ssh.

I've tailed all the logs, messages, dmesg etc and nothing seems to be out of order, or even remotely related to shh or connections etc.

My desktop machine had no (as in zero) issues installing and setting up OpenSSH, and connections can come and go as normal.

Has anyone ever seen this before?
It would be great for any insight whatsoever,

Thanks All!

---

### Post by johnson.d on 2010-02-04
Can you paste the output of the command 'ssh -vvv <username>@localhost' which gives the verbose output of ssh trying to connect the localhost? This may give some useful pointers.

---

### Post by Iowan on 2010-02-04
What's in */etc/ssh/sshd_config *? Have you tried it just: "ssh localhost"?

---

### Post by sarraceno on 2010-02-05
Hi!
 
Could reading this [http://ubuntuforums.org/showthread.php?t=1399032](http://ubuntuforums.org/showthread.php?t=1399032) helps finding the root cause?
 
There are a couple of situations for "Connection reset by peer".
 
I do not know how to deal with it, but I believe that is some network issue. If from my ubuntu or from network is on of the questions...
 
Thanks!

---

