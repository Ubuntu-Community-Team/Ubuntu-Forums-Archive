---
title: "Wireless Router Question not specific to Ubuntu"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Apv507 on 2010-05-08
So.. my laptop recently died and I got a desktop to replace it. Of course it doesn't have a wirless adapter built in. I have two belkin wirless routers, Is there anyway to use my second router as a reciever and have my computer on the network through a lan cable? This sounds kind of iffy, but seems to make sense that it would be possible, Any help?

---

### Post by bananas4370 on 2010-05-08
Check the documentation for your routers and see if they support bridge mode.Also known as point to point.

---

### Post by Apv507 on 2010-05-08
They do in fact have wireless bridge! I have a feeling this is going to be easier than I thought. Thanks!

---

### Post by bananas4370 on 2010-05-08
> **Apv507 said:**
> They do in fact have wireless bridge! I have a feeling this is going to be easier than I thought. Thanks!

You basically need to tell each router the other routers MAC address. The MAC address should be marked on the router. If not, you can always find it with arp.

---

### Post by Apv507 on 2010-05-09
Wow, you answered my question before I could ask it! Thanks for the speedy help, I really appreciated it!

---

### Post by Apv507 on 2010-05-09
Well that being said I have another question: Do I need to set one as an access point or both, or neither. They are both belkin routers and both have a settings tab for wireless bridging and another for Access Point (well kind of a tab, more like an option on the left). Everything so far has been under the Wireless Bridging 'tab', the mac address and all that, but it refers to an AP (Access Point, but im sure you know that), however niether is set as an access point.

---

### Post by bananas4370 on 2010-05-09
> **Apv507 said:**
> Well that being said I have another question: Do I need to set one as an access point or both, or neither. They are both belkin routers and both have a settings tab for wireless bridging and another for Access Point (well kind of a tab, more like an option on the left). Everything so far has been under the Wireless Bridging 'tab', the mac address and all that, but it refers to an AP (Access Point, but im sure you know that), however niether is set as an access point.

The TP-Link routers I have here let me set them as AP's. I think the last time I played with point to point on these, I had those boxes ticked. It shouldn't really matter because the routers will only talk to each other because of the MAC address field. To be honest, I can't really find any documentation to explain the AP part.

Cheers
Patrick

---

### Post by bananas4370 on 2010-05-09
My mistake here and confirmed by reading the manual :P. On the TP-Link routers, and would be the same with your Belkins, if you tick the box that says AP mode, then the router/s will also act as an AP. Thinking back, I never had that ticked, as I only wanted at the time a point to point link. I didn't want any other sort of access.

To summarize -

Put both routers in point to point bridge mode.
In the MAC address field, put the MAC address of the other router.
Make sure both routers are on the same channel and are using the same security settings. 

I hope this helps.

Cheers
Patrick

---

### Post by Apv507 on 2010-05-10
Thanks for all your help, I finally got it working last night, sadly it only works 50% of the time with Ubuntu, but 100% with Windows 7. Even if is working on 7 and I restart the machine and pick Ubuntu it doesn't work, which is more than a little strange to me. Any this set up is only for a few months and then I'm back off to college, So I can settle Windows for a summer. Thanks again for all your help. I would recommend this to anyone that has two routers and doesn't want to buy a new wireless adapter for a computer. It was easier than my post made it sound, turns out completely resetting both routers did the trick. (Not just a power reset but restoring it back to factory settings).

---

