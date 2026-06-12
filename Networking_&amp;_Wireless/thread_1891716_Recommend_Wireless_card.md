---
title: "Recommend Wireless card"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by jowilker on 2011-12-06
I started a thread over the weekend, did a lot of grunt work for another member and came up empty handed.

So 2nd attempt, Is there a PnP Wireless card that will work in an older HP PC with 11.10 installed? I currently have Anatel 0949 with RTL 8185L, that keeps getting an error message: Authentication required by Wireless network.

I see other cards advertised at Walmart, CompUSA for around $15.00. I have spent several hours chasing this issue and am tired of it.

I currently have a DLink 615 router set to WEP with several current users, and I really would rather not have to reconfigure it, if I don't have to.  



John

---

### Post by jaimeaux on 2011-12-06
So... what I'm getting from this is that the same password/passphrase works for everyone else, but you? maybe you should reinstall the drivers for that card (but I bet you already have)... maybe it has something to do with the program used to connect. Have you tried reinstalling that?

---

### Post by kurt18947 on 2011-12-06
Is this a USB adapter?  Here is something I posted:

[http://ubuntuforums.org/showthread.php?t=1888673&page=2](http://ubuntuforums.org/showthread.php?t=1888673&page=2)

I've never tried a PCI card so no help there.

---

### Post by jowilker on 2011-12-06
Any ideas on this one? 
Sabrent PCI-G802 PCI Wireless Card - 54Mbps, 802.11g, Windows/Mac/Linux Compatible

[http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2697](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2697)


John

---

### Post by kurt18947 on 2011-12-07
> **jowilker said:**
> Any ideas on this one? 
Sabrent PCI-G802 PCI Wireless Card - 54Mbps, 802.11g, Windows/Mac/Linux Compatible

[http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2697](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2697)


John

No firsthand experience but this looks promising:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Sabrent_PCI-G802](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Sabrent_PCI-G802)
**Sabrent PCI-G802**

 		 			 			 												 			** Sabrent PCI-G802**

 
[LIST]
[*] Chipset: RaLink RT2561/RT61 802.11g PCI
[*] pciid: 1814:0301
[*] Driver: worked out of the box on Ubuntu
[/LIST]
 ** Info**

 ndiswrapper not needed, use native drivers

---

### Post by jowilker on 2011-12-08
Thanks Kurt, I did see this at the bottom of the page "This page was last modified on 12 August 2010, at 10:25."

I wonder if it will work with the new kernel in 11.10??



John

---

### Post by kurt18947 on 2011-12-08
> **jowilker said:**
> Thanks Kurt, I did see this at the bottom of the page "This page was last modified on 12 August 2010, at 10:25."

I wonder if it will work with the new kernel in 11.10??



John

My experience is that once something works OOB, it will continue to do so.  Hardware modules are part of the kernel AFAIK and although things that have been obsolete for *years* are removed,  hardware that is relatively current should continue to be supported for some time.  I'd think the CompUSA device is probably a safe bet.  Something to consider with PCI devices is antenna position relative to your wireless access point.  My configuration is such that any PCI card with attached antenna would have the desktop case between it and the WAP.  I'm pretty sure that wouldn't work well :).  Some PCI cards have remote antennas but I just went with a Netgear WNA1100 which comes with its own cradle.  That has worked well for me.

---

### Post by jowilker on 2011-12-09
OK Guys, I am posting with the wireless card installed in the Dell. It found it right away, a little notice appeared, I clicked the little icon at the top, chose my network, plugged in the pass word and it took off.

Too soon to say that it will stay, but it is working now, cruzing at 35,000 ft.    


John

---

### Post by kurt18947 on 2011-12-09
> **jowilker said:**
> OK Guys, I am posting with the wireless card installed in the Dell. It found it right away, a little notice appeared, I clicked the little icon at the top, chose my network, plugged in the pass word and it took off.

Too soon to say that it will stay, but it is working now, cruzing at 35,000 ft.    


John

Congrats!! I love it when a plan comes together.  My experience is that when something installs & just works, it will continue to do so.  Normal system updates shouldn't break it.

---

### Post by jowilker on 2011-12-09
You guys wont believe this. I shut the Dell off, pulled the card, restarted it, it would not start. It took several tries got it to do a rebuild and it finally redeemed itself.

I put the card in the HP took it to a local computer shop. I had to leave it, the guy called me a couple hours later, saying he fired it up and it connected to the open wireless no prob. He couldn't splain it, other than it has to be my Dlink WEP. I bring it home fire it up it will not boot, screen stays dark.

One connect and it kills it.


John

---

### Post by kurt18947 on 2011-12-10
> **jowilker said:**
> You guys wont believe this. I shut the Dell off, pulled the card, restarted it, it would not start. It took several tries got it to do a rebuild and it finally redeemed itself.

I put the card in the HP took it to a local computer shop. I had to leave it, the guy called me a couple hours later, saying he fired it up and it connected to the open wireless no prob. He couldn't splain it, other than it has to be my Dlink WEP. I bring it home fire it up it will not boot, screen stays dark.

One connect and it kills it.


John

If the card won't work in 2 machines it may be a victim of SEDS (sudden electronics death syndrome).  It happens.  You should be able to exchange it.  Sorry to hear of your bad luck.

---

### Post by jowilker on 2011-12-10
Kurt, it did work once in both machines, it killed the machine. I can not boot the HP machine, was able to recover the Dell.





John

---

### Post by kurt18947 on 2011-12-11
> **jowilker said:**
> Kurt, it did work once in both machines, it killed the machine. I can not boot the HP machine, was able to recover the Dell.
John

Oh dear, murder/suicide?  I've never heard of a PCI card killing a motherboard but not being a pro, I suppose it's possible -- some sort of short on the board or other flaw.  Sorry to hear about it.  I wonder if you could remove the CR2032 battery that maintains BIOS settings, let it sit for a day then replace the battery and try to boot it again.  It may not work but the price is right, cheaper than a new machine or motherboard.

---

