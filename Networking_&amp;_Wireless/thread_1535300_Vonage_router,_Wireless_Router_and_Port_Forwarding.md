---
title: "Vonage router, Wireless Router and Port Forwarding"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by alodhi on 2010-07-20
All: 

The following setup has been working successfully but I couldn't understand this all - need your help.

Initially, I was not able to access FTP, HTTP services setup within my private LAN from public domain address (public IP). I tried port forwarding - but no use - eventually discovered that I am using Vonage router in the upstream and my netgear router is sitting behind the vonage router. I disconnected vonage router - then it all started working fine. 

Obviously, now I need to hook up vonage back - did some research - and found that perhaps I can put my NetGear router as a DMZ to Vonage router. So using vonage router admin GUI, I attached the NetGear router to a DMZ.

Question is: Vonage router admin page asked for a static IP to use to set DMZ. Both Vonage and NetGear routers are set as DHCP servers. Vonage router default gateway is set to 192.168.15.1 -- so for setting the NetGear router on DMZ - I used 192.168.15.2 to set NetGear.

My theory was that once I hook up Netgear on a DMZ - public traffic would by pass vonage router and intercepted at NetGear router, from where it will assign new private IP addresses to machines in my private LAN. So I was expecting to setup NetGear LAN IP to 192.168.15.2 as gateway, and then starting IP range from 192.168.15.3 -- 192.168.15.65 --- with this setup -- I was not able to browse internet --- why?

I change the NetGear configuration back to 192.168.0.1 as gateway and 192.168.0.2 - 192.168.0.65 as IP range --- everything started working .... using DynDNS to map ISP assigned IP to domain name through which I can access FTP, HTTP, SSH running within my private LAN.

How come if I am setting NetGear on a DMZ with IP = 192.168.15.2 --- my private LAN is not functioning if I use the range 192.168.15.3 - 192.168.15.65 ---- why do I have to set NetGear gateway back to 192.168.0.1 ?

Thanks in advance ... hope I explained this succinctly.

---

### Post by alodhi on 2010-07-20
just found out only HTTP is working -- SSH and FTP not working -- it was when I dropped the vonage router -- seems like there is still something not properly configured. 

i am waiting for someone help.....

---

