---
title: "good wireless adaptor for 9.10?"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by bovus on 2009-12-26
I'm looking to buy a wireless USB adapter that I can easily configure in NetworkManager without any trouble.  I'm looking to buy it from either [**newegg.com**]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=31&name=Wireless-Adapters") or [**tigerdirect.com**]("http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=2688&name=Wireless-Adapter&").  I've looked on [**this**]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless USB Adapters") site for advice but the list seems to out-of-date.  Could you please provide some suggestions on a brand/ model to purchase?  Thanks.

PS.  I am running Ubuntu 9.10 32-bit desktop edition.  The router I will be connecting to will most likely by a linksys router that will be password protected.

---

### Post by bovus on 2009-12-27
anyone?

---

### Post by coffeecat on 2009-12-27
> **bovus said:**
> I've looked on [**this**]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters") site for advice but the list seems to out-of-date.

Yes, it's hopelessly out of date, but some of the links under the heading 'By Manufacturer' are semi-useful.

The main problem with giving you a direct recommendation is that manufacturers have a habit of changing the chipset but not changing the model number, just the revision number. So if someone recommends a particular brand and model number, that recommendation is not particularly helpful. An example. A link from the link you gave:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)

Look at what Belkin has done with the F5D7050. I happen to have two F5D7050's. They have different chipsets - Zydas and Ralink - and both work well with Ubuntu. But I wouldn't want to struggle with the Realtek one. At the moment, here in the UK, Belkin are using Ralink, which came in handy when I bought one for a relative running Jaunty. It 'just worked'. So I might be tempted to suggest this:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2893259&CatId=2688](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2893259&CatId=2688)

... except that there's no guarantee that US Belkin F5D7050's are shipping with the same chipset as UK ones.

There's a consumer law in the UK that says if I buy from a distance seller (over the internet) I have the right to return the goods within 10 days and get a refund - no reason given. Do you have a similar law where you are? If so, you could order that and, if it doesn't work, ask for a refund.

---

### Post by bovus on 2009-12-27
Thanks!  I'm going to try my luck with the Belkin adapter you suggested.  There was a customer review that stated it "just worked" on Ubuntu 8.10 so hopefully it works the same for me!

---

### Post by lindsay7 on 2009-12-28
The card form Edimax work well too.

---

### Post by sau99ms on 2010-03-16
> **coffeecat said:**
> Yes, it's hopelessly out of date, but some of the links under the heading 'By Manufacturer' are semi-useful.

The main problem with giving you a direct recommendation is that manufacturers have a habit of changing the chipset but not changing the model number, just the revision number. So if someone recommends a particular brand and model number, that recommendation is not particularly helpful. An example. A link from the link you gave:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)

Look at what Belkin has done with the F5D7050. I happen to have two F5D7050's. They have different chipsets - Zydas and Ralink - and both work well with Ubuntu. But I wouldn't want to struggle with the Realtek one. At the moment, here in the UK, Belkin are using Ralink, which came in handy when I bought one for a relative running Jaunty. It 'just worked'. So I might be tempted to suggest this:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2893259&CatId=2688](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2893259&CatId=2688)

... except that there's no guarantee that US Belkin F5D7050's are shipping with the same chipset as UK ones.

There's a consumer law in the UK that says if I buy from a distance seller (over the internet) I have the right to return the goods within 10 days and get a refund - no reason given. Do you have a similar law where you are? If so, you could order that and, if it doesn't work, ask for a refund.
Hi,

Do you know if the UK version of the Belkin G USB wireless adaptor will work on xubuntu 9.10 out of the box or will it require some installation/tweaking?

Thanks,

Mark

---

### Post by coffeecat on 2010-03-16
> **sau99ms said:**
> Hi,

Do you know if the UK version of the Belkin G USB wireless adaptor will work on xubuntu 9.10 out of the box or will it require some installation/tweaking?

Thanks,

Mark

Double-check what I wrote in my December post and also the information in the first link in my post. The answer is: "It depends."

The best you can do is go into whichever store you are going to use (PCWorld, Staples, whatever), get the precise model number from the box - i.e. not just 'FWD-7050', but what comes after the 7050 and any revision number - and check it against that link and hope for the best.

For what it's worth, the one I bought for a relative I bought from one of [Bennett's]("http://www.bennettsonline.co.uk/stores.asp") stores, mainly because they were stocking one which came with a dandy little USB stand, which makes things tidy when using a desktop. I noticed that the Belkins stocked in other stores were just the bare dongle without the stand, clearly intended for an (older) laptop. Whether they had the same chipset as the one I bought, I have no idea.

However, if you want a USB wireless dongle that is guaranteed to work in Ubuntu, have a look here:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

At the moment they're selling a D-Link one which has printed on the box, "Works with MacOS X, [SIZE=4][COLOR=Red]Linux[/COLOR][/SIZE] and Windows." \o/ I'm glad they put Windows last. :wink:

---

### Post by sau99ms on 2010-03-18
> **coffeecat said:**
> Double-check what I wrote in my December post and also the information in the first link in my post. The answer is: "It depends."

The best you can do is go into whichever store you are going to use (PCWorld, Staples, whatever), get the precise model number from the box - i.e. not just 'FWD-7050', but what comes after the 7050 and any revision number - and check it against that link and hope for the best.

For what it's worth, the one I bought for a relative I bought from one of [Bennett's]("http://www.bennettsonline.co.uk/stores.asp") stores, mainly because they were stocking one which came with a dandy little USB stand, which makes things tidy when using a desktop. I noticed that the Belkins stocked in other stores were just the bare dongle without the stand, clearly intended for an (older) laptop. Whether they had the same chipset as the one I bought, I have no idea.

However, if you want a USB wireless dongle that is guaranteed to work in Ubuntu, have a look here:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

At the moment they're selling a D-Link one which has printed on the box, "Works with MacOS X, [SIZE=4][COLOR=Red]Linux[/COLOR][/SIZE] and Windows." \o/ I'm glad they put Windows last. :wink:

Thanks for the link, Coffeecat! Hope all is well in E. Anglia!

Cheers,

Mark (in Wiltshire :) )

---

### Post by ruudspark on 2010-03-18
Hello, I plugged in a Belkin F5D 7050 Wireless G and a Belkin N ver: 3000x wireless usb adapter. Both worked with no problems. I am considering trying a Belkin N1 Express card for my Hp PC as it wont stick out so much! Hopefully it should work as well as the other 2.

---

