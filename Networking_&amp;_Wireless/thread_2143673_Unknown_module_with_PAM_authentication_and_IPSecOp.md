---
title: "Unknown module with PAM authentication and IPSec/OpenSwan VPN on 12.10"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by justinmiller621 on 2013-05-09
I have setup a VPN on my home Ubuntu 12.10 server using instructions found here using CHAP authentication:

[https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.10.html](https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.10.html)

I'd like to now change this to use PAM, so I followed the relevant instructions. And this is what I get in my syslog:

```
May  7 09:08:41 myhost pppd[27235]: Attempting PAM authentication
...
May  7 09:08:41 myhost pppd[27235]: PAM Authentication OK for someuser
May  7 09:08:41 myhost pppd[27235]: Attempting PAM account checks
May  7 09:08:41 myhost pppd[27235]: PAM Account checks failed: 28: Module is unknown
May  7 09:08:41 myhost pppd[27235]: PAP peer authentication failed for someuser

```

I've looked everywhere for this and can't find any info on it. I even searched for PAM error codes, found the relevant one, but no information on how to fix it.

Thanks, Justin

---

