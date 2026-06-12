---
title: "What's the most compatable 802.11g USB wirless adaptor?"
date: 2005-02-16
forum: Networking &amp; Wireless
---

### Post by manno on 2005-02-16
I've been trying to get wireless networking to work with Ubuntu, on my laptop that has a busted PCMCIA slot. I've had nothing but problems does anyone know what's the easiest USB 802.11g wireless adapter out there? Hell at this point I'll settle for 802.11b. Any suggestions would be very helpful.

-manno

---

### Post by mendicant on 2005-02-16
The kernel has the prism54 driver:
[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

Also check here:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html)
for other drivers that you might have to build yourself.

---

### Post by manno on 2005-02-16
yeah I saw those prism drivers, the problem is I can only use USB all those cards their are either pci, or pcmcia,  not USB, I was hoping some one out there used a laptop, or pc and a USB wireless adaptor, and could point me in the right direction, as a laptop without wireless, as far as I'm concerned is useless. Thanks for the reply though.

-manno

---

### Post by Tapeworm on 2005-02-17
I bought a Linksys WUSB54G based on the list supported by NdisWrapper. 

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List#WUSB54G](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List#WUSB54G)

I haven't had time to work on my Ubuntu box and set it up though...

Be sure and post your results here whatever you try.

Tapeworm

---

### Post by snackzilla on 2005-05-01
Hi--

I am a total newbie who just installed Hoary recently. I only have a Belkin USB wireless g adapter (model F5D7050). I've seen lots of resources for pcmcia wireless cards (e.g. ndiswrapper), but next to nothing in terms of USB adapters. Does anybody out here know of any how-tos or other resources to getting my USB adapter to work with Ubuntu? Any pointer is greatly appreciated. Thanks.

---

