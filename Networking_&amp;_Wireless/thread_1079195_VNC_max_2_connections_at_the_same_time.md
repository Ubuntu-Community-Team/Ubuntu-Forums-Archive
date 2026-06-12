---
title: "VNC max 2 connections at the same time?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by danielw84 on 2009-02-24
Hi All,

I have setup VNC access to an Ubuntu server. (So that people have access to the network when they are connected with VNC to this server) I have used this manual to setup VNC: [https://help.ubuntu.com/community/UbuntuLTSP/GDMVNCInetdssh](https://help.ubuntu.com/community/UbuntuLTSP/GDMVNCInetdssh)

I have tested it for a while. In the inetd.conf I have added 3 more lines, so that 4 people can connect to the server at the same time. But when 2 people are connected let's say through port 5901 and 5902 and I want to connect through 5903 I don't get my desktop. When I use the shell to open a VNC connection I directly get this message:

[INDENT]CConn:       connected to host XXX.XXX.XXX.XXX port 5903
CConnection: Server supports RFB protocol version 3.8
CConnection: Using RFB protocol version 3.8
main:        read: Connection reset by peer (104)[/INDENT]

When one of the users logout (let say 5091) I suddenly can connect to port 5903. When the disconnected user wants to connect again through port 5901 he get's the same messages as above.

So I can only think there is some kind of an limitation of de connections through VNC. I only can't find where to configure it.

Hope somebody knows the answer.

Thanks,
Daniël

---

### Post by danielw84 on 2009-02-26
Does sombody already have a solution? I still can't find what I'm doing wrong.

The problem with java and VNC is solved:
[http://ubuntuforums.org/newreply.php?do=postreply&t=1079182](http://ubuntuforums.org/newreply.php?do=postreply&t=1079182)

Hope someone can help me with thisone, because I really need more than two active VNC connections.

Daniël

---

### Post by danielw84 on 2009-04-08
Still searching and not found a solution.....

---

