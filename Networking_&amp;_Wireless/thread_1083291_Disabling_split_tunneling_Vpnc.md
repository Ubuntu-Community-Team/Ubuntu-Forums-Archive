---
title: "Disabling split tunneling Vpnc"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by ww39932 on 2009-02-28
Hello

I am currently using Vpnc version 0.5.1 connecting to a remote location. Vpnc connects fine and everything works, but in my case there is one problem, i can still ping and talk to the devices on my private network, i want ALL my traffic to be routed to the remote location. I have searched Google for help but all results are regarding enabling split tunneling which is the opposite of what i want. I have also tried to create a wrapper script for Vpnc with the line CISCO_SPLIT_INC=0 but no luck.

Is it possible for anybody to give me a clue on configuring Vpnc so all my traffic is sent to the remote location?

The operating systems is Ubuntu 8.10 fully updated. I have uninstalled Network-manager and Network-manager-gnome, and using /etc/network/interfaces to configure the network interfaces.

---

