---
title: "Point me in the right direction?"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by ForMar on 2009-06-28
Hello,

For my own "entertainment" I am attempting to setup and configure Ubuntu to be a router/firewall/dhcp...ect,ect. Now I know there are a million how to 's  about this sort of thing but my knowledge about this is minimal at best.
**Question:**I am attempting to restrict access to the Internet via a specific user name and password.
For example: lets say you want to access the internet through my wifi you get on the network fine but when it comes time to google something you are redirected to a webpage asking for your username and password. 

**Request:**Though a step by step would be very appreciated it is no necessary. All I ask is that you point me in the right direction, by telling either exactly were to look or just putting a simple name to this idea so I can find the howtos myself on the internet.

Thank you for your time and help

Anthony

---

### Post by Iowan on 2009-06-28
A proxy server (Squid) is the first thing that comes to mind - though I don't know if it asks for a username/password.

---

### Post by alphacrucis2 on 2009-06-28
I'm pretty sure you can configure squid to require authentication but there are host of different methods that can be used such as back end radius servers but the easiest is probably as described here:

[URL="http://beginlinux.com/server_training/proxy-server/1049-squid-proxy-authentication"]http://beginlinux.com/server_training/proxy-server/1049-squid-proxy-authentication
[/URL]

---

### Post by ForMar on 2009-06-28
> **alphacrucis2 said:**
> I'm pretty sure you can configure squid to require authentication but there are host of different methods that can be used such as back end radius servers but the easiest is probably as described here:

[URL="http://beginlinux.com/server_training/proxy-server/1049-squid-proxy-authentication"]http://beginlinux.com/server_training/proxy-server/1049-squid-proxy-authentication
[/URL]

Thanks alot! really appreciate your time

---

