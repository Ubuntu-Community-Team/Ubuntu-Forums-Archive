---
title: "Connected to Resara then lost firefox"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by theller on 2011-08-05
I set up [Resara]("http://resara.org/") and I am using an external DHCP server. Windows machines are on this network and use the same DHCP server but they are not connected to Resara. The server that has resara on it can get to the internet, and if I add a windows machine to the Resara domain it will get to the internet so I think the server is set up correctly. 

The Ubuntu client has the problems. It will connect to the internet if it is not in the Resara domain but when I change the networking to DHCP(addresses only) and add the resara address as the DNS (Likewise is used to connect) then no internet. I can ping any machine in the building just not outside.

I really think this is just as .conf file needs to be tweeked but I don't know where to start. Something with the network connections maybe? If I can answer any questions to clarify or post anything just ask.

---

### Post by theller on 2011-08-14
I got internet!! I just had to tweak the network manager file and now it connects.

---

