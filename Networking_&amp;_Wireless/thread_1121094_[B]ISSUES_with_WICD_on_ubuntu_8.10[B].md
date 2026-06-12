---
title: "[B]ISSUES with WICD on ubuntu 8.10[/B]"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-04-09
Hi,
I recently had a posting here about not being able to stay connected to the internet for more than an hour or so. 

My PCI wireless card is AWLH 3028 and I used Ndiswrapper to install the card.


The suggestion was to use WICD instead of network manager. I installed it and it worked awesome. It would stay connected for a many hours and then get disconnected. saying "connected to none at 0" and then followed by a address, which i presume is that of the wireless router. When I open the WICD interface, it doesn't even show any networks. Only way to make it work again is to either restart or remove the driver and install it again using ndiswrapper gui.

Also, i remember seeing in one of the tabs of WICD, its not ndiswrapper that is selected, it something else, wtex or wpex or something like that.

I am very new to ubuntu and linux world. Any help would be greatly appreciated.

Thanks a tonne

Vishwa**[B]**[/B]

---

### Post by tlois on 2009-04-09
Is your router set to mixed n, b, g, etc?  I had some issues recently with two Ubuntu computers that were doing the same with dropping signal.  One was just slow.  The one that was dropping out periodically was doing the thing yours was with the connected to none at 0.  I set the router to g only- that's what all our cards had in common, so that worked here at least.

---

### Post by dagarshali on 2009-04-11
hi All,
the wireless router had b and g and I changed it to g only as my card is of type G. But still it got disconnected..is there anything less that I can try?

cheers,
vishwa

---

