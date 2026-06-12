---
title: "ssh not working, ports not open, tcp diallow for lucid lynx"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by mrstoney on 2010-05-07
I've installed a fresh copy of the latest 10.04 distro, lucid lynx and have problems connecting to the machine via ssh because the ports are all blocked (using nmap to check).

In past releases, changing the gdm.conf flag "TCPDISALLOW" from true to false would fix this.  In the new /etc/gdm/gdm.schemas, I've tried making a similar change, but it's still not opening things up.

I've downloaded gufw and have made sure the firewall is off.  So, I'm not sure what to try next.

Does anyone have any suggestions on how to troubleshoot this?

---

### Post by mrstoney on 2010-05-10
Ah, as it turns out, openssh_server is not installed by default.  That fixed it.

---

