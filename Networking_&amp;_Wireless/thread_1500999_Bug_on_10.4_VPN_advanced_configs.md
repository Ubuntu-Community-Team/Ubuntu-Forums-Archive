---
title: "Bug on 10.4 VPN advanced configs?"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by Pazin~ on 2010-06-03
Hi !

I think I found a bug on VPN advanced configurations.
To connect to my company's VPN I have to leave only the MSCHAPv2 checked on the authentication method and it was working fine under ubuntu 9.10.

Now I have this behaviour:

[IMG]http://i46.tinypic.com/j59p2b.jpg[/IMG]

[IMG]http://i47.tinypic.com/25psqs9.png[/IMG]

Checking on Log messages when trying to connect to my VPN shows me that NM doesn't save correctly as it insists in use PAP authentication.


I never posted a bug on launchpad before so... can some of you guys confirm if this happens too?

Thank you.


EDIT: NEVERMIND... I'm dumb. If I click on "Use point-to-point encryption MPEE" it works fine.  ](*,)

---

