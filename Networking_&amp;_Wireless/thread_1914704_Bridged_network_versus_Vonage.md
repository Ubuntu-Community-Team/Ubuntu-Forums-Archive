---
title: "Bridged network versus Vonage?"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by csete on 2012-01-24
I'm having some Vonage voice quality issues that I'm trying to sort out.  Until recently, my network was set up similar to the following:

Cable Modem <--> Linux eth0 <--> Linux Router/NAT <--> Linux eth1 <--> Private network (including Vonage adapter and other hardware)

I had decent Vonage phone service with this.  Recently, I changed my networking and introduced a bridge to eth1 so that I could place a KVM-based Windows virtual machine on to the private network, yielding something like:

Cable Modem <--> Linux eth0 <--> Linux Router/NAT <--> Linux br0 (including eth1) <--> Private network (including Vonage adapter, Windows KVM and other hardware)

It may be coincidence, but I seem to be having significantly worse call quality since the change and I'm trying to understand if that may be the case or if it is coincidence?  If it could be related, what can I do to improve the situation?  Would STP possibly help?  Anything else?  There should be minimal traffic from the Windows machine at the same time that I'm using the Vonage line, so I don't believe that it would be caused by that.  At some point, I may need to also consider some QoS scripts of some sort to give the Vonage line priority, but up until recently that has not been necessary.  

Any help would be greatly appreciated,
Craig

---

