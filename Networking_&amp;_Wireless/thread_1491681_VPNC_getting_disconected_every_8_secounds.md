---
title: "VPNC getting disconected every 8 secounds"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by 3junior on 2010-05-23
Has this issue been resolved yet?  [http://ubuntuforums.org/showthread.php?t=441042&page=7](http://ubuntuforums.org/showthread.php?t=441042&page=7)     Re: Using vpnc to connect to Nortel Contivity VPN Quote: Originally Posted by irregardlessly View Post I have the same problem. Let me know if you figure this out. Quote: Originally Posted by oldcyberdude View Post Check this posting [http://lists.unix-ag.uni-kl.de/piper...st/001647.html](http://lists.unix-ag.uni-kl.de/piper...st/001647.html)  &quot;vpnc currently only supports aggressive mode (3 packet exchange), not the alternative main mode (6 packet exchange). This makes sense, because unless you use certificates for Phase I authentication, main mode won't work. And certificates are not (yet) supported (see TODO). I hope this explains this a bit. So it's most likely not working because the concentrator uses a mode that is not supported by vpnc.&quot;  I don't quite understand this comment but doesn't sound good irregardlessly: probably that's the problem, vpnc does not support yet the authentication method that the routers we're trying to connect! that's the reason why vpnc worked for some, failed for others...

---

### Post by 3junior on 2010-05-24
Can anyone help?

---

