---
title: "Setting up and Old Machine as a firewall"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by TheEndIsNear on 2010-10-12
I have a quick question, I have installed Ubuntu 10.04 Server on an older desktop with the intent of making it into a firewall box. What I would like to do is hook one nic into the modem, and the other nic into my router. I'm not sure if I want to setup the 2 nics as bridged. Any help would be appreciated.

Thanks,
TheEndIsNear

---

### Post by SeijiSensei on 2010-10-12
I'd give the internal interface an address in the officially-designated private blocks described in [RFC1918]("http://www.ietf.org/rfc/rfc1918.txt").  192.168.1.1 is a common choice.  

There are plenty of guides out there on how to build a simple firewalling router with iptables and "masquerading."  This is probably as good a place to start as any: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo).

I never use bridging.  I much prefer having all my network segments in separate address blocks with clear rules set up to control the flow of packets among them.

---

