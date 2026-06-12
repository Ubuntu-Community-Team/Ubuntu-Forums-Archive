---
title: "Howto? - Transparent proxy with Dansguardian"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by rbue on 2010-06-22
I've installed Ubuntu Desktop 10.04, and tried (I think) all the descriptions on the net about how to seup af Transparent proxy server with dansguardian. Somehow I can't get the transparency to work! I think I tried alle the suggestions with NAT Masquerade etc but I'm not that much into iptables. Can anyone give me a detailed description on howto setup Ubuntu 10.04 as a Transparent proxy with Dansguardian filtering ? The installation I have now is with squid 2.7 Stable 7 and Dansguardian 2.10.1.1.
 
Just to point it out: the setup works perfectly when I set the proxy in the clients browser - but I cannot get it to work as a transparent server. I think I have googled any answer there is to this question right now - but haven't found any answers that concern Ubuntu 10.04 - and squid 2.7
 
 
Thank you!

---

### Post by dbloom on 2010-06-22
i think you'll have to get your hands dirty with iptables.  i set up squid with a transparent proxy before (haven't used for a while though).  i found this link with a quick google search. 

[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html]("http://www.faqs.org/docs/Linux-mini/TransparentProxy.html")

i'm sure there are others.  good luck.

---

### Post by rbue on 2010-06-22
Thank you - but the problem with that HOWTO (from 2002) is that it is for an older version of squid and iptables - a lot has changed since then! I need a version that is up to date - beacuse I cannot figure out what is wrong. As mentioned in my first post - I have tried a LOT of howto's - but still cannot get it to work.

---

