---
title: "Slow wireless connection with D-Link dwl-g630"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by rayl on 2006-01-06
I am new to linux but managed to compile and install madwifi for my dwl-g630.  After about two weeks of pulling out hair to get it to receive an ip from my router, I finally got connected.  However, it would only go at 28 Mb/s which is way too slow to get anywhere on the internet.  

I have seen a few threads discussing this but haven't found an end solution posted anywhere.  Any help would bbe appreciated.

---

### Post by firecat53 on 2006-01-07
Hmmm...I also use the DWL-G630 card and it seems to work just fine. Check some of my old posts...I've posted my configurations and how I compiled madwifi and got it running. If that doesn't help, post your some of your configuration here (iwconfig, ifconfig, /etc/network/interfaces, etc.....)

Scott

---

### Post by rayl on 2006-01-09
Firecat-thanks for your help.  I had used your threads earlier to compile madwifi.  It was very useful.  I did figure out my problem.  I had my DNS set wrong.  I had it set for the DSL modem DNS and it should have been the IP for the router.  The next time I turned on my computer after posting this thread, it adjusted automatically to the correct one and I was up and running fine.  My next hurdle is the wireless printer server.  There appear to be other threads for that. 

Thanks again.

---

