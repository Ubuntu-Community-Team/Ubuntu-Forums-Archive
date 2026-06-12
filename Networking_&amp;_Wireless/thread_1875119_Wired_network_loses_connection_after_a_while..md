---
title: "Wired network loses connection after a while."
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by yay101 on 2011-11-04
Hello all, I am currently fiddling with various configurations trying to fix a problem i am having with my data server.

I recently moved a pc with a 740GM-P21 motherboard from windows to Ubuntu (fedora/ mint also have this bug). The problem i am having however is that as soon as i transfer any large amount of data in either direction over the network the adapter seems to just quit, bringing the transfer speed to 0 and causing errors if using ftp or samba to transfer. 

After this drop in speed it refuses connections or to be pinged. Disabling and reenbling the interface via the gui SOMETIMES works to bring the interface back up. Usually however a restart is the only fix.

As a data server the problem here is obvious.

The adapter on the board is a AR8132M, made by atheros. The only thing that makes sense in my mind is this being a driver problem.

Any ideas or help is appreciated.

Thanks, 
Dave.

---

### Post by praseodym on 2011-11-04
Hi,

please show:

```
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/resolv.conf
```

---

