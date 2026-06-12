---
title: "Making ssh X forwarding and hibernation work together"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by B-D_ on 2009-08-14
I am using ssh X forwarding to run gVim on remote box and display the screen locally.

If I hibernate my machine for a long time SSH session times out and I have to relogin and restart the forwarded application.

The important thing to note here is that **ssh session survives short hibernation** :-k so this could be of use in solving my problem.

Network connections are stable like a rock, I'm logging into rackmounted professionally hosted server, 2 hops away from me, <1ms latency, on FTTH network, so network stability is not an issue and it can be treated like a LAN.



I see three solutions for my problem: *to be able to login today, start my forwarded app, hibernate my box, wake it up tomorrow and continue working where I left it off*.

Solution 1:

**Extend the SSH timeout so session never gets killed.**

Is this a viable option?


Solution 2:

**Create screen-ed application, kill it before hibernation, ssh into screen after hibernation and takeover the "screened" X application from remote session.**

Does screen support gui apps? Can above be summed into a simple shell script runned before/after hibernation?


Solution 3:

**Create virtual X server and login into via VNC.**

I don't like this solution because I have to drag whole desktop with it. Also it makes window resizing, copy/paste and similar operations complicated.

---

### Post by wojox on 2009-08-14
Solution 1.
Try editing /etc/ssh/ssh_config
Look for ConnectTimeout

---

### Post by B-D_ on 2009-08-14
On local box or remote box?

---

### Post by B-D_ on 2009-08-14
I set the ConnectTimeout to 99999 locally, but won't server's sshd still kick me out after period of inactivity?

---

