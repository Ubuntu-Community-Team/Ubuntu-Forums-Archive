---
title: "need help on making ubuntu router with webmin for cyber cafe!! please"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by dlwoaud on 2009-12-16
hi, i'm a owner of cyber cafe, and switched qwest T1 to Cox Business Cable.
Cox give me 64 IP Address and i want to set all of our computer has static IP for indivisually. So i asked cox tech. that how do i use all 64 IP address for my network, they said i have to buy Router or make Linux Router. So i installed ubuntu and installed webmin to set my linux machine as router. After that i followed instruction on webmin and i'm just stucked....Have no idea......:(

Cox Tech told me I have to route my 64 IP to Main IP address come from Cox Modem, and they said i can do that if i make linux system with webmin.

Here is what i want to do.

I just installed ubuntu on computer, and installed two Netwroks card.
and i have main ip (i'll call is as 1.1.1.1.) and they also give me extra 64 IPs that i need to route it to my main ip 1.1.1.1.  (i'll say my extra IPs as 9.9.9.1 ~ 9.9.9.63)

and i installed WEBMIN on ubuntu, i don't know how to route the IPs...

if anyone knows, please help me.


our network setup will be 

connect "**COX MODEM" **to "**ubuntu linux router machine NIC 1**"

connect "**ubuntu linix router machine NIC 2**" to "**64 port switch**"

connect cables from "**64 port switch**" to "**each stations**."

---

### Post by byStanderone on 2009-12-16
...hope this community doc helps : [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by dlwoaud on 2009-12-16
> **byStanderone said:**
> ...hope this community doc helps : [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

thank you for replay, i tried that on the link you send me. but i do not have any good luck from that link....anyone have other idea?

---

### Post by thenone on 2009-12-26
there is an easy way to setup a linux router for sharing your internet access for your others client/workstations is by using smoothwall, it is very easy to install although an installation via text base, once you manage installed it on your pc, then you can connect to smoothwall via web browser. Smoothwall also provided with squid as proxy server and iptables to turn it as a firewall to manage your internet access security.

Smoothwall comes with 2 version:

1- smoothwall corporate for the business purpose(you need to pay for it)
2- smoothwall express is the free version

the free version can be download from here [www.smoothwall.org]("http://www.smoothwall.org")

---

