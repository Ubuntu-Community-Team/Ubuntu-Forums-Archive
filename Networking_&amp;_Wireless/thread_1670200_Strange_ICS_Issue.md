---
title: "Strange ICS Issue"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by LoneTonberry on 2011-01-18
I have been trying to get ICS working to share an internet connection to my Xbox 360 through my wireless on my laptop. I met with some success today by setting up DHCP, Bind9, and a few other things on my Ubuntu 10.4 laptop. Everything is set up, the Xbox connects perfectly fine. Only this is where the strangeness comes in. It will only connect to Xbox Live straight away if tcpdump is running on the system. Otherwise it fails to connect and the testing utility on the Xbox says that the DNS can't resolve the names of the Xbox Live servers or xbox.com. 

I turn the system off, start running tcpdump as root in a terminal, turn it back on and lo and behold it connects to Xbox Live. Turn the system back off, stop tcpdump and turn it back on and I can't connect again. Even just testing the network connection on the console with tcpdump on or off yields the same response.

Are there any ideas as to why this is occurring so I don't have to keep tcpdump running in order to connect to Xbox Live?

---

