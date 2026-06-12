---
title: "umts ports problem?"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by userid on 2009-08-10
I am using a Huawei UMTS modem, everything worked beautifully out of the box via network-manager, but for some reason I can only surf the web (http) on port 80.

SSL sites, ssh connections, IRC, Skype etc, or IMAP fail to connect. Ping from terminal does not work either.

The provider does not block any ports.

I have already attempted using firestarter to reset iptables to no avail.


Grateful for any ideas, thanks for your attention.

---

### Post by userid on 2009-08-10
Problem solved by "turning off" firewall in firestarter, then restarting once skype and msn connection was established. go figure..

---

