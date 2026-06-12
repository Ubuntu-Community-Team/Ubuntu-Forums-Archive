---
title: "Setting up plain gateway without NAT or port forwarding"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by pslikesrouters on 2010-08-24
Help please. We seme to be stuck and are feeling like we are missing something obvious.
 
Situation:
1 "main" IP: 216.x.x.100
1 "main" ISP gateway: 216.x.x.1
15 publicly accessible IPs: 66.x.x.101-115 (yes, they are publicly available but have no gateway within their range)
(none of this can be changed, and my ISP assures me this is very common practice)
 
So we are setting up a gateway at our main 216...100 IP, can ubuntu support this? If so, what are the steps to do it?
 
Remember, this isn't a typical NAT as the packet will come in go via 216...100 to 66...100. It has to be like a gateway as our ISP will have a static route of our 66. packets going to the 216.x.x.100 as if its a gateway.

---

