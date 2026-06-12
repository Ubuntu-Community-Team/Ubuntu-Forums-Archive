---
title: "Wireless prob.."
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by Inglor on 2006-06-14
I can't connect to the wireless network. My settings in /etc/network/interfaces are correct cause i test them with a Live CD of Ubuntu and working fine.
When I try to ping anything in my network I get an error like:

ping: sendmsg: Operation not permitted

Any ideas?

edit:typo

---

### Post by kb3hkg on 2006-06-15
have you checked to make sure you are actually connected to wireless? does ifconfig show an IP address for the interface?

---

### Post by Inglor on 2006-06-15
Yes I am connected. I have an ip. (I use static not dhcp)

---

### Post by Room101 on 2006-06-16
Have you turned off any firewall? I.e. stopping firestarter.

---

### Post by Inglor on 2006-06-17
No firewall running.

p.s.: I have two threads so I will continbue in ony one, this one.

---

### Post by Inglor on 2006-06-17
A few weeks ago I tried to fix it following the "How to add ipw2200 with WPA support".
I followed all steps adding WPA support too, I have a feeling that this has somethign to do with my prob.

Anyway I uninstall the wpa_supplicant (prolly typo) and erased the scripts but i think something has left in maybe a module..

Maybe has to do something with the prob.

Sorry i can't provide links I will as soon as possible, I am away from the laptop atm.

---

