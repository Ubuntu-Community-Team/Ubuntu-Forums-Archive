---
title: "I need it at work please help :("
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by ibrahim.k on 2009-12-01
Hi!
I have a desktop computer with 9.10 installed on it and on that desktop i have two ethernet cards and i need to bridge these connections how can i do this please ?

auto eth0
auto eth1

switch      ----->  auto eth1
auto eth0 -----> laptop


thank you guys

---

### Post by doas777 on 2009-12-01
this should get you going in the right direction:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

at a minimum, all you need is a route established, between the two networks established on your box, but there are a lot of other things that may or may not need be configured.
are you comfortable with static IP configuration, routing, and firewalls?

---

