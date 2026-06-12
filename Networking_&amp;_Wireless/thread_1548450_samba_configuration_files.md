---
title: "samba configuration files"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Roinou on 2010-08-08
Hi all,

I'm setting up a Samba server on my 10.04 machine, and ran into some good documentation. Nevertheless, there is something I would like to know.

You can use nautilus to create the share options. There are not so many parameters, but you can do it. My question is: where are these parameters stored? I would pretty much like to tweak them, and I was wandering whether it was a good idea to edit a file inside my user folder rather than the /etc/samba/smb.conf directly. Now, if everybody says that smb.conf is the only place to be, so be it.

Bonus question: I have the feeling that /etc/init.d/smbd restart or service smbd restart (neither the reload target) seem to fully work. I noticed that it wouldn't apply changes of the workgroup value (change would appear after restart).

thanks all!

---

### Post by Iowan on 2010-08-08
Check in */var/lib/samba/usershare*.

---

