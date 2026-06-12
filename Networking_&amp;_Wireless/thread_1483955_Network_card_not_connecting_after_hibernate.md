---
title: "Network card not connecting after hibernate"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by simon303 on 2010-05-15
Hi,

Recently I hibernated my computer, then when starting up again managed to boot into Windows instead. When I rebooted back into Ubuntu 10.04 my network card had stopped connecting to the internet.

It's not a problem with my connection -- I'm posting this form Windows just fine. Using the network tools tool I can see that the card is inactive.

I can use ifconfog to reactivate it, but it still won't connect.

Attached is as many commands as I could find that provide information about the card -- I don't know what's relavent or if I've missed something but I hope it helps.

Does anyone know what is likely to be causing this? Even after reboots the problem persists.

Simon

---

### Post by hansbk on 2010-05-23
Hi,

I found this :

sudo rm /var/lib/NetworkManager/NetworkManager.state

on the french forum :

[http://doc.ubuntu-fr.org/network-manager?redirect=1#verifier_que_le_service_est_en_fonction](http://doc.ubuntu-fr.org/network-manager?redirect=1#verifier_que_le_service_est_en_fonction)


It worked for me ...

Looks like I won't hibernate that often :)

---

### Post by Commodore64 on 2010-05-26
Worked brilliantly hansbk ...thanks man !!

---

