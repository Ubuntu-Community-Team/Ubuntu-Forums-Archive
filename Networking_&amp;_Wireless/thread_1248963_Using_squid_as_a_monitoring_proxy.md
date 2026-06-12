---
title: "Using squid as a monitoring proxy"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by carlnielsen on 2009-08-24
I have set up an xubuntu machine in my office environment as a server. The other machines (of which there are 4 and one virtual machine) all run Windows XP. I am keen to be able to monitor all internet traffic into and out of the network and to this end have set up squid on the xubuntu server. I have set the proxy settings on the office machines to go through squid. I wanted to force all traffic through squid, so I set up firewall rules on my router to only allow outbound connections from the server. This work well: PC's cannot connect to the internet unless they are set to use the proxy.

My problem comes with email, where it seems, from my reading, that pop3 cannot pass through squid and it is a bad idea to push smtp through squid. From what I can tell, the mail clients bypass the proxy (they won't work when the firewall rules are blocking direct connections to the internet are on).

Am I missing something here? Is there any way to get all internet traffic to be recorded by squid? Is this in fact happening and I just don't realise it (I haven't gotten into checking the actual squid logs yet).

Any help, explanations and comments would be welcomed.

---

