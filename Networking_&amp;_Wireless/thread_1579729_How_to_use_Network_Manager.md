---
title: "How to use Network Manager"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by Stephen-I-M on 2010-09-22
Sorry if this is a dumb question.

I'm trying to change my network settings under Gnome and 9.10.

System->Preferences->Network Connection brings up "Network Connections". Under the "wired" tab, I see "ifupdown (eth1)". The edit button on the right side is grayed out.

Is this where an IP address can be config'ed, or is it somewhere else? Thanks.

Stephen

---

### Post by linux-hack on 2010-09-22
it is not a stupid question. Is there a button that says UNLOCK or something because you need root privileges (Administrator) to change the conf. 
Did you take a look at the doc : 
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

[http://doc.ubuntu-fr.org/network-manager](http://doc.ubuntu-fr.org/network-manager)

---

### Post by dineshs on 2010-09-22
You should select the ethernet connection listed under wired to edit (ie click on eth1).Have you tried that?

---

### Post by Stephen-I-M on 2010-09-22
Thanks. If I click on the interface, the edit button stays grayed out. There is no unlock button.

In the past I've edited /etc/network/interfaces by hand. Perhaps this is the reason. I was able to get networking back up by changing this file, so immediate problem solved.

---

