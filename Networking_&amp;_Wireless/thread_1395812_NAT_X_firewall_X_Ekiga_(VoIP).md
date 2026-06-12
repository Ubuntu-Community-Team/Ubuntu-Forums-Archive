---
title: "NAT X firewall X Ekiga (VoIP)"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by kapetr on 2010-02-01
Hello,

I can not break in Ekiga :-(

I'm connected to the Internet with ADSL ZyXEL router.

- If it is in BRIDGE mode - and then my PC has a public address via PPPoE, so it goes, but
- in ROUTE mode - that is, with NAT and firewall, than is it bad:

no, and no break in it.

I was looking at [http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router)

but after cup of failed attempts, I resigned and I did:

- stop Ubuntu FW with: "service ufw stop" and
- On the ZyXEL firewall also stopped and
- In his setup NAT> Port Forwarding-> Server Default entered my LAN address.
- with Portmap from outside then I had verify that my system has the door ajar

ekiga but not and not going!

SIP accounts registration goes OK, but no call does start with the message: "user unavailable"

Note: in Ekida is enabled "network auto detection", so STUN server should probably make his work.

What the hell Ekida may still want?

Thanks all and sorry please my english

--kapetr

---

### Post by kapetr on 2010-02-02
I have now try to run (live CD) with Ubuntu 6.06 LTS.

Here is **Ekiga 2.0.1** and is _working_

Behind of: ufw, ZyXELs fw and ZyXELs NAT - without any kind of configuration (port forwarding, etc ...).

Also it seems to be a problem in Karmic or Ekiga itself.

I out there someone using Ekiga in U9.10 behind NAT modem (ADSL) ???

--kapetr

---

### Post by YannickDefais on 2010-04-05
Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)

Best regards,
Yannick

---

