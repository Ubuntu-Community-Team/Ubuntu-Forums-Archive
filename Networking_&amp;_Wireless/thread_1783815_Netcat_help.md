---
title: "Netcat help"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by icmdwilliams on 2011-06-16
Hi guys, I'm in real need of some help. I'm not good with ubuntu at all but I am trying to get better.
 
I have an issue with asterisk & multiple sip trunks, the problem being that asterisk assumes that the last trunk to register against an IP address is the one that owns that ip address, this would be fine for trunks to multiple sip trunk suppliers, but the problem comes when you use the same provider for multiple trunks.
 
Anyhow with a bit of research (and askign friends) I was pointed in the direction of netcat. 
 
What I want to do is specify additional local IP address (10.0.0.1) against my nic then set the sip registration to point to that ip address then netcat to forward all the traffic from that ip address to my sip provider (xxx.xxx.xxx.xxx) and the traffic that is returned from the sip provider back to 10.0.0.1 
 
so it's 
 
asterisk-box <-----> 10.0.0.1 <-------> xxx.xxx.xxx.xxx
 
I hope that makes sense and someone can help me.
 
Regards
 
Dave.

---

