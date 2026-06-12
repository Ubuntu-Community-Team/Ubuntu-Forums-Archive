---
title: "Joining Windows AD"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by NeilDW on 2011-07-06
I'm using Ubuntu 11.04, and trying to join a Windows AD using Likewise Open.
 
My server is Win2k3 as DC with DNS installed.
My domain is .LOCAL, my IP addressing is static.
 
When I run domainjoin from the Ubuntu machine I get DNS bad packet error (251e).
All network settingsappear to be ok
I can run NSLOOKUP from Ubuntu and find my DNS server, but if i ping the server there appears to be no reply from the server to the Ubuntu machine.
 
Any suggestions?
 
Thanks

---

### Post by headvampyre@hotmail.co.uk on 2011-07-06
Have you configured ubuntu to use the Win2003 server's DNS? This is vital in an AD environment.

---

