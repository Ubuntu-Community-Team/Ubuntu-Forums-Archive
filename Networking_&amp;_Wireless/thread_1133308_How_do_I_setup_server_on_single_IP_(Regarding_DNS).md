---
title: "How do I setup server on single IP (Regarding DNS)"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by CyberMick on 2009-04-22
Just wondering how I would go about setting up a simple server regarding DNS implementation(for web and e-mail mostly, very small user base).
I will have access to one single public static IP. Given that DNS Registrars require two (different) nameservers, it seems i won't be able to host my own DNS to adjust the host and MX records to start with.
Is there a simple solution for this or would I better to just shell out extra and pay for managed DNS?

---

### Post by puppywhacker on 2009-04-23
Find a secondary dns host, either from a friendly person willing to put up a zone for you, or find a service like dyndns to host the secondary (or just the full domain)

[https://www.dyndns.com/services/dns/secdns/howto.html](https://www.dyndns.com/services/dns/secdns/howto.html)

I'm a happy customer for 7 years now, they are very reliable, they have good tutorials and fair prices

---

