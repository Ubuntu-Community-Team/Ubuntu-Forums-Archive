---
title: "Windows browsing problems may be due to DNS redirection/&quot;DNS assistance&quot;"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by dhalbert on 2009-03-13
*(This is a solution to a problem, not a query. I haven't found this mentioned elsewhere.)*

I was not able browse Windows shares from the Ubuntu machines in our house, and could not refer to the Windows machines using their own names. I would get errors like "failed to retrieve share list from server", etc. I had to use IP addresses instead.

I thought this problem was something broken in newer versions of Ubuntu, but in this case, Ubuntu turned out to be blameless.

For me, this problem was caused by the **DNS redirection** service provided by our Internet service provider (in my case, Verizon). Verizon and some other ISP's call this **DNS assistance**.

You have such a service if you get a search page with suggestions instead of "server not found" when you try to enter an unregistered domain name in a browser. The ISP's DNS servers serve up an IP address that goes to the search page instead of returning "not found". This DNS redirection was short-circuiting proper lookup of the Windows machine names, because it was returning a DNS result instead of "not found".

An easy way to check for DNS redirection being the cause of Windows browsing problems is to unplug the WAN connection from your router, so you are connected to your own LAN only, and not to the ISP's name servers. Then try browsing your Windows shares. If it works, the problem is due to the ISP.

Verizon, at least, has a workaround for this. Click on the "About This Page" button toward the upper right of one of the DNS redirection search results pages. You will go to a page explaining how to opt out. The basic technique is to reconfigure your router to use a fixed set of DNS servers. For Verizon, the nornal DNS server IP addresses are of the form xxx.xxx.xxx.12. If you change them to xxx.xxx.xxx.14, you'll disable DNS redirection.

You could also choose some other public DNS servers. A web search on "DNS redirection" will get you many suggestions.

---

### Post by jja7001 on 2009-03-22
Thanks for posting this!  I've been banging my head against the proverbial wall for days with this problem.  Your diagnostic steps quickly verified that I had the same problem, and the solution worked like a charm.

I just ran into one minor roadblock, which I'll mention in the hope that it saves someone else a few minutes of headache.  When I went to reconfigure my router (D-link DI-624), the primary and secondary DNS were both listed as 0.0.0.0 on the WAN Settings page (Home tab, WAN button in the DI-624 Config page).  It didn't seem like changing these to 0.0.0.14 would help. A call to VerizonFios tech support and a half hour later, I found that clicking on the Status tab reveals the DNS addresses, which were 71.243.0.12 and 68.237.161.12.  Going back to the WAN settings and entering 71.243.0.14 and 68.237.161.14 in place of 0.0.0.0 for the primary and secondary DNS addresses nailed it.  Now I can browse windows shares from ubuntu, and ubuntu shares from windows.

Thanks again, dhalbert!!!

---

### Post by dhalbert on 2010-04-15
[Bug 389909]("https://bugs.launchpad.net/hundredpapercuts/+bug/389909") is associated with this problem.

---

