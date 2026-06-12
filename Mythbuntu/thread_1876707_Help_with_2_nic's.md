---
title: "Help with 2 nic's"
date: 2011-11-06
forum: Mythbuntu
---

### Post by henge on 2011-11-06
I have problems then using 2 nic's.
eth0 lan 192.168.1.249 - normal lan
eth1 lan 10.44.51.205 - IPTV

then first interface I connect is used
how can I make both working
Then only thing I need eth1 for is IPTV and using theese subs

233.139.5.xxx
239.255.0.xxx
I can watch IPTV on the server but only if I disconnect eth0

I tried to make route on eth1 for theese subs
but it didn't work ( properly wrong setup ;-) )

Please help me

---

### Post by its_johan on 2011-11-13
Any help on this ? I have the same problem

---

### Post by nhtrader on 2011-11-14
> **henge said:**
> I have problems then using 2 nic's.
eth0 lan 192.168.1.249 - normal lan
eth1 lan 10.44.51.205 - IPTV


1. Would you mind explaining in more detail what IPTV is (manufacturer, model, and what service you are using: terrestrial/satellite and/or unmanaged IP/internet )?
2. Please explain why do you have 2 subnets (192.168. and 10.44.)?
3. Have you created another Capture Card for IPTV in MythTV BackEnd Setup?
4. Have you created a Video Source for IPTV in MythTV BackEnd Setup?
5. Have you created an Input Connection for IPTV in MythTV BackEnd Setup?

---

### Post by nickrout on 2011-11-14
> **nhtrader said:**
> 1. Would you mind explaining in more detail what IPTV is (manufacturer, model, and what service you are using: terrestrial/satellite and/or unmanaged IP/internet )?[http://en.wikipedia.org/wiki/Iptv](http://en.wikipedia.org/wiki/Iptv)> 
2. Please explain why do you have 2 subnets (192.168. and 10.44.)?because it is usually best practice to separate your IPTV traffic from your LAN traffic.> 
3. Have you created another Capture Card for IPTV in MythTV BackEnd Setup?
4. Have you created a Video Source for IPTV in MythTV BackEnd Setup?
5. Have you created an Input Connection for IPTV in MythTV BackEnd Setup?

I suspect it is a routing problem. What does ```
route -n
``` tell you?

---

