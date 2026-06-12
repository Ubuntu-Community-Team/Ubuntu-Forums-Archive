---
title: "UFW, block access to an internet site"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by davidecapod on 2010-10-29
Hi all, a question about ufw.
How can I block access to a certain internet site using ufw?
Let's say I want to block access to [www.xxx.zzz](www.xxx.zzz) (IP 1.2.3.4) to any program and user; using iptables I can do

sudo iptables -A OUTPUT -d 1.2.3.4 -j DROP

- how can I do that using ufw?
- if ufw can not do this, where should I put this rule to persist it over reboot, without interfering with ufw chains infrastructure?

Thanks
Davide

---

### Post by Frogs Hair on 2010-10-29
This may be helpful ,  it is possible to add rules under the edit tab .

 [http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

---

### Post by davidecapod on 2010-10-31
Well GUFW is just a GUI for UFW, so it has the same capabilities...
(but for me does not work at all, I can not add any rule, I get a generic error message...)
what kind of rule should I add in UFW/GUFW to do my task?

---

### Post by davidecapod on 2010-11-03
It seems to me that this is not possibile at all using UFW ... !!!
Anyone can confirm this?

---

### Post by sikander3786 on 2010-11-03
[http://superuser.com/questions/183294/how-to-block-access-to-a-website-on-lucid-lynx](http://superuser.com/questions/183294/how-to-block-access-to-a-website-on-lucid-lynx)

This link states that you can use iptables to serve the purpose.

Although I prefer dansguardian to filter all the unwanted websites.

---

### Post by davidecapod on 2010-11-06
Yes I know I can block a site using iptables, I am currently using this method right now (see my first message).
But I was wondering how to do this using UFW, since U is for Uncomplicated I would expected this to be possible.... but it appears not.

---

