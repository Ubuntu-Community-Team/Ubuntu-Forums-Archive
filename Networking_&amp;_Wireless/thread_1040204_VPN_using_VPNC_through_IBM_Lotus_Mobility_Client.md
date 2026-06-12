---
title: "VPN using VPNC through IBM Lotus Mobility Client"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by aamr on 2009-01-15
Hi,

I have an issue that I don't know whether it can be solved or not, but seems logical to me anyway! I work in IBM and currently I work for a customer site that blocked all the traffic except those through IBM's VPN Client (Lotus Mobility Client), I wanted to achieve two goals:

1) Get Internet access through that connection: I was successful in that as I found that IBM has internal proxies, therefore I could have access through them.

2) I have another VPN connection to that client (so that I can connect from home), this client is implemented using VPNC, but I cannot connect to it when I'm at the client using the SAME connection as above (Remember that I can only access IBM's VPN through the Lotus Mobility Client). What I wanted to do is **access the client's VPN through IBM's VPN**, is that possible?

Thanks!

---

### Post by acronis on 2009-09-29
Hi, I have the same situation :(
I managed to download Mobility Client 6.1.3 and converted it from rpm with alien to deb.
The Icon showed up in Ubunto, but unfortunately the application did not start.
Looking for advise on how to proceed.
The other route to a solution could be using the ISSI pack from the IBM Linux client, but then you need a Linux workstation to be able to download it.
Curious to know your next steps.

---

### Post by aamr on 2009-09-30
Hi Acronis, this problem does no longer exist with me and I'm able to connect the IBM Mobility Client and the VPNC connection simultaneously, but only through wired and wireless (wifi) connections, i.e. it doesn't work using my 3G modem, don't know why!

Also, concerning the IBM packages for mobility client, there already exists all .deb files you need, you needn't use alien at all. If you need any further information or assistance, you can contact me on my IBM e-mail; my username is "aamr".

---

