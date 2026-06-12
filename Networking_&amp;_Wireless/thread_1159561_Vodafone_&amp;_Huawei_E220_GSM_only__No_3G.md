---
title: "Vodafone &amp; Huawei E220 GSM only ? No 3G ?"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by laffinet on 2009-05-14
Hi !

I'm trying to connect to Vodafone mobile broadband using the supplied Huawei E220. Network Manager recognised it out of the box, but it only connects via GSM, which is very slow. How do I get it to connect via 3G ?

I know there's a vodafone application to handle this modem, but I haven't been able to get that to work yet (something wrong with folder permissions), so my preference is to use Network Manager only. 

So, how do I configure Network Manager to connect via 3G, not GSM.

BTW: the Vodafone map shows that I have plenty of 3G coverage, so that shouldn't be the issue.

---

### Post by GeorgeVita on 2009-05-15
Hi **laffinet**,

Huawei modems blink in green color when they found a GPRS network.
Blinking in blue color means that a 3G or 3G+ found.
Blinking twice means that you (your SIM) cannot connect with the network found.

You can check all above without running any s/w, just by powering the modem via a USB port.

Try connecting after the blinking blue condition.

Have you been connected in a stable 3G condition with the same h/w (modem, pc) but with other O.S.?
Check also if you can "force" a 3G only state via the Vodafone's application s/w and then try again ubuntu.

Regards,
George

---

### Post by laffinet on 2009-05-17
I've managed to get the vodafone software working (by properly uninstalling the beta 2 version and then installing an older version) and everything is working fine now. Thanks for the reply.

---

