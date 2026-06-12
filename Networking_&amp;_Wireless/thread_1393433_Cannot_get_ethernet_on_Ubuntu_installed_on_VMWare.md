---
title: "Cannot get ethernet on Ubuntu installed on VMWare"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by hughOnLinux on 2010-01-29
Hi all, 
  My root problem is that I have no connectivity after doing a fresh install of Ubuntu 9.10 on a VMWare share running on VMWare Server 2.0. The fact that I'm running on VMWare may be the problem, but unlikely since a similar install of OpenSuse 11 worked without a hitch.
  I've gone to the network connections to try and edit the settings on my connection. I've set it up for DHCP authentication.  Actually first question there is what is DHCP Client ID? Should I have a value there?  
  The next thing I tried after looking at a couple of threads is running [ifconfig] from the command line.  I am unable to cut and paste from my VMWare share to my desktop (probably because I can't get VMWare tools to run either), and with no network connection, I cannot post my findings somewhere where I can copy them here.  The one notable thing was that the loopback adaptor had an inet and an inet6 line, whereas the ethernet only had an inet6 entry.  I suspect that this is the root of my problem, but have no idea how to fix it.
  Any suggestions?
-Hugh

---

