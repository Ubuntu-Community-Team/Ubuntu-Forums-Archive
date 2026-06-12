---
title: "Remote desktop connection"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by masterchief1995 on 2009-09-01
I'm pretty sure this is impossible, because I have looked into this for a while now, but is there a way to access my desktop at from another computer, say a computer at school, without installing anything on the school computer. Just install something on the ubuntu home desktop.

Thanks in advance

---

### Post by falconindy on 2009-09-01
Assuming the computer at school is windows based, it should have an RDP client installed by default. In XP, it was available by running mstsc from the run dialog. I don't know if this has changed in Vista or Win7.

However, the Ubuntu end is tricky. XRDP claims to work as a server for the Windows RDP client, but I've had limited success with getting it to work. I can connect to the machine, but I'm unable to log in. It may have something to do with Compiz. I haven't played with it recently, as I've become familiar enough to survive on the command line.

Are you able to use a flash drive? If you don't need/want a graphical interface, you could use PuTTY, which is an SSH client with no installer.

---

### Post by masterchief1995 on 2009-09-02
thanks for your help.
Yes, it is windows xp but I can't use a flash drive
but I will definitley try your suggestion

---

### Post by stefangr1 on 2009-09-02
This is all possible, and very simple. You can configure the Ubuntu part trough the configuration menu's, and use the realvnc executable on the windows machine. You will have to download this executable each time ([www.realvnc.com](www.realvnc.com)), but you don't have to install it.

A saver way to do this though would to install openssh-server on the Ubuntu machine, connect to it with putty (also an executable that can be used without installing anything), forward the port that is used by the remote desktop client, and then start the vnc cliënt. Just google a bit around to find out how exactly to do this in putty, or ask.

---

