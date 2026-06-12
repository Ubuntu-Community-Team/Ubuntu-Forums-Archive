---
title: "How do I connect to my Windows Server 2012 workstation remotely?"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by bertles86 on 2013-05-14
I can access my workstation in my office remotely by going to remoteacess.XXXX.com in a browser, logging in and clicking 'Connect' next to my laptop which runs an .rdp file and shows me my desktop.

How do I do this in Lubuntu?

---

### Post by TheFu on 2013-05-14
Using RDP over the internet is not secure.  To address some of the security issues (not all), Microsoft improved the overall security by adding NLA - Network Level Authentication - starting with MS-Vista and later.  These updates are incompatible with most Linux versions of RDP.

There is good news - FreeRDP and Remmina are reported to support NLA. 

As a fallback, you might force the Windows Server 2012 into legacy authentication mode. Changing the RDP session into legacy mode can have other security implications even on the LAN. Read up and understand those trade-offs.

Generally, remote desktops need a VPN to be secure. Again, the Microsoft version of VPN - PPTP - has been cracked multiple times and is not considered secure enough for business use by anyone.  Use of openvpn or IPSec is needed.  After a VPN using either of those tools is setup, then either the new or legacy RDP session authentications can be used from any Linux client without concern.

I wrote most of this from memory, so some of the Microsoft terms are probably inaccurate, but I stand behind the general ideas.

For Linux remote desktops, NX is a fantastic, efficient, solution.  FreeNX is the server and Remmina or NoMachine! nxclient work well.
Good luck!

---

