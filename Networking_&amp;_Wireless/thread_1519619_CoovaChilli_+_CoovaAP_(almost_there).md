---
title: "CoovaChilli + CoovaAP (almost there)"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by dashnu on 2010-06-28
I used this howto [https://help.ubuntu.com/community/WifiDocs/CoovaChilli](https://help.ubuntu.com/community/WifiDocs/CoovaChilli)

And I can now connect to the wireless hotspot and it redirects me to a (what I suspect to be) final login page. However nothing shows up after the initial coova redirect page. I loads a page with only a coova logo, nothing more.

Any ideas what might me causing this, what I forgot to do or did incorrectly ?

TIA

---

### Post by dashnu on 2010-06-28
This is something with using json interface, if you change the following in /etc/chilli/config;


HS_UAMFORMAT=http://\$HS_UAMLISTEN:\$HS_UAMUIPORT/www/login.chi
#HS_UAMFORMAT=https://\$HS_UAMSERVER/uam/

i get a login page and can log in and use the hotspot as expected.

I am not sure what this is costing me right now as I have only been dorking with it for a few days..

---

