---
title: "Wep authentication"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by titanicmusic14 on 2010-01-31
Is there a way to setup something where in order to use the internet. One has to Authenticate through my ubuntu server or something along those lines. Because I think someone has cracked our WEP key. My samba server has logging some random user that does not live in our house keeps trying to log in as 'root' and as 'nobody' multiple times. How do I make like a gateway or something to add an extra layer of authentication without having to get everybody in my house's mac address.

---

### Post by mprokolo on 2010-01-31
the easiest thing to to is change authentication to wpa

---

### Post by moebuspcgold on 2010-02-12
Perhaps you can use a Authenticating Proxy for internet access?
```
http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html
```

---

### Post by markbuntu on 2010-02-12
WEP is very easy to crack. You should switch to WPA as suggested above. You can also use mac address authentication. Either one will kick the offender off your network.

---

