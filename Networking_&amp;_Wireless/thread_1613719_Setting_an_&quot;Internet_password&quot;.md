---
title: "Setting an &quot;Internet password&quot;?"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by PhawKhrua on 2010-11-04
Hello,
Some friends of mine have a son who would like to experiment with Linux and they would like for me to put it onto an older, spare computer they have. The difficulty is that they want to control when their son would be able to access the Internet and they want me to set up an "Internet password" so that ANY attempt to access the Internet from that machine (not just from a browser, but also from ftp, bittorrent clients, etc.) would require the entry of the password. I'm used to having complete, unfettered, root access to Linux systems, so I don't know of any way to implement such a password.


Is this the kind of thing that something like squid would be able to do?  If so, how?  If not, do you know of any other ways to accomplish this?


Thank you!

---

### Post by grahammechanical on 2010-11-05
Try Users and Groups. Let the parents have access as Administrator, which is what will happen when you first install, but set the boy up as a desktop user with his own password. Limit what he can do as a desktop user. There is also a custom setting. Changes cannot be made to these accounts without the administrator password, which is the login in password of the parents. They of course must not allow their son to know their password or access the computer under their login. They should switch users. They could also allow their son to use the computer as a guest. Check first what privileges a guest has.

regards
Regards.

---

### Post by Chazz44able on 2010-11-05
The easiest thing would be to simple password protect their internet connection (if they're using a router, just use a WEP key that they don't tell their son

---

### Post by CharlesA on 2010-11-05
> **Chazz44able said:**
> The easiest thing would be to simple password protect their internet connection (if they're using a router, just use a WEP key that they don't tell their son

That only works for wireless and don't use WEP. Use WPA or WPA2.

---

### Post by PhawKhrua on 2010-11-05
> **Chazz44able said:**
> The easiest thing would be to simple password protect their internet connection

Hence my question of how to set one.

> (if they're using a router, just use a WEP key that they don't tell their sonOops!  Had planned to mention this, but forgot: This is a desktop machine that would be connected directly to a Linksys router - not via wireless, not through a Smoothwall machine, *nada*.

Thank you all for your suggestions so far, though.

---

### Post by CharlesA on 2010-11-05
You could always be mean and redirect the DNS servers to 127.0.0.1 and then change them back to what they should be when you want them on the interwebs.

I don't know of a way to "password protect" it tho.

Either that or just bring the network interface down if they don't need to access the network at all:

```
sudo eth0 down
```

---

### Post by chili555 on 2010-11-05
I think System > Administration > Users and Groups is the simple way to do it. Please see attached. As you can see, access to all network activity may be denied.

That will prohibit file sharing, but USB drives will allow Dad to know what is being transferred to son's computer.

Any changes to these settings require the administrator's password (read: Daddy).

---

### Post by PhawKhrua on 2010-11-07
Thanks, Chili.  I'll give that a try and see if they're satisfied with that.  They're expecting something more like a prompt for a password upon attempted access (which would then last for a certain amount of time), but let's see if this will be enough to keep them happy.

To get a head start (I hope), I'll install Ubuntu Christian Edition so it will already have Dansguardian, etc. installed.

---

### Post by chili555 on 2010-11-07
Post back if we can help you further.

---

