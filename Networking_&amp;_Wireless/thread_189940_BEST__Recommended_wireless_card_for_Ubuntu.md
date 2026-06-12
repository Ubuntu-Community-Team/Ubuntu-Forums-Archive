---
title: "BEST / Recommended wireless card for Ubuntu"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by Sasquatch2000 on 2006-06-05
I can't find anywhere on the site what is a good or recommended card.

That said, what is recommended for wireless cards?

802.11g?
802.11b?
802.11n?

What about the new long range ones from Belkin (and maybe others)?

Thanks.

---

### Post by celem on 2006-06-05
I don't know about best, but I can tell you what "just works", out of the box, for me. I have three PCMCIA WiFi cards that ALL work, out of the box with Dapper - plug and play. This was NOT the case with Breezy. I have an AVAYA Gold, Linksys WPC11-VN version 4, and one that works great but will be hard for you to find because I bought on eBay for $10 - it is a WLAN CB-200B. It is made by Wistron NeWeb Corp but the box is only marked WLAN CB-200B. All of these work great for 802.11B with WEP encryption.

---

### Post by Sasquatch2000 on 2006-06-06
How about the 802.11g? n?

Is there a place I am missing on ubuntu's web site which lists recommended or preferred cards? I have an older PC which I might like to set up, but want to get the right card for it from the get-go rather than diddling around with one extra piece.

Thanks again.

---

### Post by Zed on 2006-06-06
[HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) from the wiki.

---

### Post by jml on 2006-06-06
Two other cards that I use with Ubuntu is the Cisco Aironet 802.11 a/b/g card, and the NetGear WG511T card.  Both are based on the Atheros chip sets.  I would recommend sticking to either a used 802.11b card or the two listed cards that support g as well.  802.11n standard has not yet been ratified.  All these companies selling "n" compatible cards are putting their customers at risk of being left behind once the standard is ratified.  I've also read that the 802.11n "compatible" cards don't communicate well with devices from other vendors.  Plus the newest hardware does not always have the best Linux support.

Joe

---

### Post by polo_step on 2006-06-06
[FONT="Courier New"]Like most people, I don't consider a wireless device "supported" unless it can easily and fairly transparently use its WPA/WPA2/AES capabilities.  WEP is grossly insecure and obsolete, and simply shouldn't be used.

I don't know of **ANY** devices that currently fit that description with 6.06, though a bunch of devices seem to more or less work with limited features.  I plugged in a little zYdas 1211 USB dongle just to see what would happen and it actually set up and found my network, though it of course couldn't access it because of the encryption.



[/FONT]

---

### Post by jml on 2006-06-06
polo-step, I agree with you.  Its not a hardware issue, its an issue with most Linux distros.  They just don't support WPA out of the box.  The only distros that do are Kanotix (based on Debian unstable) and Mandrica2006, and SUSE 10.0 (both RPM based distros.

Joe

---

### Post by Sasquatch2000 on 2006-06-06
[QUOTE=Zed][HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) from the wiki.[/QUOTE]

Thanks, that is a good start, though it covers various versions and not just "this is good for 6.06" type of info. 

