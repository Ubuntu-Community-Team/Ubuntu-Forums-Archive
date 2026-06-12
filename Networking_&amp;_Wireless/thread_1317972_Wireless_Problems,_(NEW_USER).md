---
title: "Wireless Problems, (NEW USER)"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by barnesey on 2009-11-07
Hi,
I am a new Ubuntu user as i decided that windows is a pain on my laptop, so i installed the new Ubuntu (9.10). 
I have so far like the OS however i am having problems using my Netgear WG111T Wireless G Adapter. I have tried many thing to see if i can get it to work but failed. I have installed ndisgtk package and installed the drivers but no play, I was also recommended to use WICD and it did not work at all. I have now removed WICD and now i cant find the network manager that came with Ubuntu.
I do also have another wireless card and it is a Netgear WG511 v2, but i have not attempted to use it yet as the WG111T does not work.

If anyone knows how to fix this quickly and easily please help me as i need wireless to work asap.

---

### Post by Menestrello on 2009-11-07
When you installed WICD, it removed your network manager.
To get it back, remove WICD and search into your synaptic packet manager if you still have network-manager and network-manager-gnome cached in your memory and install them; otherwise you need to download them again (sudo apt-get install netowrk-manager network-manager-gnome), assuming that you can connect your computer in any way.
Otherwise download those 2 packages from another computer, copy them onto yours and execute them with the packet manager.

About the not working wireless, I don't have any tip...other than try some workaround (like using the Ubuntu 9.04 version of network-manager and network-manager-gnome as I'm doing...)

---

### Post by Cato2 on 2009-11-07
Regardless of wicd vs. NetworkManager, the WG111T doesn't work with Linux very well.  You can use ndiswrapper to get it working with Windows driver, but that will never be as stable.  If you value stability more than the cost of a new USB dongle, get one that does work well without ndiswrapper.

