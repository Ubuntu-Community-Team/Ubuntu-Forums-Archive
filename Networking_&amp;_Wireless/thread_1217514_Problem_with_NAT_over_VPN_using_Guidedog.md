---
title: "Problem with NAT over VPN using Guidedog"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by lordofthebrambles on 2009-07-19
I am having a problem getting NAT to work over a PPTP VPN connection using Guidedog.  I have a Windows XP virtual machine setup in VirtualBox, using host-only networking, and I am using Guarddog to provide it with NAT, as a workaround to problems with VirtualBox's own internal NAT and bridged networking functionality.

Everything works fine if I am not connected to the Internet through my VPN.  I can browse websites on my Windows virtual machine and so forth.  However, once I establish a VPN connection, suddenly, the Windows virtual machine loses all Internet connectivity.  It can still connect to the host machine and DNS queries work, because I am using dnsmasq.  However, TCP connections to the Internet time out.

I also have a firewall setup with Guarddog, but I disabled the firewall while testing this, and I still had connectivity problems.  I can connect to the Internet on the Windows virtual machine with the firewall disabled and VPN disconnected, but not once I establish the VPN connection.  This does not seem to be an issue related to the firewall rules.

Does anyone have any idea what is going on here?  Is there some additional piece of configuraiton I have forgotten about  here?

---

### Post by replier on 2011-01-21
I had a similar problem. Enabling ICMP redirect in the Internet Zone in Guarddog solved it.

---

