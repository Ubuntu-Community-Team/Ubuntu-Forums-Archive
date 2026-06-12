---
title: "how do I monitor network traffic?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Miles_Prower on 2009-04-14
Is there a tool that will let me assess the traffic that crosses my network? 

I want something that would be able to do things like...

~ Automate bandwidth tests and keep information average speeds, highs/lows, monthly data consumption (Time-Warner is about to start capping bandwidth, and there's no competition in my area)

~ Measure the impact of certain types of traffic on overall speed (does alice's web access slow more when bob starts an ftp transfer, samba transfer, or bittorrent transfer?)

Does this kind of thing exist, or do I have to write it? Please tell me it exists....

---

### Post by Mordac85 on 2009-04-14
You could use [rddtool]("http://oss.oetiker.ch/rrdtool/"), but your home network config, if you have more than one box, is important.  If you're working on a switch or a hub, does it support SNMP, etc.  Remember, you have to be able to 'see' the traffic in some manner to monitor it.

---

### Post by Miles_Prower on 2009-04-18
no, it seems like my belkin F5D7231-4 does not support snmp. I could buy a new router if I need to. Is there anything else I should look for besides snmp?

---

### Post by MarkM06 on 2009-04-18
Have you tried Wireshark? I'm not sure if it meets all of your criteria, but it's certainly worth looking into.

Mark

---

