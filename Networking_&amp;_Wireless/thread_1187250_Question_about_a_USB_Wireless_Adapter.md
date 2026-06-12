---
title: "Question about a USB Wireless Adapter"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Virtua-Touch on 2009-06-14
I have a cheapo USB network adapter from TRENDnet which gets the job done. I have a TEW-424UB USB Wireless Adapter ([Link]("http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=49")) and I would like to know if Ubuntu would be able to use it right from installation. The problem I see is that it only has instructions for Windows machines, so I don't know if Ubuntu would use it out of the box. Any ideas?
[IMG]http://www.trendnet.com/image/products/photo/TEW-424UB_d1_1.jpg[/IMG]

---

### Post by kapoperry on 2009-07-24
you've likely already resolved the issue, but for posterity's sake, I just went through a few hours of torture, and would like to document my pain (I'm not the most advanced of linux users).

I purchased a trendnet wireless n pci adapter, TEW-643PI, which also has no explicit linux support, and was able to get it working by installing the ndiswrapper module (wonderful instructions found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")), using the windows xp x86 driver found on the cd, or on their website [here]("http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=1258"), and following the manual network configuration instructions found [here]("http://ubuntuforums.org/showthread.php?t=571188&highlight=no+dhcpoffers+received").  One caveat: on the very last step of that last page, sudo dhclient <interface>, I had to run that command once, reset the modem (as I was getting no DHCPOFFERS received), then run it again, and it worked like a charm.  the gui network manager doesn't work for me, hence using the command line.  the wireless card is now recognized, working, and pumping glorious packets into my machine.

if it matters, I'm running ubuntu 9.04, and have a late 2000ish Dell desktop.

given all of that, I am just guessing you can get your model of trendnet adapter to work using similar steps.  good luck.

---

