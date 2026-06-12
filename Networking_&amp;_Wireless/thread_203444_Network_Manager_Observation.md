---
title: "Network Manager Observation"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by phillip181 on 2006-06-25
I know some of us out there have had an issue with Network Manager where we cannot connect with free networks that don't require a password like hotels and coffeshops but can connect to networks that require a WPA or WEP. 

One thing that I noticed was that when trying to connect to one of these free networks, I will get a full signal on the Network Interface applet, but it won't connect fully. When running the Nm display tool on terminal, It will indicate that it is the current network, but won't show IP addresses. I am wondering if it is just the DHCP not working without a WEP or WPA. 

Just some thoughts.

---

### Post by queenorych on 2006-06-25
I have an rt2500, and found that while nm was "trying" to connect to an open network, if I ran dhclient ra0, it would get an ip address and work.  Eventually nm would give up, and close the connection.  So I agree that dhcp is a problem.  More receintly I retried nm, and found that it would not conenct, and something prevented me from conencted even after I disabled nm.  It wasn't until I reloaded the module that I was able to connect using good old iwconfig.

---

