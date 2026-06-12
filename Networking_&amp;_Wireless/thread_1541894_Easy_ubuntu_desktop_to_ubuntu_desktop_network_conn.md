---
title: "Easy ubuntu desktop to ubuntu desktop network connection"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by osviweb on 2010-07-29
Hi all I've searched for this with no easy answer.
How I can connect two pc both with fresh install of Ubuntu 10.04 ?
In the middle there is a router switch.
Pc are on the same lan.
I have the ip of the remote ubuntu box I want to connect to.
I have no phisical access (keyboard, mouse) on the second box.

the ubuntu box I want to connect to it have:

ip 192.168.1.9
fresh install of ubuntu desktop 10.4 32bit
user is not logged in
I know user and password for it
THere is no particular network configuration or share in it
it respond to ping

I'm from a ubuntu pc with the same lan and configuration.

Is there an easy way (like workgroup in windows) to do that?

thanks

---

### Post by marc.verwerft on 2010-07-30
Hello,

> How I can connect two pc both with fresh install of Ubuntu 10.04 ?

the first thing you should do is install and activate ssh daemon (package sshd) on the machine you want to connect to. Then read this:
[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

You mentioned > Is there an easy way (like workgroup in windows) to do that? so I think you want to share some files between the two boxes. Possibilities are:

[LIST]
[*]sshfs (ssh file system)
[*]nfs (network file system)
[*]samba (to share files/printers with windows machines)
[/LIST]
If you have ssh running, then probably sshfs will be the easiest to set up.

Regards,

Marc

---

