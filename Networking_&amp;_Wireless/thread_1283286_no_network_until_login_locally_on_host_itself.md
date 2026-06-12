---
title: "no network until login locally on host itself"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by justfred on 2009-10-05
Trying to fiddle and install a wireless adapter on a Jaunty desktop I think I broke something, but I am unable to tell what exactly.

Unlike before, I am not able to remote login or even ping on this host (even though it is running and showing the gdm greeter locally) until I also login locally. Loging out locally also breaks the remote logins established.

In fact in the logfiles of my dchp server (another host) I can see that when and only when I login locally a DHCP address is asked for and obtained.

Any ideas ?

Thanks.

---

### Post by justfred on 2009-10-05
Just to be clear the wireless adapter is removed at present.

---

### Post by justfred on 2009-10-05
bump ...
anyone ?

---

### Post by Iowan on 2009-10-05
That *might* be a function of Network Manager.  Some other threads suggest that NM-managed connections don't start until a user logs in.  An option would be to set up the interface in */etc/network/interfaces*, try it, and put things back (delete/comment) if nothing improves.  Shortcoming is that DNS servers get trickier to define.

---

### Post by justfred on 2009-10-06
Yup that's it :

reverted /etc/network/interfaces to

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0                    # inadvertedly deleted those lines when I came 
iface eth0 inet dhcp         # back from my adventures with the wireless


```Thanks.

---

