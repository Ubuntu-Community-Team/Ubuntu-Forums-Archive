---
title: "Intermittently Able To Ping In/Out"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by inter5 on 2012-09-06
Hello all,

I'm running into a strange networking issue on a fresh install of server 10.04.4. 

Initially,  I had a static IP set up on eth1 and wasn't able to ping anything on  the LAN or internet. After check and rechecking that I entered the  correct information for the interface, I switched the ethernet cable to  eth0, updated the relevant information, and restarted networking. At  this point, I was able to ping on the LAN and was able to ping a server  on the internet, but wasn't able to receive a response.

Suddenly,  after switching interfaces a couple more times to see the result, I'm  able to send and receive pings from the LAN and internet but it only  appears to work intermittently.

Since I really didn't do anything  but switch the interfaces a couple of times, I'm a bit stumped as to what the actual problem/fix was and am afraid I won't have a concrete way to  fix it if it happens again. 

Any ideas?

---

### Post by inter5 on 2012-09-07
After doing a little more testing, I'm able to plug in a Windows laptop with the same switch port/cable/IP and have no issues at all. 
 
Anyone have any ideas? I'm really interested in finding an answer.

---

### Post by inter5 on 2012-09-07
Next update...
 
Ethernet cable is plugged into eth0, route -n shows the correct default gateway, yet I'm unable to ping past the gateway.
 
After a bit more research I decided to take a shot in the dark and ran "route add default gw XX.XX.XX.XX" which to my surprise allowed me to ping past the gateway. The strange part though is that route -n shows the command added the gateway for eth1 which isn't in use and the only difference between the eth0 and eth1 lines is that eth0 has a metric of 100 and eth1 has a metric of 0.
 
Thoroughly stumped.

---

