---
title: "Error: &quot;SIOCSIFADDR: Cannot allocate memory&quot; adding virtual IPv6 Addresses"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by janneaa on 2010-04-30
I get errors trying to virtual IPv6 Addresses i a lab environment. It works fine up to 2033 (?) adrressses, but when I try to add more i get "Cannot allocate memory" error:

# ifconfig eth0 add 2001:1b70:8282:2021:18:0:20:1
SIOCSIFADDR: Cannot allocate memory

This is on Ubuntu Server 9.10 (64-bit).

Any ideas on why we run into this limitation? Any kernel parameters that can be changed?

/Janne

---

