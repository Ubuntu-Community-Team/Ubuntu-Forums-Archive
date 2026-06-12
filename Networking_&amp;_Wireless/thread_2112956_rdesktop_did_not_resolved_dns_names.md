---
title: "rdesktop did not resolved dns names"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by nsk7even on 2013-02-06
Hi all,

just wondering why on one of my systems rdesktop was not be able to resolve dns names.

The error message was "ERROR: getaddrinfo: could not resolve by name... or similar (it was in german for me)".

The solution to stop avahi daemon did not worked for me!

After comparing my two machines I found a difference: the working system had a configuration file /etc/resolvconf/resolv.conf.d/original, which was missing on the other system!

The content of this file did include the following lines:
search sub.domain.one domain.one domain.two
nameserver ip-address-of-first-nameserver
nameserver ip-address-of-second-nameserver

After creating this file with this content rdesktop works now on both systems! Solved!

I just wonder why?

So let me give you some environmental infos...
Both systems are Ubuntu 12.04.2 LTS 64 Bit, running on kernel 3.2.0-37-generic.
Network was configured on both systems via network-manager that is accessed via classic gnome-panel from Gnome 3 Fallback Mode.
BUT on both systems I configured only the primary dns server via network-manager while this mysterious "original" file contains the secondary dns server as well!

So how and who configured this file?
May I assume that using only network-manager rdesktop will never work?

Ah and one thing I noticed:
nslookup is able to resolve dns names
dig is NOT able to do this
Whats going on here?

Regards,
Nicolas

---

### Post by jdthood on 2013-02-06
> **nsk7even said:**
> 
After comparing my two machines I found a difference: the working system had a configuration file /etc/resolvconf/resolv.conf.d/original, which was missing on the other system!

The content of this file did include the following lines:
search sub.domain.one domain.one domain.two
nameserver ip-address-of-first-nameserver
nameserver ip-address-of-second-nameserver

After creating this file with this content rdesktop works now on both systems! Solved!

I just wonder why?


When an Ubuntu system is upgraded to 12.04 or higher the original static /etc/resolv.conf file gets moved to /etc/resolvconf/resolv.conf.d/original which gets included in the *dynamic* resolv.conf file which resolvconf generates.

What you as system administrator are supposed to do next is move the information from that file into the correct location. If the interface over which you reach the nameserver is configured with DHCP and the nameserver address comes in during DHCP negotiation then you don't need to do anything. If you are using ifup to configure interfaces statically then the correct location is the /etc/network/interfaces file: you add "dns-nameservers" and "dns-search" lines to the relevant stanza in that file. If you are using NetworkManager then the information should be entered into the connection definition using the NetworkManager Connection Editor. Please see resolvconf(8) for more information. After you have configured ifup or NetworkManager properly you should "ln -sf /dev/null /etc/resolvconf/resolv.conf.d/tail" so that the original file won't get included in resolv.conf any longer.

> 
So let me give you some environmental infos...
Both systems are Ubuntu 12.04.2 LTS 64 Bit, running on kernel 3.2.0-37-generic.
Network was configured on both systems via network-manager that is accessed via classic gnome-panel from Gnome 3 Fallback Mode.
BUT on both systems I configured only the primary dns server via network-manager while this mysterious "original" file contains the secondary dns server as well!

So how and who configured this file?
May I assume that using only network-manager rdesktop will never work?

Ah and one thing I noticed:
nslookup is able to resolve dns names
dig is NOT able to do this
Whats going on here?


The "original" file was created when resolvconf was installed, on OS upgrade.

If the second nameserver address is valid then you should use NetworkManager's Connection Editor to add the second address to IPv4 Settings | Additional DNS servers. Multiple addresses can be separated by spaces, I believe. I am assuming here that you need to enter these addresses manually and they won't be furnished by a DHCP server. Do you have Method set to "Manual" or to "Automatic (DHCP) addresses only"?

Post the nslookup and dig outputs.

---

