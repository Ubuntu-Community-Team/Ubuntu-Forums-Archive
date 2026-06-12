---
title: "SMTP port forwarding reject relay"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by daveytee on 2009-10-27
We have an Ubuntu box set up as a proxy server but have found a use for it as a port forwarder & firewall for SMTP.

We are about to have our email scanned by MessageLabs and needed a way of getting SMTP traffic through from MessageLabs' IP addresses only to our SMTP server (Exchange).

The router we have (Linksys WRV200) can do the port forwarding but cannot let us block all SMTP traffic except that from MessageLabs IPs (which we have). We don't want to have the Exchange server open to all machines on the internet (as you would expect) neither do we trust Windows Firewall on the 2k3 server to handle the firewalling so have set up the Ubuntu box to forward the port 25 traffic it gets (forwarded from the router) to the Exchange Server and are using IPTABLES (actually GuardDog & GuideDog) to only allow ML's IPs (and others for testing).
This seems to be working fine - I can connect in from a remote PC whose IP is allowed and grc.com's Shields Up shows that port 25's not open.

All is working fine but for an extra level of security I would like to set the Exchange/SMTP server to not allow relay from any IP addresses other than local ones (obviously ML's SMTP servers will still be able to deliver email for our domains to our Exchange Server).

The problem I have is that the port forwarding from the Ubuntu box is showing up on the Exchange server as the Ubuntu's internal IP address - whereas I think I'd prefer it to be the external IP that's passed through.

Hope this makes sense - for additional info the Ubuntu box is on the local network and only has one interface (ie it's not in a DMZ or anything).

Thanks

Dave

---

