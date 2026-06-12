---
title: "iptables and LSI"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by W03L on 2009-06-26
Hi.
Tell me, please, what is LSI in iptables and what is different between INBOUND and INPUT.
thanks.

---

### Post by slugmax on 2009-07-09
LSI is firestarter's "Log and Stop Input" chain. INBOUND is typically a user-defined chain used to grab inbound traffic. INPUT is a pre-defined chain that sees packets destined for the firewall itself.

---

