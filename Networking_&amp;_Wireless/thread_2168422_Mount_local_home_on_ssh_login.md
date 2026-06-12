---
title: "Mount local home on ssh login"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by kelbethor on 2013-08-17
I use ubuntu desktop to log into ubuntu server using ssh, is it possible to have automaticaly mounted local home directory in remote fs when on login??

---

### Post by newbie-user on 2013-08-17
Yes. On the server, edit your .bashrc file. You can add a script in there that will mount your desktop's home dir to the server. The .bashrc file is read every time you log in, so it'll do whatever is in that file whenever you ssh into the server.

---

### Post by kelbethor on 2013-08-18
Well I supose that way sshfs is needed, but it's not what I was thinking about (but I admit I didn't think about that alternative).

I was thinking about an openssh client built-in feature (something like connect local folders on terminal services).

Goal is pretty complex way to get vps partition backup. I set up a minimal secondary installation to boot into for management, log in using ssh to make main system partition image but I want the image being stored in my local machine. I think I could redirect partclone output to scp but that would involve seting dyndns, forwarding... And I not working always behind the same gateway...
Well that is... suggestions wellcomed!

---

