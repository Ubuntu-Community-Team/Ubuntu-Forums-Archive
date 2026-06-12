---
title: "Airlink AWLL5099 doesn't work in Ubuntu"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by bevboy0223 on 2012-11-13
Hi. I bought a used Dell D410 laptop recently.  The built-in wireless had been removed but the vendor included an AWLL5099 wireless usb adapter.

It works fine in XP, but I quickly put Ubuntu 10.4 on it.  The adapter doesn't work.  Meanwhile a pcmcia belkin adapter works perfectly.  I also have an aged belkin usb wireless adapter, and that works out of the box.

I cannot for the life of me find any drivers to get this adapter to work in ubuntu.  Does anybody know what I have to do to get this working?

Thanks!

Bev in Halifax


[COLOR=#1f497d][FONT=&quot]
[/FONT][/COLOR]

---

### Post by ahallubuntu on 2012-11-13
Component manufacturers like Airlink rarely provide direct Linux support.  Instead, you have to find out what chipset is inside the product.  In this case, it appears that this AWLL5099 has a Realtek 8188CUS chipset, at least according to this:

[http://www.amazon.com/Airlink-compatible-Wireless-Mini-USB-AWLL5099/product-reviews/B006ZZUK5Y](http://www.amazon.com/Airlink-compatible-Wireless-Mini-USB-AWLL5099/product-reviews/B006ZZUK5Y)

You can try downloading and building a driver directly from Realtek's website:


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Through ("Communications Network ICs" - "Wireless LAN ICs" - "WLAN NIC" - "IEEE 802.11b/g/n Single-Chip", "Software,") check the box next to "RTL8188CUS," click "Go," and download the Linux/Unix driver from there. I chose the "HK1" link to get the above. Make sure the page says "RTL8188CUS" at the top before downloading.

Then extract the downloaded file and look for a "README" file of some sort.  You will have to build this in a terminal.

---

### Post by ahallubuntu on 2012-11-13
but you might really be better off installing a new internal wireless card in your Dell.  You can probably buy a used one off eBay for about $10 USD.  Here are Dell's instructions for removing/installing the card in your laptop:

[http://support.dell.com/support/edocs/systems/latd410/en/sm/minipci0.htm#wp1000001](http://support.dell.com/support/edocs/systems/latd410/en/sm/minipci0.htm#wp1000001)

Not too hard to install.  You might open it up and make sure the antenna wires are still in there before proceeding to buy one.

The key is getting a compatible wireless card that will work in your laptop.  They are not all the same.  You might not be able to get an "N" card though but a "G" card will work just fine for basic internet surfing.

I recommend the Intel card if there's a choice - most likely to work automatically in Linux.  I think the Intel 2200BG card is one that works in your laptop.  If you buy one, you don't have to buy a "Dell" version but make sure you get one that's not made for IBM, Lenovo, or HP.  A Dell or Toshiba card (but the Intel part number) should work fine.

---

### Post by bevboy0223 on 2012-11-15
General comment: When Ubuntu works, it works really, really well.  When it doesn't work, it doesn't work on a spectacular basis.  
 
I got the Airlink AWLL5099 for free with the laptop purchase.  It would be neat to get that working, but I also have a PCMCIA wireless N card which works flawlessly.  At least it doesn't tie up one of the precious usb ports.
 
My head began to swim at the thought of opening up my computer and installing a fresh wireless card.  I managed to download the package mentioned in the first answer to my query, but running install.sh didn't make the slightest difference.  Well, it probably added some unnecessary packages to the computer.  I guess I should do a fresh install.
 
Thanks anyway.
 
Bev

---

### Post by sordna on 2012-11-30
> **bevboy0223 said:**
> 
It works fine in XP, but I quickly put Ubuntu 10.4 on it.  The adapter doesn't work.

10.4 ??  I think that's the problem, it's ancient!
Why don't you try a recent version of Ubuntu such as 12.04 or even better 12.10?

---

### Post by royfeldman on 2013-03-07
+1 

I have been researching Realtek based devices like this one, and I see reports that they "work of the box" starting with 11.04.
The bad news is that problems arise again with the latest kernels in 12.10 (quantal).


> **sordna said:**
> 10.4 ??  I think that's the problem, it's ancient!
Why don't you try a recent version of Ubuntu such as 12.04 or even better 12.10?

---

