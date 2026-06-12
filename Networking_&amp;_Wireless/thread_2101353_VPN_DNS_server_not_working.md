---
title: "VPN DNS server not working"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by TomtheWombat on 2013-01-04
I am having a problem with the new resolvconf stuff.  I am able to configure my primary DNS server correctly through network manager.  However, when I connect to my VPN it has its only DNS server.  I manually added the DNS server to "Additional DNS Servers" in the IPV4 settings.  I also tried it with the addresses only method and specifying the "DNS Servers", but neither worked.

I have to manually add the new DNS servers to the resolvconf every time.  Is this a known bug?  Is there an easier solution?

---

### Post by jdthood on 2013-01-04
> **TomtheWombat said:**
> I am having a problem with the new resolvconf stuff.  I am able to configure my primary DNS server correctly through network manager.  However, when I connect to my VPN it has its only DNS server.  I manually added the DNS server to "Additional DNS Servers" in the IPV4 settings.  I also tried it with the addresses only method and specifying the "DNS Servers", but neither worked.

I have to manually add the new DNS servers to the resolvconf every time.  Is this a known bug?  Is there an easier solution?

Background reading: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Possibly you are missing the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf. To fix this, run "sudo dpkg-reconfigure resolvconf".

Are you connecting to the VPN using NetworkManager?  What kind of VPN is it?

---

### Post by TomtheWombat on 2013-01-04
> **jdthood said:**
> Background reading: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Possibly you are missing the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf. To fix this, run "sudo dpkg-reconfigure resolvconf".

Are you connecting to the VPN using NetworkManager?  What kind of VPN is it?

I had that problem before, but it is fixed now.

Thanks for the informative link. I'm pretty sure that the domain and subnet are not reported by the VPN. I will read that and report back here with what I find out. I should be able to figure it out!

---

