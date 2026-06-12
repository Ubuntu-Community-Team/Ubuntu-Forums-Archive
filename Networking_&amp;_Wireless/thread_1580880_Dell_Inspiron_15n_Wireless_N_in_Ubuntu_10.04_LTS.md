---
title: "Dell Inspiron 15n Wireless N in Ubuntu 10.04 LTS"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by OooBuntuRox on 2010-09-24
[SIZE=2] I am interested in upgrading from wireless G to wireless N using this Dell Broadcom card or similar if anyone knows of an alternate internal wifi card for the Inspiron 15n
[see link Below]
[COLOR=Blue]
**[COLOR=Red]LINK:[/COLOR]**[/COLOR]  [COLOR=Blue][http://accessories.us.dell.com/sna/products/Networking_Enterprise_Class/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=430-3130&mfgpid=200183&chassisid=8666#Overview](http://accessories.us.dell.com/sna/products/Networking_Enterprise_Class/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=430-3130&mfgpid=200183&chassisid=8666#Overview)[/COLOR]

[/SIZE]  [SIZE=2]
Does anyone know if there is a Ubuntu driver available that supports an internal WiFi N network card for the Inspiron 15n model? If Dell and/ or Broadcom doesn't offer a driver, does the Ubuntu community offer one?

Has anyone installed this card? If Yes, what comments do you have. It is reliable, easy to install? Or, is it a headache.

**Update: **Actually, I'm not sure what brand the card mentioned above is. A wiki indicates it is an Intel card. RE: [/SIZE]**Wi-Fi Card:** Dell Wireless 1397 802.11b/g half mini-card or Intel Wi-Fi Link 5100 802.11a/b/g/n half mini-card.[SIZE=2] 

All comments appreciated !

Thanks Everyone,

[/SIZE]   [SIZE=2]OooBuntuRox[/SIZE] :guitar:

---

### Post by blakep2 on 2010-09-24
It should the community usually keeps up with newer drivers a wireless n driver I assume is fairly new, am I correct.

---

### Post by blakep2 on 2010-09-24
I did a little research and some people seem to have got it to work
[http://www.cuntud.com/card-1510-wireless/32565/Dell-Studio-XPS-1340-Review-and-Howto-Mike-s-Planet.html](http://www.cuntud.com/card-1510-wireless/32565/Dell-Studio-XPS-1340-Review-and-Howto-Mike-s-Planet.html)

---

### Post by OooBuntuRox on 2010-09-24
> **blakep2 said:**
>  It should the community usually keeps up with newer drivers a wireless n driver I assume is fairly new, am I correct. 




Thanks Blake. Well, It's not like it came out in Ubuntu version 10. I never paid attention to when the N standard came out though. 

> **blakep2 said:**
>  I did a little research and some people seem to have got it to work
[http://www.mikesplanet.net/2009/09/dell_studio_xps_1340_review/](http://www.mikesplanet.net/2009/09/dell_studio_xps_1340_review/)[]("http://www.cuntud.com/card-1510-wire...-s-Planet.html")


An interesting read. It sounds like they did get it to work but a little flakey. I noticed it was a Dell studio and Ubuntu 9.04. I also noticed that he recommended using wireless G if you can get one. That is what I have. Too bad I need to upgrade to wifi-N. I am dropping too many connections with G.

I am hoping that someone will chime in and say they are using a certain Wireless N card (and give the number) in a Dell Inspriron with Ubuntu 10.04 or above. And further comment that it works well.

I had a chat session with Dell earlier today. They really don't seem to like discussing Linux. It seems there are a number of cards that will fit in the PCI Express Internal card slot.

I have seen 1510, 1515, 1520 listed. But an Intel card also caught my attention. It is listed as an Intel 5100. The Intel site also lists a linux driver: [http://www.intellinuxwireless.org/?n=downloads](http://www.intellinuxwireless.org/?n=downloads)

I also found this article specifying various Dell 15n compatibility: [http://www.linlap.com/wiki/dell+inspiron+15](http://www.linlap.com/wiki/dell+inspiron+15)

This is the Dell 5100: [http://accessories.us.dell.com/sna/products/Networking_Enterprise_Class/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=430-3243#Overview](http://accessories.us.dell.com/sna/products/Networking_Enterprise_Class/productdetail.aspx?c=us&l=en&s=bsd&cs=04&sku=430-3243#Overview)

This Intel Page explains that the Intel 5100 drivers are included in the newer kernels:
[http://www.intellinuxwireless.org/?p=iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi)

> 
Using kernels 2.6.24 and up 
These kernels have the iwlwifi driver included and the released drivers (available from this site under download page) do not work with these kernels. If you want to run the latest (or very close to it) development code with your kernel then you should use the compat-wireless project that retrieves the latest driver development code from the upstream repository. We do push our changes to this repository very frequently. 
I also found this wiki: [http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1545_.28Inspiron_15.29](http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1545_.28Inspiron_15.29)
**Pertinent info from the Wiki:**
 
**Inspiron 1545 (Inspiron 15)**

Released online on January 16, 2009, the Inspiron 1545 isa 15.6" budget laptop that weighs 5.8 lbs. The Inspiron 1545 is the first laptop in Dell's Inspiron line to get Design Studio.

**Processors: **Intel Celeron 900, Intel Pentium Dual-Core T4200, T4300 or T4400 or Intel Core 2 Duo T6400, T6500, T6600, P7350, P7450, P8600 , P8700 , Intel Core i5 - 520M , AMD Athlon X2 Dual-Core QL-64 , AMD Turion X2 Dual-Core RM-74 or AMD Turion X2 Dual-Core Ultra ZM-82
 
**Memory:** 2 GB, 3 GB or 4 GB of shared dual-channel DDR2 SDRAM @ 800 MHz. 

**Chipset:** Intel GM45 Express Chipset.
 
**Graphics Processor:** integrated Intel GMA 4500MHD graphics or ATI Mobility Radeon with 256 MB of graphics memory.
 [B]
LCD Display:[/B] 15.6" CCFL-backlit widescreen with a 1366 × 768 and TrueLife or 15.6" WLED-backlit widescreen with 1366 × 768 resolution 15.6" or WLED-backlit display with 1600 × 900 resolution and TrueLife. 

**Hard Drive:** 160 GB, 250 GB, 320 GB, or 500 GB SATA at 5400 RPM. 

**Optical Drive:** 8X tray-load dual-layer DVD+/-RW drive.
 
**Battery:** 4-cell (37 Whr), 6-cell (56 Whr), or 9-cell (85 Whr) Lithium Ion battery. 
[B]
Camera:[/B] 1.3 MP webcam with optional facial recognition software 
[B]
Wi-Fi Card:[/B] Dell Wireless 1397 802.11b/g half mini-card or Intel Wi-Fi Link 5100 802.11a/b/g/n half mini-card. 

**Bluetooth:** Dell Wireless Bluetooth Internal 365 (2.1 EDR). 
I/O ports: 3 USB 2.0 ports, 1 Fast Ethernet port, 1 VGA output, 1 headphone jack, 1 microphone jack, 1 Express Card slot, 1 7-in-1 memory card reader, and 1 power adapter connector.


Now, to make sense of all this info. So far, It is looking like the Intel 5100 is the card to go with. But I am hoping for confirmation from others who have used the Intel 5100 and associated drivers in and Inspriron 15xx successfully. I still have to poke around the Intel mentioned repositories [http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git](http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git) (mentioned above as upstream repository).

To all members, please post comments to help with progress and determining/ isolating the best Dual Band WiFi-N Card for use with the Inspiron 15n / 1545 series Laptop in Ubuntu 10.04 and above.

OooBuntuRox, :guitar:

---

### Post by OooBuntuRox on 2010-10-16
[SIZE=3]Hello Everyone,

I found these links at Intel and Dell. I think this wraps it up for now. In short there are a number of cards, as listed by Intel, that work with more recent versions of Ubuntu/ Linux.[/SIZE] [SIZE=3]The only thing to confirm is board size/ fit before purchasing. I also noticed that Dell now lists the Intel 5100 A/ G/ N (and others) as an option with the Inspiron 15 Laptop (with Windows OS). So, Dell is confirming the hardware compatibility and Intel is suggesting software compatibility with Linux on it's website.

When I get around to the actual hardware upgrade, I will post an update.

[/SIZE][SIZE=3][http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm](http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm)

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&model_id=inspiron-15&oc=dncwzs1&s=dhs&vw=list&fb=1&frb=1](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&model_id=inspiron-15&oc=dncwzs1&s=dhs&vw=list&fb=1&frb=1)[/SIZE]

[FONT=arial][SIZE=3][B]Internal Wireless Card
[/B][/SIZE][/FONT][SIZE=3]Dell 1397 Wireless-G 
[/SIZE] [SIZE=3]Dell Wireless 1515 802.11 Wireless-N Mini-card 
[/SIZE] [SIZE=3]Intel WiFi Link 5100 802.11 Wireless-N Mini Card[/SIZE]



[SIZE=3]Thanks, OooBuntuRox[/SIZE] :guitar:

---

