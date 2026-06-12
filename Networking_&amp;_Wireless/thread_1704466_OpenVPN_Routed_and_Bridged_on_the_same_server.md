---
title: "OpenVPN Routed and Bridged on the same server?"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by Chrus on 2011-03-10
I currently have one of our clients set up to use a routed VPN for their 5 laptops to connect to the server remotley. And this works brilliantly. They are about to bring on a remote office that will need a VPN connection back to the main office, so I was going to set up a bridged connection between the two sites (and possibly more sites in the future).

So my question is whats the best way to go about this? Can I have one instance of OpenVPN running with tun0 set up for a routed connection to the laptops and add a second tun (tun1) to the config that will be for the bridged connection between the sites? Or am I going to have to run multiple instances of OpenVNP, one for the routed and another for the bridged?

If routed and bridged have to run in seperate instances, will I have to add another instance for each new remote site that needs a connection? Can a bridged config connect to multiple sites, or have multiple tuns in the one config?

For reference, I was looking at this guide for setting up the Bridged connection ([http://ubuntuforums.org/showthread.php?t=752127](http://ubuntuforums.org/showthread.php?t=752127))

I will supply any additional info if needed.

Thanks

---

### Post by Kreindhild on 2011-03-10
depending how you are set up at both sites, there are routers that can be purchased to automatically VPN in... so you could set the router up as a vpn client to the main site, then anyone connecting from the remote site would already be on vpn, instead of each computer creating its own connection through the 1 tunnel....

Not sure if it helps, but worth looking into.

---

### Post by Chrus on 2011-03-10
Sorry... I should of specified. The laptops connect from anywhere/everywhere. Home offices, other peoples offices, McDonalds hotspots, etc. So leaving them on the routed VPN still looks like the logical way to go.

And it would make sense for the two sites to be bridged so there is no NAT involved etc.

Their main office is currently running an Ubuntu virtual machine set up as a router/gateway. IPtables, edge server, OpenVPN. The new site is going to have something similar with a VM running ubuntu and OpenVPN.

---

### Post by Foeburner on 2011-03-31
Hey im currently looking into doing the same. 


These are the howto's im following. 
[click here]("http://www.smallnetbuilder.com/security/security-howto/30353-how-to-set-up-a-site-to-site-vpn-with-openvpn?start=2")

and [here]("http://openvpn.net/index.php/open-source/documentation/howto.html#vpntype")

i havent got it working yet but i'm hoping to find another that is going through the same as me and work together. 

Keep posting how far you get. I would really like to see this finished.

---

