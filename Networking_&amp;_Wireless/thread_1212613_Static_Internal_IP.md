---
title: "Static Internal IP"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Broomhead on 2009-07-13
Ok so I've been trying to get this to work all day and I haven't found anything, here's my network setup:
My cable (comcast) modem connects to my airport extreme, my ubuntu server is connected to the airport via an ethernet cable and then i have 5 or so computers (macs) connecting to the wireless network from the airport. I'm trying to assign a static IP to my server, on my mac the only way I've been able to assign a static IP is to choose the option Configure IPv4 using DHCP with a manual address, using the manual option doesn't work. 

Is there any way I can configure my network settings on my server to do something similar to that?
If not, is there any other fix?

---

### Post by tomdagreek on 2009-07-13
i am not familar with the airport but there should be a option to give it a static ip (lan wise) by putting the mac address of the server in the router. From my exp with linksys routers u can assign a static lan ip from your router.

---

### Post by tomdagreek on 2009-07-13
have u tried to config a static ip under connections and just use a local ip?

---

### Post by Broomhead on 2009-07-14
Ok someone on the apple forums helped me, it's in the airport utility settings, a dhcp reservation feature

---

### Post by bemental on 2011-10-29
> **Broomhead said:**
> Ok someone on the apple forums helped me, it's in the airport utility settings, a dhcp reservation feature

Airport Utility -> AirPort -> DHCP -> DHCP Reservations

Gives you the option to input MAC address or DHCP Client ID.

---

