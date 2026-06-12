---
title: "wireless connection problem"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by gejo23 on 2009-05-26
Hello everybody , i have laptop dell inspiron 6000 , i have problem to connect the wireless internet,  somebody help me please .
Thank you very much

---

### Post by Iowan on 2009-05-26
Wireless is not my forte, but...
Post results of **ifconfig** and **iwconfig**, and **lshw -C network**. I presume you're connecting via DHCP rather than static address.

---

### Post by dmizer on 2009-05-26
I moved this to the Networking and Wireless section, you'll get more help here.

Please post the output of this command (from terminal):
```
lshw -C network
```

---

### Post by hjacker on 2009-05-26
I had problems with WI-FI, which I couldn't resolve when I had KDE(Kubuntu 9.04) with it's glitchy-glitchy network-manager applet on my VAIO SZ6. Whereas Ubuntu worked 100% smooth. If you are using KDE, try installing gnome's network manager, which is not that eye-candy, but it works. 
In fact, there's a bug in KDE's nm, which forgets static netmasks and ip's as soon as the window is closed.
Anyway, seems like i'm getting into details.

---

