---
title: "2 Network interfaces cant work simultaneously"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by tada-jin on 2009-07-13
i got a wireless card, with a network interface on the mobo. for some reson, they cant work at the same time. the cable network overrides the wireless. is this a bug or is thier a work-around?

thanks in adv.
tada-jin

---

### Post by sanemanmad on 2009-07-13
I believe what you are looking for is documented here [http://linux-ip.net/html/adv-multi-internet.html]("http://linux-ip.net/html/adv-multi-internet.html")

---

### Post by tada-jin on 2009-07-14
Sorry sanemanmad, i may not hav explained it properly... my bad. my wireless link is connected to a wireless router that is connected to the internet. the cable is connected to a small network that has no internet connection.  i am essentally using the pc as a proxy server without the proxy program.

---

### Post by aesis05401 on 2009-07-14
> **tada-jin said:**
> Sorry sanemanmad, i may not hav explained it properly... my bad. my wireless link is connected to a wireless router that is connected to the internet. the cable is connected to a small network that has no internet connection.  i am essentally using the pc as a proxy server without the proxy program.

[http://ubuntuforums.org/showthread.php?t=376283]("http://ubuntuforums.org/showthread.php?t=376283")

---

### Post by sanemanmad on 2009-07-14
So what you want is to use iptables.

---

### Post by sanemanmad on 2009-07-14
Example would be 
```
iptables -t nat -A PREROUTING -p TCP -i ethX -s YOUR_NET_BLOCK -j DNAT --to YOUR_NET_IFACE
```
```
iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
```

---

