---
title: "ION, Mythbuntu, TV over IP"
date: 2009-10-12
forum: Mythbuntu
---

### Post by Dan1317 on 2009-10-12
Hello, a friend just got an ION (Nvidia 9400m graphics with atom processor) ([Newegg link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027"))  Is there a way to use Mythbuntu with this?  The inputs for the cable box are HDMI and component only.  (TV with phone company over internet)

His tv has 4 HDMI but no dsub connector.

I can't really find any tuners that would replace the cable box (Remember the box has an ethernet cable coming into it, and to the tv has either HDMI or component)  

On Newegg, I found [these]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380047%201148410221&bop=And&ShowDeactivatedMark=False&ActiveSearchResult=True&Order=PRICE") but these appear to be opposite of what I need

If anyone could help, I would greatly appreciate it

---

### Post by joshoekstra on 2009-10-12
Tell us a bit more about the service used, like hardware, company and such. The ION can do a lot, just not magic ;)
If the IPTV is scrambled, chances are that using something like a HD-PVR from hauppauge is the way to go. If it's clear IPTV you can capture it using mythtv directly(as far as I know)

---

### Post by Dan1317 on 2009-10-12
Thank you joshoesktra for your quick reply.  The company is Consolidated Communications, [here is their TV page]("http://consolidated.com/residential-digitaltv.php").  For the set top box, I couldn't find an HTML page, only a PDF.  ([Link]("http://www.consolidated.com/files/pdf/35145_SetTopBoxUsersGuide.pdf")) 

 If I were to just use something like the HD-PVR could I still use Mythbuntu to record and watch tv? The only hardware right now are the tv, computer, and set top box.


Also, one last question, if the IPTV isn't scrambled, then I can just plug the cable directly into the ION ethernet port?  

Thank you again and please let me know if you need more information

---

### Post by nickrout on 2009-10-12
> **Dan1317 said:**
> Thank you joshoesktra for your quick reply.  The company is Consolidated Communications, [here is their TV page]("http://consolidated.com/residential-digitaltv.php").  For the set top box, I couldn't find an HTML page, only a PDF.  ([Link]("http://www.consolidated.com/files/pdf/35145_SetTopBoxUsersGuide.pdf")) 

 If I were to just use something like the HD-PVR could I still use Mythbuntu to record and watch tv? The only hardware right now are the tv, computer, and set top box.

yes of course you can use hdpvr with mythtv [http://www.mythtv.org/wiki/HDPVR](http://www.mythtv.org/wiki/HDPVR)

> 
Also, one last question, if the IPTV isn't scrambled, then I can just plug the cable directly into the ION ethernet port?  



I believe you can, but you will need to set it up correctly. I would ask on the main mailing list as others have probably crossed this bridge.

PS can't connect to the consolidated.com site at present.

---

### Post by joshoekstra on 2009-10-13
Like Nick said, there is the possibility to use the IPTV-stream if it isn't scrambled. I guess you could even use the std ethernet-port for that..
In my company, we use scrambled IPTV and use a different VLAN for the TV-signal to our motorola VIP1960. If your setup is the same, it's probably easier to use the HD-PVR.

---

### Post by bsntech on 2009-10-13
Consolidated IPTV eh?  Nice - so that means you must be in the Central Illinois area then - or one of their other companies they bought.

My parents tried to get their IPTV after they found out it was only going to add on about $10 a month to their current bill - but they are not within range - although they get their DSL service just fine.

---

