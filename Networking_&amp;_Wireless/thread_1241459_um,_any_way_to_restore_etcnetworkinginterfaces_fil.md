---
title: "um, any way to restore /etc/networking/interfaces file?"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by hooless on 2009-08-16
hey, i'm an ubuntu noob, and guess what- I somehow deleted my interfaces file, or its not showing up in terminal.

either way, is there a way to restore it without wiping my entire system??

thanks!

---

### Post by lswb on 2009-08-16
On a standard desktop installation using Metwork Manager, the /etc/network/interfaces file isn't used for much. The only contents are:
```

auto lo
iface lo inet loopback

```

You can save this by running gedit as root with the terminal command

gksudo gedit /etc/network/interfaces

Then just paste the 2 lines and save the file

---

### Post by hooless on 2009-08-16
> **lswb said:**
> On a standard desktop installation using Metwork Manager, the /etc/network/interfaces file isn't used for much. The only contents are:
```

auto lo
iface lo inet loopback

```

You can save this by running gedit as root with the terminal command

gksudo gedit /etc/network/interfaces

Then just paste the 2 lines and save the file

kk. that was exactly what I needed. thanks!!

---

