---
title: "snmpv1 works but snmpv3 doesn't"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by Doc_symbiosis on 2010-03-16
Hi there,

I've got a little problem and don't see any way out.
Situation is: I've got two server (let's assume A and B).

A is running snmp-daemon. Now on server A snmpv1 and v3 requests work fine on the DNS-name of the server.

But when I run snmpget on server B, only the snmpv1 requests succeed, but the snmpv3 requests fail.

I already tried the NoAuthNoPriv security level for version3 but this also made no change.

Anyone got a clue, what the problem is?

By the way. server A is running on Solaris 10, but I think, this shouldn't have to do anything with the problem.

---

