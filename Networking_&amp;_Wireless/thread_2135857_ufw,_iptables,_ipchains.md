---
title: "ufw, iptables, ipchains"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by pponchot on 2013-04-15
I have a server that I inherited.  The server apparently redirects network traffic to the internet.  When using a browser from another computer a web page appears with a place to click the agreement to the rules and then redirects to the network.  The redirection lasts 2 hours and then resets.

I've checked and apparently ufw is not setup (status - inactive).  When I run iptables -L, I see a lot of traffic happening so I think the server is using iptables which as I understand can be formulated by many front end programs.  

I understand Simple Masquerading but I'm still struggling to understand how all this works.   I checked the Services but did not see anything that would give me a hint.  I also checked the processes. 

The server is all command line driven, so if anyone has any ideas, please spit them out (smile). 

Phillip

---

### Post by Doug S on 2013-04-15
Could you tell us what you want to do? Do you want to change the iptables rule set to eliminate the 2 hour thing or disable them entirely? Determine if some other front end program is involved?
Perhaps post your iptables rule set (the output from "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L" or just "sudo iptables-save -c").

---

