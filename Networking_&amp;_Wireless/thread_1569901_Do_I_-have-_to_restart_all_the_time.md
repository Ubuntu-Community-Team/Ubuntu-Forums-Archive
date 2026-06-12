---
title: "Do I -have- to restart all the time?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by locoHost on 2010-09-07
I have a POS Belkin Pre-N AP. For the past few months it's been quiting about every 2 or 3 days. Not sure why, but that's for another discussion. To get my wireless to reconnect I have to shutdown the laptop then go reset the AP then restart the laptop. I've tried doing various combinations of disconnect/reconnect in conjuction with ifconfig down/up repeatedly, nothing works, it won't reconnect without the shutdown and restart. Of course this is giant PITA, hence this post ;) How can I get it to reconnect without the shutdown?

Thanks for sharing your expertise! :-)

---

### Post by pricetech on 2010-09-07
What you're describing is not a problem with your computer or Ubuntu.  You have a dying router and need to replace it.

Netgear, Linksys, TrendNet are the 3 brand I recommend.

---

### Post by locoHost on 2010-09-07
> **pricetech said:**
> What you're describing is not a problem with your computer or Ubuntu.  You have a dying router and need to replace it.

Netgear, Linksys, TrendNet are the 3 brand I recommend.

Right... like I said in the OP, the AP is another discussion ;)

About 30 minutes ago the AP quit yet again. This time I disconnected from wifi. Then I restarted the AP, came back to this laptop, did ifconfig eth0 down, pause, then up. Then I tried to reconnect to the wifi and it worked! I don't know if this is the magic sequence and if so, why haven't I tried this unti now? Not sure, but I'm certain the AP will quit again so I'll have a chance to retest this connecting sequence. If this works again later, I'll mark this solved.

I do have a few Netgear switches and my main router is a wired Netgear. I'll probably go Netgear on the new AP.

Thanks :)

---

### Post by wilee-nilee on 2010-09-07
Do you you have the wireless set to auto connect for all users, via the right click edit in the applet.

---

