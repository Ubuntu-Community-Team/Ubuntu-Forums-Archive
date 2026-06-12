---
title: "Advice on throttling bandwith by IP on home network"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by h2sammo on 2013-04-17
I have a ubuntu box (of course :) ) directly connected to a dir -655 Dlink router. My roommates hog my bandwidth. How do i control how much bandwidth each IP gets in this situation?

Thank you

---

### Post by SeijiSensei on 2013-04-17
If your roomates are peered with you in the same subnet, then you would have to apply rules at the router.  If your roomates are "behind" you, with all their traffic coming in on one interface of your machine and being forwarded to your D-Link router on the other, you could write rules for them.  I doubt that is how your network is set up. 

I looked at the manual for your router and did not see anything that allows you to set bandwidth limits.

Managed switches with "rate-limiting" can do this, but they're [pricey]("http://community.spiceworks.com/topic/269390-bandwidth-control-on-low-mid-range-switches").  If you had a [router that supported dd-wrt]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010076&IsNodeId=1&bop=And&ActiveSearchResult=True&SrchInDesc=open%20source&Page=1&PageSize=20") (yours [doesn't]("http://www.dd-wrt.com/wiki/index.php/Known_incompatible_devices")), you could use "[quality of service]("http://www.dd-wrt.com/phpBB2/viewtopic.php?p=658249")" rules based on the MAC addresses of the client machines.  You could put your machine(s) into the top category and your roommates' machines in a lower one.

---

### Post by CharlesA on 2013-04-17
I think the default Dlink firmware also offers quality of service, but I'm not 100% sure as both the dlink routers I have (615s) are running dd-wrt.

---

### Post by SeijiSensei on 2013-04-17
I looked at [his router's manual](http://static.highspeedbackbone.net/pdf/D-link-DIR-655-Manual.pdf) again.  There is a "QOS Engine" described there on page 36, but it does not look to me like it enables you to limit bandwidth by client address.

---

### Post by h2sammo on 2013-04-17
so there is no way to control other IP addresses unless i do it through the router. do you have any suggestions on the type of router i could buy that can do this properly? QOS will only allow me to set priorities btw, i played with that but its not satisfactory to me.

thank you

---

### Post by CharlesA on 2013-04-17
Depends on your needs and environment. I use a DIR-615 with DD-WRT but it only has 10/100 ports, not gigabit ports, so I have a gigabit switch attached to it so I get gigabit speeds internally.

---

### Post by h2sammo on 2013-04-17
my needs r to control everyone who lives in my house :). I would prefer one single item to buy (router) that can do all this.

---

