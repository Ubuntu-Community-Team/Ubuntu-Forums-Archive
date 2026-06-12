---
title: "Can't re-enable wireless on my laptop"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by campee on 2009-06-24
I have an Asus EEE 1000HE running Ubuntu 9.04. Wireless works fine out of the box. However, if I disable my wireless card by pressing Fn + F2 to save power and then try to re-enable it by pressing Fn + F2 again, Network Manager doesn't show me any wireless networks. Also, if I type "ifconfig" in a command prompt, the wireless device doesn't show up in the list. It shows up as "ra0" when it's working. I can get it to work again if I reboot, but I'd rather not have to reboot. I've tried "ifup ra0" and "ifconfig ra0 up" but neither one works:

root@netbook:~# ifup ra0
Ignoring unknown interface ra0=ra0.
root@netbook:~# ifconfig ra0 up
SIOCSIFFLAGS: Operation not permitted

I've also tried /etc/init.d/NetworkManager restart but that doesn't help either. Any ideas?

---

### Post by campee on 2009-06-25
Anyone?

---

