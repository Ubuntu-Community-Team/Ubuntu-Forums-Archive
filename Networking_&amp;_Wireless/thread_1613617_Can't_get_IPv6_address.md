---
title: "Can't get IPv6 address"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by webappl on 2010-11-04
Hi everyone,

I have a networking problem with my computer.
Under Windows, the computer can get both v4 and v6 address via DHCP. However, the same computer can only get v4 address under Ubuntu. Does anybody know how to solve this problem?
Thanks.

Alex

---

### Post by ratcheer on 2010-11-04
Look in the Network Tools applet. Select the "Ethernet interface" network device.

Tim

---

### Post by webappl on 2010-11-04
> **ratcheer said:**
> Look in the Network Tools applet. Select the "Ethernet interface" network device.

Tim

Hi Tim,
When I selected 'Ethernet interface' and clicked Configure, I only saw 'auto eth1' and 'auto usb0' from the Wired tab, neither of which is corresponding to eth0 connected with network cable. What Can I do next?

---

### Post by lemming465 on 2010-11-13
First, which version of Ubuntu are you running? ("cat /etc/lsb-release").  Second, could we see the output of "ip addr show"?

---

