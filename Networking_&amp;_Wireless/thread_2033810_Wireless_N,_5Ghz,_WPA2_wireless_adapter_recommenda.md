---
title: "Wireless N, 5Ghz, WPA2 wireless adapter recommendation"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by kniwor on 2012-07-27
I need to buy a wireless adapter for my desktop. I would prefer an internal adapter (PCI or PCI-e) with antennas that satisfies the following


Wireless N 300Mbps or more (Not N-card working at 54mbps)
WPA2-Personal
**5Ghz Band**
Ubuntu 12.04 **64bit**
Powerful Antennas
Around $50, or less

The important thing is not that the card merely works OOB with 12.04, but that it works in the above configuration!

Thanks in advance.

---

### Post by kniwor on 2012-07-28
No suggestions at all? Or is it that no adapter works with Ubuntu with the latest standards? I find that hard to believe.

---

### Post by bakegoodz on 2012-07-28
I recommend chipsets that use Atheroes 9k series chipsets. This list is bit out of Data [http://linuxwireless.org/en/users/Drivers/ath9k/devices](http://linuxwireless.org/en/users/Drivers/ath9k/devices)
I recently bought a Ubiquiti SR71e (mpcie) from Amazon for about $50, there nice but expensive. I also got a AzureWave AW-NE772 from a seller on Ebay for $20 that supports all your requirements too.

Oh nevermind you want a desktop adapter huh?
This will help you in your search
[http://www.wikidevi.com/wiki/Special:BrowseData/Wireless_adapter?Chip1_brand=Atheros&Interface=PCIe](http://www.wikidevi.com/wiki/Special:BrowseData/Wireless_adapter?Chip1_brand=Atheros&Interface=PCIe)

---

### Post by kniwor on 2012-07-29
Thanks a lot.

Is this product a good choice?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124342](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124342)

---

### Post by bakegoodz on 2012-07-29
I don't know first hand. But support for it is in the Linux Kernel

---

### Post by kniwor on 2012-07-29
Only one of the adapters on the page you directed seems to fit the criteria, it is this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704133](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704133)

So now it seems my choice is between the Cisco adapter and this one above, if someone has any experience with one or the other, that would be very helpful for me to decide.

---

### Post by bakegoodz on 2012-07-29
I would pick the TP-Link it is the cheapest Dual band PCI express adapter on Newegg and it uses the ath9k driver which I'm partial to because it supports AP and Monitor mode, which may not matter to you if you never do packet sniffing or like the possibility to use it as an access point. Though I've yet to figure out how to setup a 5 GHZ Access Point in Ubuntu, but that is another discussion.

---

### Post by kniwor on 2012-07-29
Thanks a lot, bakegoodz. I guess I'll go with the TP-Link one. Though I will never need to set it up as an AP, I am assuming that it is easy enough to connect to the 5Ghz network using this adapter.

---

### Post by kniwor on 2012-08-07
Update:

Thanks again for the invaluable help, bakegoodz. I just now received the adapter (TP-LINK TL-WDN4800) and it worked as I plugged it in, without making any efforts at all, for the 5Ghz network with above specifications. I will test this thing out for a week and then update the relevant pages to reflect that this adapter is well supported. Cheers!

---

### Post by bakegoodz on 2012-08-12
It is nice when a wireless adapter works out of the box. I got an adapter with a new Ralink chipset and it required a download of a firmware file. (Asus Diamond Black), so annoying.

---

### Post by pellefantus on 2013-05-08
I can vouch for the TP-LINK TL-WDN4800 on 12.04. I get incredible 5ghz speed and very good 2.4ghz speed. Works out of the box.

---

