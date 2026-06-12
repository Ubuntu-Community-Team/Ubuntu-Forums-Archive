---
title: "Connecting to a WPA2-Enterpise network with intrepid"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by mariourk on 2008-12-08
I have installed Ubuntu 8.10 on a laptop. Now I'm trying to connect to a eap-tls protected WPA2-Enterprise network. When I'm trying to select te certificates, it will only show the private-key. Not the (CA)certificate. I exported these certificates with ssl to a x509 format. Yes, I created all the certificates myself, So I have some flexibility here :p
```

openssl x509 -in cert_nonx509.pem -days 3650 -out cert_x509.pem

```
After doing this, Intrepid would see the certificates and I got one step further.

However. After filling in all the thing Intrepid needs to know, the *Connect* button remains inactive. I can't click on it, no matter what I do :confused:

Any solution for this?

---

### Post by mariourk on 2008-12-09
*kick*

Anyone?

---

