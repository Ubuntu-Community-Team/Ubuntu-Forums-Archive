---
title: "cisco CCNA / CCNP"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2010-11-23
Well i do not know if this is the right place to post this.

I have studied CCNA and are done with that and are now studying CCNP. And to keep my knowledge up to date, i would like to offer my knowledge to anyone who wants it.

If you have questions with
*Network topology
*Routing protocols / behaviour
*Network security
*Cisco router / switch configuration

Anything you can think of in the CCNA / CCNP range.

Kind Regards

---

### Post by pricetech on 2010-11-23
"To teach is to learn again" ???

---

### Post by Drenriza on 2010-11-24
> **pricetech said:**
> "To teach is to learn again" ???
 
For me it is like. If i can "teach" others what i know, i myself will get a better understanding of the subject. Hope that answers your question, if it was a question :p

---

### Post by pricetech on 2010-11-24
It's an old adage.  I was asking if that was your purpose, which you indicate it is.

You'll probably get some response since cisco is so poorly supported by cisco.

---

### Post by endotherm on 2010-11-24
can you point me to an firmware/ios upgrade for my 851 router, and some instructions for applying it?

---

### Post by Drenriza on 2010-11-25
> **endotherm said:**
> can you point me to an firmware/ios upgrade for my 851 router, and some instructions for applying it?

Is it called something more than 851 :p
[name]851 or something.

---

### Post by endotherm on 2010-11-25
> **Drenriza said:**
> Is it called something more than 851 :p
[name]851 or something.

they seem to call them "Cisco 800 Series Routers", specifically the 851. here are the 850 series datasheets:
[http://www.cisco.com/en/US/prod/collateral/routers/ps380/ps6195/product_data_sheet0900aecd8028a9a9.html](http://www.cisco.com/en/US/prod/collateral/routers/ps380/ps6195/product_data_sheet0900aecd8028a9a9.html)

I also have a few questions about "application inspection" if you have any familiarity with it. it appears to be an extension to the firewall, but it doesn;t seem to block or allow stuff specifically. for instance if I remove https inspection from an interface, https stops working for the lan, but there are lots of protocols that are absent from the inspection list that work fine. weird.

and thanks for the offer. I really should study up on this myself, but my cisco experience is from long long ago, so any assistance would be appreciated.

---

### Post by karthick87 on 2010-11-25
Can you explain me abt Subet calculation?

---

### Post by Drenriza on 2010-11-25
> **endotherm said:**
> it appears to be an extension to the firewall, but it doesn;t seem to _** block or allow stuff**_ specifically. for instance if I remove https  inspection from an interface, https stops working for the lan, but there  are lots of protocols that are absent from the inspection list that  work fine. weird.

Uhm i do not know about that extension to the firewall, i only block stuff using ACL (access control lists). Do you manage the router with the command line or an HTTP interface? Since setting up a router, through the command line is in my opinion, much simpler.

I dont know where to download the ios, but luckily i know alot of cisco nerds that does. So i ask them and get back to you on that ,)=

Note to myself, for later use. 851 IOS.
[http://www.cisco.com/cisco/software/release.html?mdfid=279623991&softwareid=280805680](http://www.cisco.com/cisco/software/release.html?mdfid=279623991&softwareid=280805680)

---

### Post by endotherm on 2010-11-26
howdy, 
no worries man, no one seems to know what it's really about it. LMK if you find out anything. 

as for router admin, I do tend to use the SDM (the full client install) for administration, though I ssh in for simple stuff. don't get me wrong, I;m not afraid of the cli, so don;t feel like you need to crop pictures for me, but with the size of my config, I really don;t want to have to type it in line by line. I'm sure I'd forget something critical, and the UI helps me remember all the things I need to do.

edit:
that sucks, appearently I need a service agreement with them to download an ios image. lame.

---

