---
title: "Network died, bought new card, but howto make work without network?"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by eklem on 2012-12-30
Hi,
I have a desktop running 64bit desktop version of Ubuntu 12.10, and not long ago my network card died. I bought a new one, but I guess I lack a driver/kernel module or something.

Now there's lights on the network port, but I still get this error message

```

Waiting for network configuration...

```

... and ...
```

Waiting up to 60 more seconds for network configuration...

```

... and ...
```

Booting system without full network configuration...

```

So, how do I go about to fix this? The old network card had the same error messages, but then the network switch had no lights on the network cable from the desktop, now there is.

---

### Post by praseodym on 2012-12-30
Hi, open the following file:

```
gksu gedit /etc/network/interfaces
```
Delete anything _except_:
```

auto lo
iface lo inet loopback
```
Save, close, and reboot.

---

### Post by eklem on 2013-01-01
I'll try that, thanks a lot!

---

### Post by eklem on 2013-01-01
That did the trick, thanks for quick and precise answer. I think I messed up the interfaces-file when the old network interface started to have problems.

---

