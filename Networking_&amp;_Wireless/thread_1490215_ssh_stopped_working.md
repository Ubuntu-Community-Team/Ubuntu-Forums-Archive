---
title: "ssh stopped working"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Worp8d on 2010-05-22
Hi.

I'm using Ubuntu 10.04 on my home laptop and desktop connected through a router/modem.  For some time now I've been ssh-ing from the laptop to the desktop using ```
ssh media@media-centre
``` which worked fine.  Then I started playing around with VNC, installing and trying the various server/client combinations and then went back to the standard vino/vinagre.  VNC works fine but ssh now times out using the above command so I have to issue ```
ssh <ip.addr> -l <user>
``` even after re-installing the shh (i.e. openssh-client/sever) package.  Is there anything I can do to find out what the change is?

This wouldn't bother me except that I use grsync and other programs and I don't want stuff around setting them up again.

Cheers.

---

### Post by iponeverything on 2010-05-22
It is unusual to change the behaviour of something like ssh this way. You can probably get around the problems by creating a wrapper called ssh and renameing ssh to ssh.real.

This way you won't have fix your scripts or my case, my habits.

---

