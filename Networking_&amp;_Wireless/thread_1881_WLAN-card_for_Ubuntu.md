---
title: "WLAN-card for Ubuntu"
date: 2004-10-23
forum: Networking &amp; Wireless
---

### Post by enquiry on 2004-10-23
Wireless LAN-cards are known for not being the easiest piece of hardware to get to work under Linux.

Is there a specific PCI WLAN-card I can purchase that will work under Ubuntu without any problems? I wouldn't want to purchase a card, only to find out I'll have to spend the rest of my life trying to get it to work... I don't need anything faster than 10 Mbps.

All help is appreciated!

---

### Post by ubuntu-geek on 2004-10-24
These might help you out..

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119)

---

### Post by kingnubian on 2004-10-24
While ndiswrapper and DriverLoader are good solutions, they depend upon Windows native drivers to work. I have used ndiswrapper with some success but wanted a 100% Linux native solution instead. latelty 
I have been burning the midnight oil doing as much research as I can regarding just this and trying to make an educated decision on a Wireless PCI Lan 802.11G lan card that will work. Here is what I've found.

When shopping for a Linux supported wireless card the question should not be what company to look for so much as to what Chipset to look for. There exists a number of  linux driver supported chipsets, more so for 802.11b than 802.11G, two of which have more or less mature drivers available for them. Cards based on the Intersil Prism or the Atheros chips have ongoing Linux support. For the Prism chips, and there are a number of different versions, drivers are available and if I am not mistaken, been included into the linux kernel as of version 2.6.8.1.  For Atheros based cards the MadWifi drivers, [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/), are readily available. There exists a number of good resources listing various manufacutrer's cards and the chips that they use. Here are a few.

Intersill Prism: [www.prism54.org](www.prism54.org)
                        [http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

Atheros:  [http://customerproducts.atheros.com/customerproducts/](http://customerproducts.atheros.com/customerproducts/)

General Information: [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)
                                  [http://www.linux-driver.org/Main/Network](http://www.linux-driver.org/Main/Network)
                                  [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)
                                  [http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html)
                         
MadWifi Debian Packages: [http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)


Be carefull as some manufactures, for example SMC, may produce certain models which change the chipset used depending on the revision. 

I know that other WiFi chipsets, Ralink-Realtek-Intel-ect,  also do have Linux native drivers available but not from what I've seenm, with the ease of Implementation and use as those I've mentioned above not to mention stage of maturity.

Based on my research I have purchases an Xterasys XN-2522G PCI card which uses the PrismGT chip and as soon as I receive it will put it to the test and report my experiences here.  
 :-k

---

### Post by sfw5000 on 2004-10-24
I bought a d-link that uses the atheros chipset and it worked right away, auto-detected by ubuntu! That was slick. The problem is, dlink uses different chipsets for different versions of the exact same card. The card I bough said atheros on the back. I would highly recommend getting a card with the atheros chipset.

---

### Post by kingnubian on 2004-10-24
[QUOTE=sfw5000]I bought a d-link that uses the atheros chipset and it worked right away, auto-detected by ubuntu! That was slick. The problem is, dlink uses different chipsets for different versions of the exact same card. The card I bough said atheros on the back. I would highly recommend getting a card with the atheros chipset.[/QUOTE]



Would that be the G520?? If not what model was it??

---

### Post by sfw5000 on 2004-10-24
[QUOTE=kingnubian]Would that be the G520?? If not what model was it??[/QUOTE]
 yes g520 -- but careful and make sure it has the atheros chipset.

---

### Post by mduduzi on 2004-10-28
My experience has been that it's not enough just to get a model number -some manufacturers use the same model number for cards that a significantly different (e.g. Netgear has some cards with standard MAC while others have a software MAC and you'll be at your wits end trying to figure out why other cards are working but not yours)

Best get a card with the Atheros chipset AR5212. This chipset has good support and is generally spoken well of every where. That's a fairly high performace chipset so the price might be likewise.

I've had good success with the said chipset as implemented by D-Link as detailed below -the price was acceptable too .
D-Link DWL-G650 ver.C2 is a very good card to use. I almost got rid of the card after D-Link support would not ackowledge that their WinXP drivers are extremely inefficient but since using the card -autodetected and installed by Ubuntu- on Linux I'm thourougly please and the loading of the CPU is hardly noticeable. WEP isn't good though and I don't know whether its the AP's fault or the card or the software.

Remember to post if you find a solution that make you glad.



[QUOTE=enquiry]Wireless LAN-cards are known for not being the easiest piece of hardware to get to work under Linux.

Is there a specific PCI WLAN-card I can purchase that will work under Ubuntu without any problems? I wouldn't want to purchase a card, only to find out I'll have to spend the rest of my life trying to get it to work... I don't need anything faster than 10 Mbps.

All help is appreciated![/QUOTE]

---

### Post by kingnubian on 2004-10-29
Well I just ordered the D-Link dwl-G520 VB1 with teh Atheros Chipset so I'll report back to tell of my experiences.

---

### Post by enquiry on 2004-11-01
[QUOTE=mduduzi]Best get a card with the Atheros chipset AR5212. This chipset has good support and is generally spoken well of every where. That's a fairly high performace chipset so the price might be likewise.

Remember to post if you find a solution that make you glad.[/QUOTE]
I've purchased the D-Link DWL-G520 with the Atheros AR5212 chipset. Works perfectly  :grin: I did however experience how difficult it is to find out what chipset there is on different cards. Usually it doesn't say on the box, nor on the web pages for the different manufacturers.

---

### Post by kingnubian on 2004-11-01
[QUOTE=enquiry]I've purchased the D-Link DWL-G520 with the Atheros AR5212 chipset. Works perfectly  :grin: I did however experience how difficult it is to find out what chipset there is on different cards. Usually it doesn't say on the box, nor on the web pages for the different manufacturers.[/QUOTE]


Check out my first post in this thread above, I list some very good sites that will help people do just this. While I did purchase a DWL-G520 myself, I asked the seller directly to confirm the version and chipset of the card I was getting and it is Atheros. Not all sellers are that helpfull though.

---

### Post by orkid on 2007-01-01
Do you know there is any USB card that uses the atheros chipset and works automatically with linux?

---

### Post by orkid on 2007-01-01
> **orkid said:**
> Do you know there is any USB card that uses the atheros chipset and works automatically with linux?

Or maybe more general question: Does WLAN card with USB interface exist that is natively supported (out-of-the-box) by linux. (I mean that the driver is included in Ubuntu distribution by default)

---

### Post by grzesiekp on 2007-01-02
out of the box support in Ubuntu 6.10  ASUS WL-167g IEEE 802.11b/g USB 2.0 Wireless Adapter
got mine at: [http://www.newegg.com/Product/Product.asp?Item=N82E16833320107](http://www.newegg.com/Product/Product.asp?Item=N82E16833320107)

---

