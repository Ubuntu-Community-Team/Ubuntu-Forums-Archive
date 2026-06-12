---
title: "Port 80 blocked in new 14.04 installation"
date: 2015-04-06
forum: Mythbuntu
---

### Post by philled on 2015-04-06
I have been running MythBuntu 12.04 for some time. As part of my set up I have a DMZ which takes an HTTP request from the internet and uses the apache ProxyPass directive to pass the request on to Mythweb. 

I have just replaced by 12.04 Mythbackend with a new Mythbackend based on Mythbuntu 14.04. Mythweb is working when I call it from my internal LAN, but I can't access it from the internet. When I log onto the DMZ box (which is on a different subnet) and telnet to port 80 on my new 14.04 Mythbackend machine the connection times out, whereas it used to connect on my old 12.04 installation. So there must be somewhere where I can tell the new 14.04 machine to accept connections on port 80 from the DMZ. I must have done that on the old machine but I can't remember where (but I do know it wasn't hosts.allow or hosts.deny). 

Can anyone point me in the right direction, please?

---

### Post by TheFu on 2015-04-06
Did the server IP address change? Perhaps the router forwarding ports isn't going to the correct place anymore?

---

### Post by philled on 2015-04-06
> **TheFu said:**
> Did the server IP address change? Perhaps the router forwarding ports isn't going to the correct place anymore?

No it didn't change. The old machine had an IP address of 192.168.0.120 and so does the new one (obviously I'm not running the old machine any more). I'm 99% sure that the block is happening on the machine running Mythbackend and Mythweb. If I close the new machine and fire up the old one I can telnet to 192.168.0.120 80 from the DMZ. But when I shut down the old machine and start the new one I can't telnet to 192.168.0.120 80. So there's something I need to configure on the machine to allow the connection from the DMZ but I can't work out where or what that setting is.

---

### Post by khPWXxF on 2015-04-07
Your IP address has not changed but your Mac address has.  Have you rebooted your network hardware?
Phil

---

### Post by philled on 2015-04-08
> **khPWXxF said:**
> Your IP address has not changed but your Mac address has.  Have you rebooted your network hardware?
I have just rebooted my network hardware (which by the way is a Sophos UTM VM), but I still can't telnet to 192.168.0.120 80. I can, however, telnet to 192.168.0.99 80 (this is the new IP address of the old machine). So I'm convinced that there's a config on the server I need to set to allow traffic in on port 80 from the DMZ. That setting must have been made on the old machine, but I can't remember what it was.

---

### Post by philled on 2015-04-08
I've solved the problem! Thanks for the pointer to the network hardware. That got me thinking and I eventually tracked the problem down to Sophos > Network Protection > Firewall > Rules. I needed to add a new rule for the new Mythbackend machine as the existing rule had automatically take into account the new IP address for the old machine. Thanks for your help along the way.

---

