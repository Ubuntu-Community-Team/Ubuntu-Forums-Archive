---
title: "eth2 interface problem"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by zee on 2012-05-14
Hi.
  Soon after the release of Ubuntu 12.04 I had my faulty workstation replaced with a new one with the exact same configuration.

  After the first boot I erased the files /et/udev/rules.d/70-persistent-net.rules, so this file can be generated at next boot (as it was the case in the past and on other distros). Something went wrong as the eth2 interface is still listed as installed (along with eth0 and eth1) despite the fact I have only two physical ethernet ports.

  How do I fix this? This interface is also causing very long boot times as it apparently waits for the IP address from the DHCP server.

Any advice not involving a reinstall will be greatly appreciated.

tnx,
zee

EDIT:
A complete reinstall did the thing + solved the slow boot problem.

---

