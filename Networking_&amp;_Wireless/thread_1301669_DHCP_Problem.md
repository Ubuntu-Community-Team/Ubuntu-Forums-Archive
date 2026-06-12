---
title: "DHCP Problem?"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by BETELGEUSE58 on 2009-10-26
Hi

I cannot connect to my network with DHCP. 

I have win 2003 as dhcp server. It will assign an address in vista, but it doesn't connect in linux (same computer, dual boot).I am using wireless. The two lights turn green and then it drops out before connecting.

If I manually assign ip it works fine.

Only dhcp on the network is the win server. I have static ip's assigned based on mac address to two pc's. Is this conflicting somehow by booting in linux and vista on the same machine? DNS info is sent out with dhcp which is my isp's dns server.

Any ideas appreciated.

Thankyou

---

### Post by jward3010 on 2009-10-26
> **BETELGEUSE58 said:**
> 
Only dhcp on the network is the win server. I have static ip's assigned based on mac address to two pc's. Is this conflicting somehow by booting in linux and vista on the same machine?
No it shouldn't, the MAC address will be the same no matter what OS you boot up. It's strange. You  have definitely turned off DHCP on your router?

---

### Post by BETELGEUSE58 on 2009-10-26
Hi

Thanks for reply.

Yes DHCP is off on router and switch. I tested it as I went along setting up the server. If I turn off DHCP on server it wont renew an IP.

Seems a bit strange to me too.

Possibly driver related with Ubuntu. I've had problems a few times getting DHCP from other networks with my wireless card so I have to manually assign an ip.

Thanks again.

---

### Post by jward3010 on 2009-10-26
It could be driver related. If you know what DHCP options are do you have any odd ones switched on? The basic ones are provision of "Default Gateway", "DNS server", "WINS" (if switched on), "Subnet Mask" and "IP" obviously.

---

### Post by BETELGEUSE58 on 2009-10-26
I have all those on with the exception of wins.

---

