---
title: "VPN connection disable save password"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by mfellman on 2011-10-23
Hi all,

I liked the Maverick release in regards to the VPN setup. When no password was filledin it asked for a password each time I try to login. Handy because I need to enter a unique ID each time via a VASCO key.

Since Oneiric I need to clear the password each time I want to connect to the VPN so I can enter the correct one. Although there is nowhere a checkbox to be seen that sets save password (like in the previous version) it does it anyhow. Is this a bug (or was the previous way to do it a bug)?

Is there a setting I missed? It seems something in the network manager.

With Kind Regards,

Marc

---

### Post by mfellman on 2011-10-31
Nobody?

---

### Post by prodata on 2011-11-03
Same issue over here, I also need to disable this since it breaks my VASCO Digigpass too !

---

### Post by prodata on 2011-11-08
I also have posted your question to the lauchpad,
Let's see if we get an answer there, if not I think I will file a Bug
[https://answers.launchpad.net/ubuntu/+question/178078](https://answers.launchpad.net/ubuntu/+question/178078)

---

### Post by eacastro on 2012-01-12
There is VPN config work around documented on [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/893885](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/893885)
 
*************
From Zoltan Nagy (nagyzo)
 
[Zoltán Nagy (nagyzo)]("https://launchpad.net/~nagyzo") wrote on 2012-01-09: [#5]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/893885/comments/5") 
Setup the flag "password-flags=2" under [vpn] section in the related VPN config file, located here in Ubuntu:
  /etc/NetworkManager/system-connections/<name of your vpn connection>
[vpn]
password-flags=2
 
************

---

