---
title: "limiting download on shared ADSL"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by kevindontenville on 2009-11-30
Hi

Can't quite find what I want on previous responses to similar questions. 

What I want to do is allow a quota of download capacity to IP addresses on my LAN and not limit speed.

Essentially, a specific individual or range of IPs on the network would have, eg 5GB of download in a given period. I don't want traffic shaping in the form of limiting speed to achieve that just simply when they hit 5GB of traffic then they get no more access through the gateway.

Happy to have a server running as a gateway and control it there, but I stress I don't want Proxy based access controls. This should be a simple accounting issue and I would have thought it would be easy to do, but either my search terms are poor or it is not something people want to do... 

Or perhaps others don't have download hungry teens!

Any help?

Thanks!

---

### Post by Fire_Chief on 2009-11-30
I don't think this is the best solution for you but found it and it looked interesting.
[http://www.unix.com/ubuntu/95552-download-quotas-users-2.html]("http://www.unix.com/ubuntu/95552-download-quotas-users-2.html")

Cheers,

---

### Post by kevindontenville on 2009-11-30
Thanks that is interesting, reborg looks like a scarily quick coder! The basic premise there is that it is a single PC that links the users on that PC to a limit. My issue is IP based, I prefer to configure controls over NICs and IP addresses, user based limits are not useful in may case. 

Mastershaper sort of gets close but not quite and they seem a little undeveloped recently although Mastershaper is maintained.

It seems such a simple thing but not one found implemented anywhere. Some have done similar via proxy or via http only but I don't want to be so specific or introduce a proxy.

Thanks for the suggestion though, not one I had found. 

Any others very welcome!

K

---

