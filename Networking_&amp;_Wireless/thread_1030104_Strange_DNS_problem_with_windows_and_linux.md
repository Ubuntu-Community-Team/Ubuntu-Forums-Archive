---
title: "Strange DNS problem with windows and linux"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by coggins on 2009-01-04
I am having a strange problem with DNS.  I have two machines running WinXP Home and two running Ubuntu 8.10. They are all connected to a GIGABYTE GN-BR01G wired/wireless router.  Usually everything works fine - SMB file sharing / internet on all machines.  Then, at seemingly random intervals, the two XP machines and one linux machine all lose the ability to resolve internet addresses. (In case that was unclear, I mean that the 3 machines fail at the same time).  The other linux machine remains fine.  Rebooting the router fixes the problem temporarily.  
I don't think it is a DHCP thing - one of the Windows machines has a static IP (the other XP and the failing linux use dynamic), and all are using specific dns servers.  I changed the dns servers on one XP machine to OpenDNS and left the other one with my ISP's dns, so it is not a server problem.  When the problem occurs I can still ping the DNS servers from all machines.
I ran wireshark on one of the XP machines and the linux machine that is working.  This is where it gets really odd.  When the problem occurs, a dns query will go out from the XP machine to OpenDNS (or whatever) but then come back to the linux machine that is working.  Of course the linux machine doesn't know what to do with an unsolicited dns answer so replies with 'destination unreachable'.
My gut feeling is that when the router's cache fills it starts sending dns traffic to the linux box, but I can't imagine why that would be the case.  
Any ideas for further troubleshooting?

---

### Post by jonandrews on 2009-01-04
I had a very similar problem when I put a  Thomson router on my network, which I was never able to resolve. In exasperation, I switched to a Linksys router and the problems dissapeared permanently. I wish I knew why....

---

### Post by wmoore on 2009-01-04
Certainly sounds like a router issue. What router do you use?

In the first instance I would factory default / upgrade firmware on the device and Google for the issue.

---

### Post by coggins on 2009-01-04
> **wmoore said:**
> Certainly sounds like a router issue. What router do you use?

In the first instance I would factory default / upgrade firmware on the device and Google for the issue.

It is a GIGABYTE GN-BR01G.  It is already on the latest firmware.  I suppose a factory reset might not be a bad idea.  I'll give that a go now.

---

