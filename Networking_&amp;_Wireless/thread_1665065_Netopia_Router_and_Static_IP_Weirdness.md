---
title: "Netopia Router and Static IP Weirdness"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by nlk10010 on 2011-01-11
I've got a very weird situation.

I have a block of static IPs from my ISP. The incoming cable feeds through the ISPs Cisco router and into my NETOPIA WAN port. In Netopia config we had the WAN address set to one of the static IPs (say .158 ) and use a Netopia Server map to allow external RDP access (port 3389) to each of two internal servers (one a DC, one a TS). 158 goes to one machine, 159 to another (by specifying Port 3389). There are other settings but these seem to be the important ones. 

Everything was working fine and then, all of a sudden (no configuration changes), the Internet became impossibly slow and I could no longer access the 158 address via RDP from outside the network. The connection simply hung. 159 worked fine (note that 158 is also specified as the WAN address). However, I COULD use RDP from INSIDE the network (to both 158 and 159). When I pinged 158 from outside the network  I got a return from a different IP (seems to be the ISP's). Pinging 159 was no problem. 

IOW, it seemed for some reason that traffic was NOT being let in through 158. I'm not sure but that's what it seems. As an experiment I simply replaced the 158 address with a 161 address (i.e. specified it as both the WAN port AND added a server entry to direct 3389 access to my TS machine). NOW it works fine. Internet and external RDP to both computers. HOWEVER, I'm concerned and curious why this change was necessary. I'd really like to know (and learn) what this set of symptoms seems to point to. I'd LIKE to go back to the original configuration but won't until I can figure out what happened.

Any ideas would be very much appreciated.

---

