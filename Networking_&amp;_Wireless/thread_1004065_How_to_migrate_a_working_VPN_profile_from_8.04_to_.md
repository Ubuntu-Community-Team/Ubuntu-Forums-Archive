---
title: "How to migrate a working VPN profile from 8.04 to 8.10"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Physicist on 2008-12-06
The GUI of networkmanager in Ubuntu 8.10 seems to have some problems preventing me from setting up VPN. I have also tried my luck with kvpnc, pptpclient but all in vain. 

I already have a working VPN on another computer which *fortunately* did not get upgraded and still runs Ubuntu 8.04 and still has the working VPN. I am wondering if there is a way to migrate the working VPN profile from my 8.04 machine to the 8.10 one.

---

### Post by tact on 2008-12-06
> **Physicist said:**
> The GUI of networkmanager in Ubuntu 8.10 seems to have some problems preventing me from setting up VPN. I have also tried my luck with kvpnc, pptpclient but all in vain. 

I already have a working VPN on another computer which *fortunately* did not get upgraded and still runs Ubuntu 8.04 and still has the working VPN. I am wondering if there is a way to migrate the working VPN profile from my 8.04 machine to the 8.10 one.

For some PPTP (microsoft) VPN connections you need to be able to set the "refuse EAP" setting and this is missing from the networkmanager in intrepid.

If this is your problem below is an excerpt from another thread where I posted a solution I found by googling....

> Ok got it sorted. The new networkmanager in intrepid does not have an option to "refuse EAP" and that is essential to many PPTP type VPN connections.

I found a thread that hit on the answer... go into gconf and add a new string key called "refuse-EAP" and set its value to "yes"

where to put this new key - when you are in the gconf editor navigate to /system/networking/connections/x/vpn

"x" will be a number representing the connection...  mine was 5, yours may be different.

You still need to set MPPE on and stateful...  should work then.


---

