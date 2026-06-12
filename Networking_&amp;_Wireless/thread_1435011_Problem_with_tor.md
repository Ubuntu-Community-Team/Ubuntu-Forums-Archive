---
title: "Problem with tor"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-03-21
Hi everyone.

I installed tor and updated it. Works fine in my Firefox with Tor Button. 

I fired up wireshark today to play with it, and noticed that even with Tor "off" in my browser, and the computer idle, tor seems to be firing off all kinds of noise. Something called the 'etlservicemgr' seems to be sending a lot of traffic. I also see a lot of "Continuation or non-HTTP traffic" to a tor-relay site.

Could someone help explain what's going on, and what this etlservicemngr is? I have tried researching what etlservicemgr is, but I can find barely anything, other than it operates on port 9001.

Thank you.

---

### Post by jfparis on 2010-03-21
Tor runs as a service in the background. When firefox says it is disabled it simply does not use tor but tor is still here.

As a service tor maintains connections with other nodes in the network. It won't open a new connection each time you uses it. Otherwise that would be too easy to track you activity.

I believe there is nothing to worry about. 

That being said you might also have configured your tor to act as a relay in the tor network. That would mean higher traffic as your node is routing data for other users. That consumes more bandwidth but I believe that also makes your configuration more anonymous.

jf

---

