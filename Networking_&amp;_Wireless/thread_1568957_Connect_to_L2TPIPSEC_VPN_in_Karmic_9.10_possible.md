---
title: "Connect to L2TP/IPSEC VPN in Karmic 9.10 possible?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by mattkerle on 2010-09-06
I need to connect to a clients VPN to access some of their internal systems. To connect I was given a username/password and a hideous document describing how to import certificates and generate a private shared key (PSK) and add it to windows XP, then add a layer 2 tunnelling protocol / IPSEC connection. Hideous.

I can make it happen with a vmware XP instance (hopefully), but I'd prefer to do it natively under Linux rather than on windoze, only problem is I don't think it's possible?

first of all I'll say I'm a n00b when it comes to VPNs, I haven't really had to use them up to this point, and where I have it was as simple as install the cisco VPN client, add in some group name/pass and username/pass and it just worked (windows XP this is)

Next, what is up with network manager coming without any vpn clients options installed by default at all? I understand if there were encumbrances but it'd be really nice if there was a bit of UI that led you to installing them, seeing as how the "add VPN" option is there just big as a horse. anyway /rant.

So, first stop was the community doco on VPN Client:
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

PPTP check, openVPN check, Cisco VPN check, L2TP/IPSEC... not so much.

Googling found a few interesting hints:
[http://serverfault.com/questions/10671/l2tp-client-for-ubuntu-jaunty](http://serverfault.com/questions/10671/l2tp-client-for-ubuntu-jaunty)
[http://www.jacco2.dds.nl/networking/linux-l2tp.html](http://www.jacco2.dds.nl/networking/linux-l2tp.html)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691)

so it looks like you *can* set one up with openswan, but there's a fair bit of old-school h4xx0ring, there's no pretty GUI in network-manager as with the other options, and it really looked to me like I'd have to compile from source. All these are really old though and may have been superseded...

So my question is, if I wanted to make this work, what's the easiest option? I'd prefer not to have to compile from source and hack conf files to make this work...

EDIT UPDATE: looks like there's some options in synaptic that aren't on the doco page yet.. packages network-manager-strongswan and network-manager-openconnect look promising, anyone know which of these would be better for connecting to L2TP?

thanks!

---

