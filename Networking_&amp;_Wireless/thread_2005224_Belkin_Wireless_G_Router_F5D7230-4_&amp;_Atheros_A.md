---
title: "Belkin Wireless G Router F5D7230-4 &amp; Atheros AR9285 802.11b/g/n WiFi Adapter"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by trulynon on 2012-06-17
Hello Everyone,

I'm completely new with Linux. I moved from Win 7 and I'd like to stay with Ubuntu. However, I having annoying problem with my Belkin Wireless G router and my Atheros WiFi adapter. Every time when I try to watch video on YouTube or download a large file my connection is dropping/freezing and I need to disconnect Belkin router to reset it. 

As far as I remember, I have the same problem on Windows, but It wasn't so often as I experienced on Ubuntu. I resolved this problem - partially - on Win 7 updating drivers, however I don't know if need to update drivers on Ubuntu? I installed Ubuntu yesterday and flowed all needed updates. 

I working on HP Probook 4530s, but I also have another laptop in my house - Sony Vaio,  and this is my girlfriend lap. However her laptop is working fine with Belkin router - I haven't experienced dropping/freezing issue. Her computer running on Win Vista. 

What's your advice, guys? What should I do? This is very annoying, because every 8-10 minutes I need reset router. When I try to open some pages my connection is dropping/freezing. I should also pointed that when I connect to modem (without wireless) I don't any problems browsing the WEB. I'll appreciated your help. Thanks

---

### Post by trulynon on 2012-06-17
Hi again. 

By far I  can say that I solved a problem as it mentioned here

```
http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/
```

> If you are using Ubuntu (and probably other distributions too) and you have an on board Realtek RTL8168/8111E PCI Express network adapter you might find your network not working as it should. Slow connections or no connection at all and your logs full of messages like these

This was a trick! Apart of Atheros I also have Realtek network adapter in my laptop. Updated drivers for Relatek solved the problem. Please close this thread. Thanks

Mariusz

---

### Post by kurt18947 on 2012-06-17
> **trulynon said:**
> Hi again. 

By far I  can say that I solved a problem as it mentioned here

```
http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/
```

This was a trick! Apart of Atheros I also have Realtek network adapter in my laptop. Updated drivers for Relatek solved the problem. Please close this thread. Thanks

Mariusz

You can mark this thread as "solved".  There should be a 'thread tools' box near the top of the page.  This also helps others which may have similar problems and search here for help.

---

