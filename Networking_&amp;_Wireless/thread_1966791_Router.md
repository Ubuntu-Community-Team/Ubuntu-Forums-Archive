---
title: "Router?"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by dgingeri on 2012-04-27
I've been working on setting up a Linux NAT router/firewall VM with CentOS under ESXi 5, and it is just a big pain.  Hundreds of directions that only partially work.  (I pieced together several and got it mostly working, but I'm nervous on the security settings because I don't fully understand it.)  It only works part of the time, suddenly losing connection for no apparent reason.  When I look at the console for the network config, eth0 just loses it's IP address.  My latency is 10ms more than using Windows 2008 R2 for a router.  I'm just sick of the whole thing.

Does anyone know if Ubuntu server has an easier to configure and understand NAT router function?  If it's just iptables, then I'll just switch back to a Windows router VM.  However, if it's something else, I'd love to hear about it.

(note: all I need is the router functions.  I have a working DHCP/DDNS Linux machine separate from the router.  I specifically separated the router function to an exclusive VM for security and maintenance reasons.  I also have totally separate print and file servers for the same reason.  Anyone hacking into my network will have a hard time getting to anything, and if anything goes down, besides the ESXi host itself, it doesn't bring everything down.)

---

### Post by ratcheer on 2012-04-27
Why not try a Linux distro that is specifically designed to be a router, such as Untangle or m0n0wall? There are several others.

Tim

---

### Post by dgingeri on 2012-04-27
Never heard of those before.  I'll check them out.

---

