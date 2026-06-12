---
title: "djbdns set up tinydns with the Ubuntu packages?"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by mdlueck on 2010-02-07
Greetings:

Ubuntu server 9.04

I managed to get dnscache working, with the one remaining detail that I need to start the daemontools service manually for now. I added starting that service to /etc/rc.local which will do for now.

Enough accounts were installed / configured by the packages get dnscache operating.

Next up I need to configure tinydns. The needed account to get tinydns working was NOT created when installing djbdns. The tinydns-conf instructions specify to use account: Gtinydns.

Has anyone else had success getting tinydns running via the Ubuntu packages?

Thanks,

---

### Post by mdlueck on 2010-09-15
I forgot I asked this question here... Problem solved, and I posted to our blog a HOW-TO about djbdns on Ubuntu 9.04, 9.10, and 10.04. You may find it here:

"HOW-TO: Basic installation of Daniel J. Bernstein's djbdns (TinyDNS) on Ubuntu Linux"
[http://www.lueckdatasystems.com/HOW-TO_Basic_installation_of_Daniel_J_Bernstein_djbdns_TinyDNS_on_Ubuntu_Linux](http://www.lueckdatasystems.com/HOW-TO_Basic_installation_of_Daniel_J_Bernstein_djbdns_TinyDNS_on_Ubuntu_Linux)

Sincerely,

---

