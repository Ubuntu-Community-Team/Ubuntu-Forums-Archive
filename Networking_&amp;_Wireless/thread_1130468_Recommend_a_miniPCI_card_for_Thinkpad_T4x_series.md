---
title: "Recommend a miniPCI card for Thinkpad T4x series?"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by SeePU on 2009-04-19
I want to get a miniPCI wireless card for my Thinkpad T41.

I am having problems trying to use my Thinkpad T41 in Linux and have tried a few distros including Mint 6 and Kubuntu LiveCDs.

My current card isn't a stock card and as my laptop was used, the seller added a Dell 1370 card which has the Broadcom B4318 wireless card in it.

So:
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

You see this is a common card (mostly in Dells and HPs) but I have had various issues with it so I want a 2nd, backup card and perhaps, will switch it permanently if I can find one that is more Linux friendly.

I noticed that there is supposedly open source drivers/firmware for this Broadcom card but it sure isn't working out of the box for me yet.

I read that some people suggest using ndiswrapper but I'd rather find a more Linux-friendly card and one that works with a less complicated configuration "if possible.  

I was thinking of perhaps, an Intel 2200bg card or even 2915abg card.

Also, I read that Atheros has some that are shipped with Thinkpads so I was wondering if Atheros cards are as good/better/not as good as the Intel cards that can fit in a T4x series.  

For example:
Atheros AR5004X Wireless Network Adapter
[http://www.atheros.com/pt/AR5004X.htm](http://www.atheros.com/pt/AR5004X.htm)

Please recommend!  'Getting desperate here!  I thought one of the *buntus would be good to use with this Thinkpad since they are said to be pretty good with the *buntus.  

Remember though, it has to be a miniPCI network card.  Preferably one that is one of the options for that model of Thinkpad or compatible with the T4x series. 

Thanks!  

*Update:  I believe I'll be getting an Intel 2200bg to try!  Is that a good card for Ubuntu for getting wireless?!?   I need to be able to use WEP AND WPA encryption (for 2 different locations).

---

### Post by chili555 on 2009-04-19
Please research carefully before you invest in a card. Quite a few manufacturers, including IBM and Lenovo, use what's called a whitelist to only allow certain part numbers to be installed and boot the laptop. Please see here and read about '1802 error.'

[http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

Of course, it can be sidestepped by modifying your BIOS. It can and has been done: [http://forum.thinkpads.com/viewtopic.php?f=2&t=64169&view=previous](http://forum.thinkpads.com/viewtopic.php?f=2&t=64169&view=previous)

It's scary!

PS - I had a T23, I now have a T40 and a T60 and they *love* the *buntu!

---

### Post by SeePU on 2009-04-19
> **chili555 said:**
> Please research carefully before you invest in a card. Quite a few manufacturers, including IBM and Lenovo, use what's called a whitelist to only allow certain part numbers to be installed and boot the laptop. Please see here and read about '1802 error.'

[http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

Of course, it can be sidestepped by modifying your BIOS. It can and has been done: [http://forum.thinkpads.com/viewtopic.php?f=2&t=64169&view=previous](http://forum.thinkpads.com/viewtopic.php?f=2&t=64169&view=previous)

It's scary!

PS - I had a T23, I now have a T40 and a T60 and they *love* the *buntu!
Yes, cool!  But, which card is in your T40?!? :-D

I know about using *certain* cards and the one in my T41 now is *NOT* one of the 'choices.'  The previous owner or seller 'hacked' it and I suppose they modified the BIOS so the card could be used and no error would occur.

That's why I thought I might as well seek a Lenovo/IBM-directed card and I know which part numbers to look for.  But, I'm not sure which one to choose that is best for Linux.  I thought the 2200bg would be worth trying, though.

---

### Post by chili555 on 2009-04-19
From the second link:> I wanted to upgrade the Cisco Aironet wireless card to an Intel 2915ABG It's working perfectly out of the box. If I remember correctly, I had to pay about $20 for it on Ebay.

Part of the reason I posted was to catch the eye of searchers and to suggest you prepare for the worst. I'd download the bootable CD and have it ready, just in case.

---

### Post by SeePU on 2009-04-20
I bought a 2200bg card off ebay.   I'm not sure now if it is one that can be used without the BIOS 'fix.'  But, if the BIOS was hacked so the previous owner could use another "non-IBM-certified" card, does it matter?

Anyway, I thought it would not require the BIOS fix but it's a genuine card from a Thinkpad X41 machine, it turns out.  So, I am not sure although someone on that site you gave me said the part number (that will be on my card) doesn't need the BIOS fix.

It is FRU/Part Number:  27K9932

---

### Post by chili555 on 2009-04-20
According to this: [http://www.thinkwiki.org/wiki/Category:T41](http://www.thinkwiki.org/wiki/Category:T41) your T41 came with the Atheros, Cisco Aironet or the IPW2100. 

The problem that may arise is that some of the work-arounds are specific to the card and only the *no-1802* fix is permanent and card-independent. It modifies the BIOS to skip the process of checking for the correct part numbers. You have no way to know what of the many fixes was applied to your T41, so that's why I recommend having the *no-1802* CD burned and ready. CD's are cheap.

---

