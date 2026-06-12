---
title: "Ip"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by Pakia on 2009-05-18
I have set a static ip in network on my machine (Jaunty server with xubuntu desktop) and checked it with if config and it says 192.168.1.13 When I go into my router huawei smart mt882 I cannot see my ip (but I have an internet connection.) As I am webhosting I port forwarded port 80 and 443 on my router for 192.168.1.13 (my static ip) I have connected an Apple airport to the huawei as it is not wireless and I connect to wireless. The router sees me as ip 0.0.0.0 (i checked the mac adress) My apache server cannot be reached from outside the router. My machine is connected to the internet I have a static ip that is not being seen by the router? Any advice would be appreciated

Thanks in advance

---

### Post by dmizer on 2009-05-18
Are you SURE your site can't be visited from externally? If you are connected to your router, but attempting to browse to your external IP address, most routers can't handle that kind of loopback. Try browsing to your web from outside your LAN.

---

### Post by Pakia on 2009-05-18
Have confirmed I use the onion router on another computer as well as phoned someone to check who is not on my network webpage is not up

---

### Post by dmizer on 2009-05-18
Is your router configured for static IP or DHCP? If it's configured for DHCP, then your router won't know that your static server exists because the router didn't assing the IP address.

---

### Post by Pakia on 2009-05-18
I am using dhcp as there is more than one computer on the network and the other machines use dhcp for ip allocation

---

### Post by dmizer on 2009-05-18
> **Pakia said:**
> I am using dhcp as there is more than one computer on the network and the other machines use dhcp for ip allocation

I reviewed the owners manual for your router. It looks like you don't have very much choice here. The DHCP function of your router looks quite limited. You'll need to configure your LAN for static IP. The only other alternative I can think of is to get a different router which can handle a static DHCP lease according to MAC address.

---