[http://linuxemporium.co.uk/products/wireless/](http://linuxemporium.co.uk/products/wireless/) has a short list of WiFi dongles/cards that definitely work, and will support them.

---

### Post by placo on 2009-11-07
just worked on this issue, had the same problem and did the same thing, removed the gnome network manager and installed wicd, with which i could not establish a connection, due to wicd could not get an ip-address and the karmic cd was at a friends place, too far to go and get it
i could not install the previous network manager, because i no longer had internet connection
i reset my modem, so it was no longer password protected and got on the internet again, downloading the karmic iso again to burn the cd

and yes, installing wicd did it for me, internet fast as normal!

got problems though to secure my wireless connection again, wicd does'nt seem to deal with it

---

### Post by barnesey on 2009-11-07
Kl, I am now going to download the 2 packages to my pendrive to get the manager back. I am now thinking now thinking if mg WG511 will work, also thinking of Cato2's advice on getting a new usb adapter which may save some time.
 
What would wireless cards you recommend on using, Using Wireless N possible. i have looked at the link from which Cato2 has put thetre but i am unsure what would be best to get.

---

### Post by sergio jose dias on 2009-11-07
Try the solution this link: 
[http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html](http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html)

---

### Post by Cato2 on 2009-11-08
> **barnesey said:**
> What would wireless cards you recommend on using, Using Wireless N possible. i have looked at the link from which Cato2 has put thetre but i am unsure what would be best to get.

For 802.11g, pick any of the ones on that page, but they don't sell 802.11n as that's still quite bleeding edge.

There don't seem to be many 802.11n products that are supported for Linux so that will need some research.  Do you need 802.11n for coverage / throughput?  Unless you are sure that you need this, 802.11g is much easier with Linux, and costs less.  

802.11n also only helps if you have 'multipath induced' interference - i.e. various paths from the sender to receiver, causing the different paths to interfere.  If you simply have a long range requirement, or thick walls, or metal structures, then 802.11n will not necessarily help - see [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/555001371931?r=688006671931#688006671931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/555001371931?r=688006671931#688006671931)

If you need better WiFi coverage, consider staying with 802.11g and using a cheap antenna plugged into a WiFi router (check compatibility but 802.11g routers usually let you do this) - makes a huge difference to coverage even with thick brick/stone walls in a large house, and is by far the simplest option to get good coverage.  Unlike 802.11n, this works with every device out there including phones, iPod Touch, game consoles, etc.  See [http://www.wifi-antennas.co.uk/index.php?target=products&product_id=14](http://www.wifi-antennas.co.uk/index.php?target=products&product_id=14) for the kind of thing I'd go for - it's about a foot tall and costs £15.  You might also need Tomato firmware on your router to let you boost power, but the antenna is the main thing.

If you really want to use 802.11n, try emailing the guys at Linux Emporium, and also search forums for the best option - based on  [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers) I'd guess that an ath9k based dongle/card is best, and that's supported by the vendor, but that site is based on bleeding edge kernels, so you would probably need to use Ubuntu 9.10 Karmic and possibly compile your own WiFi drivers.  Some research is needed anyway since 802.11n is so new (approved in September 2009: [http://en.wikipedia.org/wiki/IEEE_802.11n-2009](http://en.wikipedia.org/wiki/IEEE_802.11n-2009)) - e.g. it works best in 5 GHz band, but that has shorter range inherently as it's higher frequency.

Some notes from my 802.11n wiki page (please excuse the wiki syntax):

[[[http://ask.slashdot.org/comments.pl?sid=1095363&cid=26496087](http://ask.slashdot.org/comments.pl?sid=1095363&cid=26496087) Must check if 802.11n routers support 5 GHz band]], for full speed

Draft-N notes from some time ago:
   * [[[http://forum.notebookreview.com/showpost.php?p=2666640&postcount=18](http://forum.notebookreview.com/showpost.php?p=2666640&postcount=18)  Good summary of best Draft-N routers]] - should support DD-WRT, Asus WL500W sounds good.  See also rest of thread - Asus WL500W (better than Linksys) is Intel certified for client 802.11n kit - not all draft-N kit works with Intel client hardware.
   * [[[http://www.asus.com/products.aspx?l1=12&l2=43&l3=0&l4=0&model=1277&modelmenu=1](http://www.asus.com/products.aspx?l1=12&l2=43&l3=0&l4=0&model=1277&modelmenu=1) Asus WL500W page]]
      * Need to check on [[[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=19538&postdays=0&postorder=asc&start=0](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=19538&postdays=0&postorder=asc&start=0) DD-WRT support for WL500W]] - it is officially [[[http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Asus](http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Asus) supported by DD-WRT V24 RC3]]

[[[http://www.wirevolution.com/2007/09/07/how-does-80211n-get-to-600mbps](http://www.wirevolution.com/2007/09/07/how-does-80211n-get-to-600mbps) 802.11n feature explanation]] including next version.  Link to a PPT about how 60 GHz doesn't go thru concrete but does well thru reflections and hence multipath.

[[[http://www.smallnetbuilder.com/content/view/30224/100/](http://www.smallnetbuilder.com/content/view/30224/100/) Mixing G and N devices incurs a hit]] - about 50% on both.

[[[http://www.smallnetbuilder.com/content/view/30387/96/1/5/](http://www.smallnetbuilder.com/content/view/30387/96/1/5/) 2-antenna WAPs aren't as good as 3-antenna]] - review.  However, 40 MHz band (which interferes with neighbouring b/g networks) required to show difference, not so much in 20 MHz band.

[[[http://www.smallnetbuilder.com/](http://www.smallnetbuilder.com/) SmallNetBuilder]] has good reviews and advice

802.11n supports both 2.4 GHz and 5 GHz - latter is more attenuated by walls but scatters better so may do well if multipath reflections are feasible.

---

### Post by barnesey on 2009-11-09
Its is mainly when i am at collage i am in need a better coverage. The collage is a large building but i don't know where the access point is. 
 
Is it worth it to get a wireless n adapter for the better range when i am at collage?

I am also possibly getting a Wireless N router as well. I have been doing some research and have found some adapters that work with Linux. 

I am unsure if i should get one now or wait later until other adapters have come out, 



Thanks for helping a new user :lolflag: 
BARNESEY

---

### Post by Cato2 on 2009-11-10
Using 802.11n on your laptop won't help at all unless your college has already deployed 802.11n WAPs (wireless access points) - very unlikely as this standard is so recently approved.

Your best option is to try:

- a different WiFi card (PC Card / Cardbus) or USB stick that may have better radio performance - if  you go USB, you can get an up to 5m USB extension cable to put the stick somewhere with better reception in same room.  You can also play with aluminium foil to block interference such as cordless phones etc in direction not pointing to WAP.  Not very elegant or mobile but can work.

- A WiFi card or USB stick that includes a better antenna - this will probably work better if you have marginal signal.  See [http://www.google.com/search?q=wifi+usb+antenna](http://www.google.com/search?q=wifi+usb+antenna) for examples, or [http://www.keenansystems.com/store/catalog/product_info.php?cPath=2&products_id=137](http://www.keenansystems.com/store/catalog/product_info.php?cPath=2&products_id=137) which has a 2 dBi antenna and connector for better antennas if needed (but requires ndiswrapper under Linux)

It will help if you read up on how to interpret WiFi radio specs, both receive sensitivity and transmit amplification are important.

On 802.11n at home, I would really encourage you to go the 802.11g route - buy a 'g' router that supports Tomato (really good firmware and easy to use, and lets you boost power) and also lets you add a replacement antenna if needed.  802.11n is just a bit bleeding edge on Linux if you have a choice of using 'g'.

---

### Post by barnesey on 2009-11-13
Hi,
The collage as 8 WAP's but i don't know what they are, I am going to say now i am a IT student but knows nothing about Linux. 

I am thinking of getting a Wireless G adapter for the moment. At the moment i am in no hurry. I am yet to see if there is any with good signal antennas. 

With the router i am using the router provided by the ISP / maybe new ISP as i have next to no money to buy one. If my router or the new one will support a additional antenna when i can afford it.

---

