---
title: "OpenVPN"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by randyklein99 on 2010-04-03
I'm trying to setup OpenVPN in order to connect back to my home network while traveling for secure browsing and such.

However, before I can even start trying to set that up I tried to see if I could open port check my computer through the net.  And I'm having a hard time doing that.  

As far as I can tell, here are my roadblocks:
1. Is ISP (Qwest) blocking my ports?
2. Is my modem doing the proper port forwarding and firewall?
3. Is my router doing the same?
4. Is my firewall on the computer allowing the request?

To minimize sources of error, I've turned off my local and router firewall and setup my router to forward ports.  I'm not to familiar with my modem, but I'm pretty sure that the firewall is turned off by default and I think I've done port-forwarding correctly.

But still no success when doing an open port check.  At this point I don't know how to diagnose the problem.  Any suggestions?

---

### Post by 2hot6ft2 on 2010-04-03
> **randyklein99 said:**
> I'm trying to setup OpenVPN in order to connect back to my home network while traveling for secure browsing and such.

However, before I can even start trying to set that up I tried to see if I could open port check my computer through the net.  And I'm having a hard time doing that.  

As far as I can tell, here are my roadblocks:
1. Is ISP (Qwest) blocking my ports?
2. Is my modem doing the proper port forwarding and firewall?
3. Is my router doing the same?
4. Is my firewall on the computer allowing the request?

To minimize sources of error, I've turned off my local and router firewall and setup my router to forward ports.  I'm not to familiar with my modem, but I'm pretty sure that the firewall is turned off by default and I think I've done port-forwarding correctly.

But still no success when doing an open port check.  At this point I don't know how to diagnose the problem.  Any suggestions?
Some routers wont let you do a loopback out from your LAN and back in to it from what I've heard.

1. Possible but doubtful depending on the port # you're using. Lower port #'s are more likely to be blocked.
2. Probably.
3. Probably.
4. If you can connect to that port over your LAN then you could find out.

There's a how to in my sig. that may help but I went with SSH and FreeNX for speed and security.

---

### Post by randyklein99 on 2010-04-03
I was doing the open port check from DynDNS.com, so it shouldn't be affected by the loopback.  I know the logs on the router so no attempted connections (not even denied ones) so I think the problem is the modem or ISP.  I've tried higher ports, e.g. 2000, just in case the ISP was blocking lower ports. 

I still don't know if I'm doing the port forwarding at the modem correctly, but I also assume that all ports should be forwarded by default.  The logs on the modem are rather anemic, so I don't glean much from them.

How can I check if the ISP is blocking?

---

