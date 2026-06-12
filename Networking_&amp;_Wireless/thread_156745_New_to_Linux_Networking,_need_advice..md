---
title: "New to Linux Networking, need advice."
date: 2006-04-07
forum: Networking &amp; Wireless
---

### Post by grs on 2006-04-07
Just loaded Ubuntu on to an old PII desktop to see what it's all about.
I also have a laptop running Windows XP Pro. how do I go about connecting the two machines together to share/swap files and to share an internet connection through the laptop?

---

### Post by John.Michael.Kane on 2006-04-07
This should get you going.
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)

---

### Post by grs on 2006-04-08
thanks for the advice.

---

### Post by grijac on 2006-04-12
Hello! How can i make the lan users to connect to internet through my ubuntu server. Ie configured my eth0 card with extarnal ip and gtw,and eth1 with the lan ip standard...192.168.0.1 and the external gtw. They can see the server but can connect to the internet.
Please enlighetn me :) .....help me please. Thanks

---

### Post by spd106 on 2006-04-12
[QUOTE=grijac]Hello! How can i make the lan users to connect to internet through my ubuntu server. Ie configured my eth0 card with extarnal ip and gtw,and eth1 with the lan ip standard...192.168.0.1 and the external gtw. They can see the server but can connect to the internet.
Please enlighetn me :) .....help me please. Thanks[/QUOTE]

You need to set up port forwarding through iptables. The easiest way is to use a utility like firestarter. It combines internet sharing with a firewall and it's available through in the universe repositories.

---

