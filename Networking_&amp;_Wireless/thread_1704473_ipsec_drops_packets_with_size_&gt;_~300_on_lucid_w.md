---
title: "ipsec drops packets with size &gt; ~300 on lucid with 2.6.35"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by rhuddusa on 2011-03-10
running 64bit ubuntu lucid on pvgrub, using racoon and ipsec-tools. 
 
upgraded from standard 2.6.32 kernel to  
linux-headers-virtual-lts-backport-maverick (2.6.35). 
 
under 2.6.35, ipsec fails to process any packets with size > ~300  bytes.  this was tested for pings, udp, and tcp traffic.  also tested  were different encryption / authentication schemes, including null  schemes.   
 
ifconfig doesn't show any errors, and tcpdump shows esp/ah packets  arriving at eth0, but disappearing after that.  i was unable to find any  logs or stats to indicated where the packets were going. 
 
it was only receiving packets that dissapeared.  i was able to send esp/ah packets as normal bytes. 
 
i ended up reverting back to 2.6.32 after trying for several days to  diagnose the problem.  everything is working again under 2.6.32. 
 
any thoughts? ... kernel bug?

---

