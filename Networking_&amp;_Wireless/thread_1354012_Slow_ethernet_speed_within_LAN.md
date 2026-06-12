---
title: "Slow ethernet speed within LAN"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by ubu_can on 2009-12-13
I have Ubuntu-64 9.04 installed (2.6.28-17-generic) and (at least) recently I discovered that a file transfer between this computer and any other would be at about 200 KBytes/sec!!!  (Asus Mobo, NVidia 430) I tried different things and recently I saw something about MTU. I tried 'ifconfig eth0 mtu 1000' (was 1500 before) and voila, now the same file transfer happens at 5.5 Mbytes/sec, more that 20 times as fast.

My questions:
1) Why is that?  Is it a bug with the specific ubuntu distro, the 64-bit, or it is  in all distros?
2) Is the above a good, sustainable fix?
3) If it is, how could I make it permanent?

Thanks

---

### Post by ubu_can on 2009-12-15
Sorry, that was 'red herring'. The same (and more) problem after changing the MTU. However, after booting to the previous installed kernel (2.6.28-16-generic) seems to help. Is there a problem with 2.6.28-17-generic?

If it does indeed help, how can I remove the ...-17-?  Also, I have problems with the nvidia driver now. How could I revert back to the driver for the ...-16- kernel?

---

