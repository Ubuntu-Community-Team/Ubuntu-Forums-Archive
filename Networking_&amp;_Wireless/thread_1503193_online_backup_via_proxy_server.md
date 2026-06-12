---
title: "online backup via proxy server"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by northward on 2010-06-06
Hi,
  	 	 	 	 	 	  Some time ago, while I was still using Ubuntu 8.10 I began accessing Internet through a proxy server. Even though I had set my system proxy settings - including authentication - to pass the proxy, my online backup service (Jungle Disk) stopped connecting. I finally figured out that I had to include proxy port in the Jungle Disk Desktop tool's configuration (like this: 192.168.0.1:8080).
 That worked fine until I recently upgraded to Ubuntu 10.04 - with the identical proxy setup. This time I can't get any connection at all. Here's the Jungle Disk report:
 ===================
 Connection Test Failed 
 Exception Code: xSocketTimeout (53) 
 Time: 06/06/2010 02:29:42 PM (GMT-4) 
 Detailed Message: HTTP connection timed out: connect() timed out! 
 Error Location: JungleHTTP.cpp:906  
 ===================
 I know there's nothing wrong with my proxy setup (or, for that matter, with the Jungle Disk software) because I experimented with a laptop loaded with 9.04 running through the very same proxy and it picked up the system proxy settings (identical to those on my desktop machine) and just allowed Jungle Disk to sail through without even requiring a separate proxy configuration.  
 Three Ubuntu distros and three different experiences handling a proxy.
 Any ideas?
Thanks

---

### Post by northward on 2010-06-17
Update: The guys at Jungle Disk released an upgrade to their desktop software (version 3.08 ) which specifically fixed the problem. Got to give them credit for keeping at it...and for supporting Linux!

---

