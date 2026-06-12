---
title: "DNS reverse lookup help"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by puelly on 2009-05-03
Hey Guys,

I need a little extra help to complete a reverse DNS project.  I have correctly configured two public DNS servers, master and slave, to resolve forward and reverse domains and I'd like the "internet" to know to use these machines for the reverse lookup.  I have recently (not yet 24hrs) submitted the reverse DNS server info to ARIN for the public address space we have assigned.

Is there anything else that I need to do?

Any assistance would be appreciated.

Thanks.

Richard

---

### Post by ejschaefer on 2009-05-03
Hi Richard, 

You will need to ensure that the following are true:

1. Your DNS servers are publicly accessible for DNS resolution.

2. You have an in-addr.arpa DNS zone for your IPs (ie. if your IP is 192.168.1.1, you need a zone "1.168.192.in-addr.arpa" that contains a PTR record for "1".

3. Your DNS servers are delegated for resolving reverse lookups for your IPs

If those are true, you should be good to go.

---

### Post by puelly on 2009-05-03
Thanks. Looks like I have to have some patience then. :)

---

