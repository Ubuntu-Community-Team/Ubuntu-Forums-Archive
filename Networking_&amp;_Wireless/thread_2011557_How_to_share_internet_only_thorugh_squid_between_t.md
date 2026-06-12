---
title: "How to share internet only thorugh squid between two ethernet"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by HereSomeHow on 2012-06-27
Sorry for the long title. I'm trying to enable a wireless access to my wired network in the office, but only for accessing Internet, I don't want to bridge the two networks (it's prohibited at work).

I have a Mythbuntu 12 box, with 2 ethernet ports already working, in eth0 is the corporate network and in eth2 is a linksys AP already configured to provide IP and access with WPA2 security.

What I thought is to install SQUID and configure it to re-route all eth2 http requests to eth0 (which has a proxy to internet, with user/password). How should I configure SQUID?

I'm getting headaches reading the SQUID doc's, and I'm getting more confused every time I read them. 

Thanks for your patience.

---

