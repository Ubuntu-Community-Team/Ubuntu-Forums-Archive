---
title: "No Lirc modules for 2.6.30 kernel"
date: 2009-07-27
forum: Multimedia Software
---

### Post by ebike on 2009-07-27
Hi All,

I am running mythbuntu jaunty.

I have just installed the 2.6.30 kernel from the ubuntu site. It boots fine, but complains about no lirc modules.

I have tried to re-install lirc, but the issue remains .. no lirc kernel modules.

Can someone explain how to get these modules into the kernel.

Thanks,
Bernie

---

### Post by cenwesi on 2009-07-27
you will have to go to lirc homepage and download the source and compile it. There is instructions there on how to do it.

---

### Post by ebike on 2009-07-27
Thanks :P

---

### Post by ebike on 2009-07-31
I have an update. I have it working, at least "irw" shows it is working, but I can't get pyLirc to connect to the socket.

With the old aptitude version of lirc, I get a /dev/lirc0 and a /dev/lircd socket. With the new source compiled and installed, when the PC boots up, I only get a /dev/lirc device ... I can't see a socket at all.

I run lircd by giving the "lircd -d /dev/lirc" command as root, and irw works fine, I can press my streamzap remote and see the commands.

However I am using Freevo, and it uses pyLirc to connect to the socket, but it wants a /dev/lircd and the new compile does not provide one. 

(I manually removed all the /dev/lirc* entries to manually remove the old aptitude lirc because to use aptitude to remove it, it wanted to un-install heaps of stuff I wanted as well ..)

So does anyone know how to get pyLirc to connect to the socket? Has lirc changed the socket device it presents?

Thanks,
Bernie

---

### Post by ebike on 2009-08-01
It seems I must do lircd -d /dev/lirc -o /dev/lircd ...

now I have a socket and pyLirc works.

---

