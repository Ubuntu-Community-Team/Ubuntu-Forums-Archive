---
title: "Remote SSH with both DSL modem and wireless router"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by shunter1191 on 2011-07-28
I have an Ubuntu server that I need to access remotely while I am at school. The server's internet connection comes first through a DI-604 broadband router and then through a Netgear Wireless router:

ethernet wall jack --> Broadband Router --> Wireless Router --> Server's ethernet port

I can manage to get the SSH to work with the current IP address (dynamic) by connecting the server directly to the broadband router, but I cannot set up DNS (ddclient on the server, Namecheap for domain registrar and nameserver) with it. I can set up DNS on the router with no issue, as it has the DNS client built in, but I cannot get the SHH to connect through both the modem and the router as mentioned above. Best case scenario, this can be fixed without having to get anything new, but if that is the case, recommendations of a new setup that could solve this issue would be greatly appreciated. 

Other reference info - ISP at server is Verizon Fios, broadband router set to PPPoE.

---

### Post by jeanathon on 2011-08-15
> **shunter1191 said:**
> I have an Ubuntu server that I need to access remotely while I am at school. The server's internet connection comes first through a DI-604 broadband router and then through a Netgear Wireless router:

ethernet wall jack --> Broadband Router --> Wireless Router --> Server's ethernet port

I can manage to get the SSH to work with the current IP address (dynamic) by connecting the server directly to the broadband router, but I cannot set up DNS (ddclient on the server, Namecheap for domain registrar and nameserver) with it. I can set up DNS on the router with no issue, as it has the DNS client built in, but I cannot get the SHH to connect through both the modem and the router as mentioned above. Best case scenario, this can be fixed without having to get anything new, but if that is the case, recommendations of a new setup that could solve this issue would be greatly appreciated. 

Other reference info - ISP at server is Verizon Fios, broadband router set to PPPoE.

Why do you have two routers?  Can your wireless router not handle the pppoe?  It is a pain to set up two routers properly if you do not need to.  Also if you are just looking to add wireless connectivity to the DI-604 you can normally plug an cat5 cable from router to the switch section of your wireless router.  
More info please.

---

