---
title: "Setting up electeronic drop box - ftp or SSH"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-12-20
I want to set up an electronic drop box for people to access online, i've considered a few different options including ftp and ssh connections

this need to be available to windows users as well as those of us in the nix world.

so which would you suggest and why?

---

### Post by wojox on 2010-12-20
I'd go with SSH and have your Windows users install PuTTy

---

### Post by Boondoklife on 2010-12-20
I would go with ftp over ssl, but it all depends on what you require.

If you don't care about encryption then go with plain ftp.

---

### Post by Ceiber Boy on 2010-12-21
> **Boondoklife said:**
> I would go with ftp over ssl, but it all depends on what you require.

If you don't care about encryption then go with plain ftp.

encryption is important so SSH i think is the way to go, i'm experimenting with setting up different users and restricting their accounts but i'm unable just to restrict them to their home folder!

---

### Post by Boondoklife on 2010-12-23
shouldn't chroot limit their access?

---

### Post by Ceiber Boy on 2011-01-13
Solution

[http://ubuntuforums.org/showthread.php?t=1660615](http://ubuntuforums.org/showthread.php?t=1660615)

---

