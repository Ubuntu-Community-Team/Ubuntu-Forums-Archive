---
title: "Configuration for &quot;virtual&quot; network interface"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by tagini on 2011-07-19
Hi all

I'm having difficulty setting up my desired network infrastructure. Here's the situation:

I'm currently using an Ubuntu box as homeserver to do everything from sharing internet (via NAT), over DHCP & DNS to filesharing and even virtualisation.

However, since my machine is capable of virtualising [Astaro Security Gateway]("http://astaro.com") properly, I would like to transfer and split up responsibilities.

I want to have my Astaro fully responsible for the internet and act as the gateway, and along with that disconnect my physical box from the internet and put it behind Astaro (basically making it just a member of the internal network).

The difficulty I'm having with this is that Astaro is running virtually on the physical box, and I can't seem to figure out how to configure the external interface. It needs to be up for Astaro to be able to use it, but it should not give the physical machine access to the external network.

I'm thinking I could set it to manual and not give it an ip address, but I'm not sure on this.

Can someone set me in the right direction?

Thanks
Tagini

---

### Post by jmoorse on 2011-07-19
Your plan with setting no IP on the physical NIC is what first came to mind for me too.  Then you can bridge in the Astaro WAN/Untrusted NIC

What virtualization software are you using?

---

### Post by tagini on 2011-07-20
Bridge as in set the NIC to bridged mode rather than NAT in the virtualistion software?

If so, I tried that and it did not work. Didn't have much time to look at it though so it could've been a configuration issue (NAT between interfaces or something)

I'm using VirtualBox as virtualisation software.

---

### Post by jmoorse on 2011-07-20
> **tagini said:**
> Bridge as in set the NIC to bridged mode rather than NAT in the virtualistion software?

If so, I tried that and it did not work. Didn't have much time to look at it though so it could've been a configuration issue (NAT between interfaces or something)

I'm using VirtualBox as virtualisation software.

Yes, bridged.  Otherwise you will need to perform an additional routing step / NAT translation inbound + outbound to Astaro.  Also, traffic originating from the server will use its directly connected gateway to the internet and bypass Astaro.

Does that make sense?  Kind of a hard concept to visualize.

---

