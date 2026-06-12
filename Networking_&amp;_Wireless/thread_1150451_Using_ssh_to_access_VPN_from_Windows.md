---
title: "Using ssh to access VPN from Windows"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2009-05-06
At home I have to use Windows as I need VPN access to the office.  We use a CheckPoint firewall and that doesn't seem to play nice with OpenSwan etc due to how it's configured.  Nothing I can change there.

Recently I got ssh working Ubuntu <---> Windows and was wondering if I could make use of that.  Can I somehow ssh from my Ubuntu laptop at home to my main Windows PC, and then have that redirect the traffic over the VPN?

This would allow me to connect my Ubuntu laptop to my Ubuntu desktop in work (either using VNC or XDMCP).

So what I would have is:

Ubuntu Laptop ---> Windows PC --VPN--> [Work]

Thanks for any advice.

---

### Post by Another Monkey on 2009-05-07
Bump

Is it even possible to do this?  As I have to use CheckPoint (and thus have to use Windows) it is a major stumbling block in my converting.

If I can get this going, I could do the same thing with Windows running inside VirtualBox with Ubuntu as the host.  Which would be nice.

I've tried Googling (and I'll keep trying) but it's like looking for a needle in a haystack.

Thanks.

---

