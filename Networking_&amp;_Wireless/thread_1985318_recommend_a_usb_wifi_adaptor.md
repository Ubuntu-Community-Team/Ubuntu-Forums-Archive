---
title: "recommend a usb wifi adaptor?"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by idiotprogrammer on 2012-05-23
Hi, there, I just learned during the install that my usb wifi 802.11n adapter Linksys AE 1200 does not work in ubuntu 12 unless you try ndiswrapper.

Ugh! Can anyone recommend a usb wifi adapter which works out of the box on a 64 bit Ubuntu? Something not is not too expensive and easy to find (like at Walmart?)  Thanks.

---

### Post by wilee-nilee on 2012-05-23
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by idiotprogrammer on 2012-05-23
Thanks for your help. This information was useful. 

I'm going to summarize what I learned and what I decided. Tonight I will try it out. (If there are problems, I'll add remarks later on this post. 

One of the chipsets recommended by FSF is AR9170 chipset. 

It can be hard to tell which chipset goes with which product. 

ThinkPenguin has linux only free chipsets, 
[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)
and Penguin Wireless N USB Adapter for GNU / Linux looks to cost  $55. 

Another option which is considerably cheaper is TP-LINK TL-WN722N for $25. It has the AR9170 chipset. Here's a query I did to show all newegg comments about the product who mention Linux. Lots of people say good things about it. 

[http://www.newegg.com/Product/Product.aspx?Item=33-704-045&SortField=0&SummaryType=0&Pagesize=100&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux&Page=3#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-704-045&SortField=0&SummaryType=0&Pagesize=100&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux&Page=3#scrollFullInfo)

here's some other feedback about this and other usb card which is more mixed. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)

another version of TP-link TL-WN821N  seems to be ok. But you have to make sure you use an earlier version of the firmware. When you get to version 3, though, the driver is different. 

I also found this list to be helpful (especially the most recent comments: [http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html) ) 

One of the most complicated things about buying an Ubuntu-friendly products is that linux sources suggest chipsets, but manufacturers of these products often don't mention the chipset that their product is. 

But TP-LINK TL-WN722N sounds like a good and affordable bet. Also it was easy to find both online and in stores in my city.

---

### Post by wilee-nilee on 2012-05-23
> **idiotprogrammer said:**
> Thanks for your help. This information was useful. 

I'm going to summarize what I learned and what I decided. Tonight I will try it out. (If there are problems, I'll add remarks later on this post. 

One of the chipsets recommended by FSF is AR9170 chipset. 

It can be hard to tell which chipset goes with which product. 

ThinkPenguin has linux only free chipsets, 
[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)
and Penguin Wireless N USB Adapter for GNU / Linux looks to cost  $55. 

Another option which is considerably cheaper is TP-LINK TL-WN722N for $25. It has the AR9170 chipset. Here's a query I did to show all newegg comments about the product who mention Linux. Lots of people say good things about it. 

[http://www.newegg.com/Product/Product.aspx?Item=33-704-045&SortField=0&SummaryType=0&Pagesize=100&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux&Page=3#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-704-045&SortField=0&SummaryType=0&Pagesize=100&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux&Page=3#scrollFullInfo)

here's some other feedback about this and other usb card which is more mixed. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)

another version of TP-link TL-WN821N  seems to be ok. But you have to make sure you use an earlier version of the firmware. When you get to version 3, though, the driver is different. 

I also found this list to be helpful (especially the most recent comments: [http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html) ) 

One of the most complicated things about buying an Ubuntu-friendly products is that linux sources suggest chipsets, but manufacturers of these products often don't mention the chipset that their product is. 

But TP-LINK TL-WN722N sounds like a good and affordable bet. Also it was easy to find both online and in stores in my city.

Cool, good investigating. :)

---

### Post by idiotprogrammer on 2012-05-26
Update. This $25 USB wifi card worked out of the box. Awesomeness!

---

### Post by wilee-nilee on 2012-05-26
> **idiotprogrammer said:**
> Update. This $25 USB wifi card worked out of the box. Awesomeness!

Cool, that's the way it should be. I think many work that are not listed, I have bought several that were random purchases for others and they worked as well.

---

