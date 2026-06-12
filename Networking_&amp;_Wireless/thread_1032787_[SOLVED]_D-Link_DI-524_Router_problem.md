---
title: "[SOLVED] D-Link DI-524 Router problem"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by HagenG on 2009-01-06
Hello all,

My problem is with the D-Link DI-524 Router. This is a wireless router and I've had some problems getting the wireless to work correctly in intrepid (kernel 2.6.27-9, AMD64 version), so I decided to connect my PC directly to the router (it has an inbuilt switch for ethernet) using an ethernet cable. This worked well, no more connections getting dropped, internet speeds are what they should be, however one issue that I thought was also due to the wireless remains: When opening any web-page (such as google.at) it would take a relatively long time to establish a connection and display content. Firefox would display "looking up google.com" in the status bar for about 15 seconds. This should really be instantaneous. Similiar problems occur with other network applications (Thunderbird, contacting the ubuntu repositories).
Interestingly once the program gets past this establishing the connection the stage things like clicking links (to content on the same site) works at appropriate speeds.

I know the problem is with the router, because bypassing it and plugging my ethernet directly into the modem will fix the above mentioned problem completely. Also the router seems to work fine with my copy of Vista on the same machine. I really don't want to keep the router between my machine and the modem, so I'm thankful for any help on fixing this problem.

---

### Post by HagenG on 2009-01-07
A quick update, I seem to have resolved the issue.

After some reading on the forums, I decided to disable IPv6. This improved things a little but not to the level I was hoping, so I enabled IPv6 again and after some more reading decided to replace the DNS server addresses in my router (which pointed to my Modem previously) with the open DNS ones given in another post, and given here for completions sake:
Primary DNS: 208.67.222.222
Secondary DNS: 208.67.220.220

This solved the problem for me.

---

