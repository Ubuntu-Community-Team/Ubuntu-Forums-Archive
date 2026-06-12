---
title: "SCP issues"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by lifemod on 2009-11-23
I need to transfer a file to a remote server using an account from a different server.
ex.
    $ scp pikachu.png [email]bob@pcn.com[/email]@172.27.0.5:/shareme/pokemonpics
I've tried many different alternatives to this but I still cant seem to make it work.
Plz help!!

---

### Post by scorp123 on 2009-11-23
> **lifemod said:**
> I need to transfer a file to a remote server using an account from a different server.  You mean the second server is behind the first one and in a private address range (guessing from the IP that you posted: 172.27....) ?

Maybe you could try a SSH tunnel instead?
[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

e.g. you establish a tunnel and port-forward e.g. port 2222 which ends up on the second host?

```
ssh -N -C -L 2222:172.27.0.5:22 bob@pcn.com
scp -P 2222 bob@localhost

```

---

### Post by Iowan on 2009-11-23
> **lifemod said:**
>  using an account from a different server. :confused: Are you copying from one remote server to another remote server?

---

### Post by scorp123 on 2009-11-23
> **Iowan said:**
> :confused: Are you copying from one remote server to another remote server? What he's trying to do is called "SSH hopping" or "SSH Bouncing"

Read here:
[http://scharfie.com/2009/08/21/ssh-hopping/](http://scharfie.com/2009/08/21/ssh-hopping/)
[http://srimal-techdiary.blogspot.com/2009/08/multi-hop-ssh-tunnelling.html](http://srimal-techdiary.blogspot.com/2009/08/multi-hop-ssh-tunnelling.html)
[http://www.hackinglinuxexposed.com/articles/20040830.html](http://www.hackinglinuxexposed.com/articles/20040830.html)

---

### Post by lifemod on 2009-11-24
Yep, thanks scorp123.  That definitely turned out better results. :D

---