Wondering what is the best as far as range, comparing to something like the [Airgo](http://www.google.com/search?as_q=airgo+wireless+distance&num=100&hl=en&ie=UTF-8&client=firefox&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=m3&as_nlo=&as_nhi=&as_occt=any&as_dt=i&as_sitesearch=&safe=images) stuff.

Just delved a little deeper. This looks like what I'd like to try:

[Wireless Pre-N Desktop Network Card Part # F5D8000](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=186931)

---

### Post by jml on 2006-06-06
Wireless range is determined by not only the card but the base station.  Of the wireless cards I reviewed, I have read, and confirmed by reading the spec sheats that cards like the Cicso Aironet 350, and the Cisco 802.11 a/b/g cards have more powerful transmitters in them.  Something like 100mw as compared to 30 mw.  To maximize the range, one  may also want to add high gain antennas to your waccess point as well. (Linxsys, for example offers them as an option for some of their base stations.)  Again, do be careful buying a "pre-n" bit of hardware.  With the stand not yet ratified, you may end up with an orphaned card.

Joe

---

### Post by Sasquatch2000 on 2006-06-06
[QUOTE=jml]...Again, do be careful buying a "pre-n" bit of hardware.  With the stand not yet ratified, you may end up with an orphaned card....[/QUOTE]

Wasn't that the talk with 56flex versus the other 56k technology? In the end, most vendors just let you upgrade through firmware updates to whatever it turned out to be.

---

### Post by James_M on 2006-06-06
[QUOTE=Sasquatch2000]Wasn't that the talk with 56flex versus the other 56k technology? In the end, most vendors just let you upgrade through firmware updates to whatever it turned out to be.[/QUOTE]
Even so, nobody knows, yet how it will turn out, so better safe then sorry.  I gotta say that the older d-link notebook adapters tend to work well.  I think the one I bought was the DWL-G630.  I didn't even have to open terminal.  Ubuntu (Breezy on an old HP) found it and connected me to my non-encrypted AP instantly.  It's worked ever since and I couldn't be happier. I'll post what happens to it when I upgrade to Dapper.

---

### Post by Skye on 2006-06-06
I have a Netgear WG511T, a wireless-G card, and it worked fine out of the box with Dapper because it has an Atheros chipset.  It supports WPA and WEP through network-manager, though I'm not sure what other encryption protocols it supports.

It's a great card in general.

---

### Post by polo_step on 2006-06-07
[QUOTE=jml]polo-step, I agree with you.  Its not a hardware issue, its an issue with most Linux distros.  They just don't support WPA out of the box. [/QUOTE]
[FONT="Courier New"]Incredibly, 6.06 is **less** WPA/WPA2 capable than 5.10 was -- according to some posts I've read here in the past few days.

I can only hope that's because they're working on something better and didn't get it finished in time, as "improved wireless support" has been a stated goal for future Ubuntu versions for some time, and that would presumably mean support for security protocols less than two generations out of date.[/FONT]:(

---

### Post by Gus Engstrom on 2006-06-07
I fought my wireless for a long time. Finally bit the bullet, bought a NetGear WG511T. A little pricey,but it worked RIGHT out of the box. I get good results in a low signal location. Smartest move I made all year.

---

### Post by Sasquatch2000 on 2006-06-07
[QUOTE=polo_step][FONT="Courier New"]Incredibly, 6.06 is **less** WPA/WPA2 capable than 5.10 was -- according to some posts I've read here in the past few days.../FONT]:([/QUOTE]

That seems counter to what was said here:

[Improved Wireless support](http://www.ubuntu.com/testing/dapperbeta?highlight=%28wireless%29)

---

### Post by bionnaki on 2006-06-07
linksys wmp54g works just fine (with WPA) following these easy instructions: [http://www.ubuntuforums.org/showthread.php?t=161376](http://www.ubuntuforums.org/showthread.php?t=161376)

---

### Post by Sasquatch2000 on 2006-06-07
So many conflicting opinions, I started a poll:


[Did the 6.06 release make wireless easier?](http://ubuntuforums.org/showthread.php?t=191557)

---

### Post by chababkk on 2006-06-17
I use ubuntu on my laptop and wireless never have problem in 5.10 but when I use 6.06 TLS is have problem. when I start wireless on networking. it hang not response anything and I can only push power off switch only for reboot it. I use 
Ralink RT2500 802.11 and driver is rt2500.

---

### Post by punkybouy on 2006-06-17
I have a wpc11 ver 4 from Linksys and it does not work at all.

---

### Post by punkybouy on 2006-06-19
[QUOTE=celem]I don't know about best, but I can tell you what "just works", out of the box, for me. I have three PCMCIA WiFi cards that ALL work, out of the box with Dapper - plug and play. This was NOT the case with Breezy. I have an AVAYA Gold, Linksys WPC11-VN version 4, and one that works great but will be hard for you to find because I bought on eBay for $10 - it is a WLAN CB-200B. It is made by Wistron NeWeb Corp but the box is only marked WLAN CB-200B. All of these work great for 802.11B with WEP encryption.[/QUOTE]


Interesting, I have a Linksys WPC11 ver 4 and I could not get it work at all in a 3 year old Dell Inspiron 8200.  Dapper reports it as a Realtek card.  I am still investigating...and running dapper on a desktop.

---

### Post by Sasquatch2000 on 2006-09-27
So, what do people know about these?

[Linksys Wireless-N Products](http://www.linksys.com/servlet/Satellite?c=L_Promotion_C2&childpagename=US%2FLayout&cid=1144421946975&pagename=Linksys%2FCommon%2FVisitorWrapper)

[RangeMax NEXT](http://www.netgear.com/Products/Adapters/RangeMaxNextWirelessAdapters.aspx)

[Share your Internet wider and faster](http://catalog.belkin.com/IWCatSectionView.process?Section_Id=202570)

Do any of them work ***"out of the box"*** with Ubuntu 6.06 (or newer)?

---

### Post by Sasquatch2000 on 2007-03-19
Bump

---

### Post by SactoBob on 2007-03-20
For a desktop, I think it is no contest.  Why not forget about the drivers and use a wireless bridge.  It is a black box that converts the wireless signal back into a standard (1 to 4 port) wire output.  It is totally inaffected by upgrades or changes of distro.  You can even connect the multiple ports to different OS's, i.e. one to a Linux box, one to a Win box, and one to an xBox.

See this thread
[http://www.linuxquestions.org/questions/showthread.php?t=536898](http://www.linuxquestions.org/questions/showthread.php?t=536898)

for totally driverless, totally dependable wireless.  In fact, I'll post my rewrite of that post.  I have the Buffalo ethernet converter, which is a wireless bridge, works way better than any pci card because of its power.  It is $60 at Newegg
=================================================

Since manufacturers' support for Linux drivers is spotty, with some not cooperating at all, using wireless under Linux can be challenging.  Some wireless cards, such as Atheros with madwifi, work well with native drivers.  Others cards may work well with ndiswrapper while a number of cards are simply unsupported.

	A wireless bridge is a versatile and often overlooked solution to wireless headaches.  A bridge is a free standing unit with its own operating system and power supply.  You configure it with your browser.  It connects independently to your wireless LAN and supplies a wired connection to your “bridged” computer(s).  Some wireless routers can operate in bridge mode.  Bridges offer advantages and disadvantages over wireless cards.

**Advantages**

-  _Simplicity_: Since the wireless connection is handled entirely by the bridge, you don't need any wireless drivers. Connected computers see the bridge as a wired connection.

-  _Location_: The bridge can be located up to 100m away for convenience or reception.  It can be moved or transported and connected to another computer.

-  _Connectivity_: Bridges can provide multiple wired Ethernet ports for other computers.

-  _Performance_: High power units function well in challenging reception environments.

-  _Flexibility_: The wireless connection is independent of the OS to which it is connected, and is unaffected by changes or upgrades to the OS.  

**Disadvantages**

-  _Cost_: High performance dedicated bridges cost over $100.  However, less expensive routers, such as ZyXEL's P330W, Buffalo (some, e.g. Wireless Ethernet Converter), and Linksys (some with third-party firmware) can operate in Bridge Mode.

-  _Bulk_:  The unit requires its own power supply and has its own footprint, which can be as large as a typical router.

-  _Energy consumption_: Up to 400 mw for higher performance units.

	For a good review of Linux wireless options, See  [http://socallinuxexpo.com/scale5x/presentations/rex.odp](http://socallinuxexpo.com/scale5x/presentations/rex.odp)  (Open Office format).

	To view the specs, manual, etc. of a typical high performance bridge, see 
[http://www.netgate.com/product_info.php?cPath=32&products_id=361](http://www.netgate.com/product_info.php?cPath=32&products_id=361)

	To see a bridge configuration for the ZyXEL, see [http://gadgetaddict.wordpress.com/20...reless-bridge/](http://gadgetaddict.wordpress.com/20...reless-bridge/)

        A fine performing, $60 bridge (called a Wireless Ethernet Converter) [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)

---

### Post by Sasquatch2000 on 2007-03-20
Interesting. Thanks.

I wonder how the range is on this technology. 

Do you think it would last a while outside, tucked up under the eaves?

---

### Post by SactoBob on 2007-03-20
The range of the high power units is the biggest difference I have seen as compared with cards.  Because the units have their own power supply, I expect, they can have better range.

The Engenius unit that I bought replaced a Win N pci card which was very problematic - always dropping out or losing speed.  The Engenius is admittedly a commercial model designed for hospitals and things like that, but I could not believe going from a very weak signal to a full power signal with an incredible speed increase in a very poor location.  When performance counts, there is no contest, which is why these are the units used for commercial applications.

But even the Buffalo unit I bought, which is also high power but not advertised as a business class unit, has MUCH better range than my pc cards.

For outside, go to netgate.com and check out their outdoor units, which are designed for this.  I am not sure why you would want an outdoor unit.  You still to run ethernet cable out of unit to the computer.

---

### Post by Sasquatch2000 on 2007-05-20
> **SactoBob said:**
> ...For outside, go to netgate.com and check out their outdoor units, which are designed for this.  I am not sure why you would want an outdoor unit.  You still to run ethernet cable out of unit to the computer.

I want it outdoors because it has some trees to see through/around, and I figure the less impediments, the better. 

Any other ideas for wireless options? I saw a device made from, believe it or not, a Pringles can to amplify a directional signal tremendously. Google it, you'll see what I mean. Thanks.

---

### Post by Sasquatch2000 on 2007-10-15
OK, bumping this up for the 7.10 release. 

What is the best or choice of the best wireless cards for version  7.10?

Is  the Belkin Wireless G Plus any good? I am hoping so, as that is what I recently picked up at Staples.

---

