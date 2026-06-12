---
title: "LAN-only PPTP VPN with network-manager"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by wareagle on 2009-09-21
I've looked all over the forums to see if this can be done.  Can I set up a LAN only PPTP VPN with network-manager.

I want internet packets to be routed through the normal router.

---

### Post by spd106 on 2009-09-21
Try the following page in the help wiki.

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

It's quite a simple process, you should just need to install the PPTP plugin via Synaptic, then while configuring the connection on the IPV4 tab click on Routes button and check the "Use this connection only for resources on its network" tickbox.

Hope that helps.

---

### Post by wareagle on 2009-09-21
Ah, ok.  When I do that, it just connects the VPN but doesn't add any routes.  I can enter them in manually, but the problem is that my gateway is always the same IP address as the one I get from the VPN server, which is different every time I connect.  Can I create a route that always uses whatever IP address the VPN server gives me as the gateway automatically?

---

### Post by racer on 2009-11-07
> **wareagle said:**
> Ah, ok.  When I do that, it just connects the VPN but doesn't add any routes.  I can enter them in manually, but ...

i'm having the same problem.  does anyone have a solution for this?

VPN connects fine, I can ping the VPN server on the other side, but nothing else on the network.  Looking at routing, I notice that there's only a route for the VPN server and not for the entire network -

10.172.11.10  *  255.255.255.255 UH  0  0  0 ppp0

That's all that's routed thru ppp0.

I've also tried adding the route to the VPN setup but that doesn't make any difference.

The only thing that does work is to manually add the route at terminal prompt, but that's not an option I believe one should be resorting to everytime VPN is needed...

tks

-r

---

