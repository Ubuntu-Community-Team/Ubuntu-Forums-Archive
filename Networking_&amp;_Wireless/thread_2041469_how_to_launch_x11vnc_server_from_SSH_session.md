---
title: "how to launch x11vnc server from SSH session"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by JCPTY on 2012-08-12
Hello Guys,

I am connected from my windows 7 laptop to another laptop running ubuntu 12.04 through ssh.

It is my understanding that i could start my x11vnc server application remotely from my ssh session and then i should be able to connect from vnc viewer on my windows 7 system.

Did anyone here knows how to do this or the commands that i need to run in the SSH session?

Appreciate your support!

JC

---

### Post by bakegoodz on 2012-08-12
On Linux it is easy
```

vncviewer -via user@DomainorIP.com LanComputerName:0
```
On Windows you can use Putty to setup a ssh tunnel. Check out this guide:
[http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/](http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/)

---

### Post by krunge on 2012-09-08
You can find some examples here to start the x11vnc server though your SSH connection:

[INDENT][http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)[/INDENT]

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-putty](http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-putty)[/INDENT]

The SSVNC companion viewer for x11vnc can also automate the SSH tunnelling for you.

---

