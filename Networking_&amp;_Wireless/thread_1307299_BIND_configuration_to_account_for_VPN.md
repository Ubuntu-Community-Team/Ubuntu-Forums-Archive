---
title: "BIND configuration to account for VPN"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by slavik on 2009-10-31
I am trying to figure out how to get bind to do the following:

VPN active:
use internal DNS servers (192.168 addresses)

VPN inactive:
use external DNS server

The above is used to only search within two domains.
vpnc is used for VPN.

One idea is to have a wrapper script, maintain 2 copies of the options files and create a symlink to the proper file when vpn is being activated/deactivated. The problem with this approach is that VPN can sometimes simply die.

Since bind does not have a way to prioritize DNS servers, are there other options that are available?

---

