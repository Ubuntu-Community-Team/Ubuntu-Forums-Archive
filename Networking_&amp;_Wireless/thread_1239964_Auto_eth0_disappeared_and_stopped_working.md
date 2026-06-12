---
title: "Auto eth0 disappeared and stopped working"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by stmartin on 2009-08-14
Hello!

After setting "pppoeconf" I lost Network Manager in the taskbar. Also local area connection (auto eth0) wasn't working. So I reinstalled network manager using "sudo apt-get remove network-manager" and "sudo apt-get install network-manager". Network Manager now appear in the taskbar by unfortunately my "Auto eth0" connection is lost, and for unknown reasons I can't set-up a new one.

Could somebody possibly help me?

Thanks in advance.

---

### Post by cmannnn on 2009-08-14
have you tried restarting your system or plug unplug your etho cable

---

### Post by Zack McCool on 2009-08-14
what is the contents of /etc/network/interfaces  ?

---

### Post by stmartin on 2009-08-14
Thanks for the replies.

> **cmannnn said:**
> have you tried restarting your system or plug unplug your etho cable

I tried that but still nothing.

> **Zack McCool said:**
> what is the contents of /etc/network/interfaces  ?

Here is the content:

```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

---

### Post by Iowan on 2009-08-14
Try commenting out everything except the two (top) lines about "lo", and reboot. If it messes things up, you can put it back, but if an interface is defined in */etc/network/interfaces*, NM is not supposed to touch it.

---

### Post by Eudoxia on 2009-08-27
Same problem here.

I'll try Iowan's solution

---

### Post by shredder12 on 2009-08-28
Ya, Iowan's solution worked for me..
Even though after restarting you won't see an auto eth0 connection but you can always add a connection named auto eth0 by editing network connections.

---

