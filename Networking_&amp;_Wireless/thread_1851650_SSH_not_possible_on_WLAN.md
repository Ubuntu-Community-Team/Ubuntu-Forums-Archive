---
title: "SSH not possible on WLAN"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by Lisiano on 2011-09-28
Okay, so today I was setting up a laptop with my cousin for our grandma to use (Web surfing for news). While we were setting it up, I added OpenSSH-Server to make the configuration part more parallel and also ease future administration. The problem is that for some unknown reason, I couldn't SSH into the laptop. Also Telnet to port 22. I tried it these ways.

Laptop <-> My netbook
Cousins phone -> Laptop
Cousins phone -> My netbook

No route worked, both my netbook and the laptop have OpenSSH-Server installed, also sshing to localhost works, using a IPv4-to-IPv6 tunnel works using a IPv6 client I used remotely (Home PC). Also I know the phone and netbook work normally when on either my cousins WiFi or mine.

Now for the weird part, I used ping, telnet and ssh. All gave me "No route to host"/"Destination unreachable". 

So, can anyone shoot me with some possibilities, I don't care if they might be easy or hard. As long as this will help me understand why on earth I can't communicate with anything on my grandmas network.

---

### Post by Lisiano on 2011-10-05
*Bumper*

---

### Post by apmcd47 on 2011-10-05
Stupid questions, but are both machines properly on the network? Can you ping the router from both machines fmachine names or IP addresses in your experiments? If names, are they mapped onto the correct IP addresses?

Andrew

---

### Post by Lisiano on 2011-10-07
I didn't use names in my experiment, don't like them, just IPs. I didn't try pinging the router but it did refuse to ping between any of the 3 devices, I'll go and take try pinging the router though, also try tracerouting my netbook and the laptop.

Also the IPs are assigned via DHCP.

---

### Post by Lisiano on 2011-10-07
Okay. So pings and traceroute go through.

Oddly, connecting to devices on the WLAN now work. I have no idea what changed but marking this as solved.

---

