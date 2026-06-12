---
title: "Live CD 9.04 BETA &amp; RT2860 pci : It just works"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by TBerk on 2009-03-27
Had trouble with what amounts to 8.10 (Intrepid Ibex) using a hand configured ra2860STA chipset pci based network card. (My environment is '80211g only' at the moment.)

After ditching the default Network Manager and installing wicd, configuring and running make install, I was able to boot into a dual boot system where Ubuntu just connected to the WPA2 router with out problems.

Then it broke.

Last night I downloaded the 9.04 beta iso image. Today I burned it to a disk, booted from it in 'Live!' mode ("without making any changes to your system...") and other than having to choose which network and entering a password the previously troublesome nic card just went ahead and worked for me.

No configuration necessary.  

Let me repeat that; I'm posting this from a CD booted system using a formerly very manual, hands on, then it worked, then it 'broke', "I don't want to use ndiswrapper" type network card.  A system I didn't have to 'setup' to connect to my local wireless network. I just booted from the CD and typed in a password.
 
The beta may not be ready for prime time yet but with it's immanent release around the corner, I'm going to press ahead with deploying it on this system full time and rely on the Windows partition as a fallback resource.


TBerk

---

### Post by mosaic2s on 2009-03-28
I had similar trouble with networking when I installed 8.04 on a new intel dual core machine. The live CD worked and the networking worked through that. But when I installed it, the network card was not accepting dhcp or anything like pinging etc.

Will try 8.10 - may be the motherboard drivers are not available in 8.04 for this new machine.

---

### Post by TBerk on 2009-03-28
Well as for me I just updated 8.10 > 2.6.27-11 to > 2.6.27-14.

Then I did a ```
sudo make
``` and ```
sudo make install
``` of my rt2860sta drivers. After a reboot I have 'fixed' my "wouldn't auto-connect on startup" problem.

Next step is to find a way to do the upgrade to 9.04 beta from the CD without having to download 800Megs of stuff all over again.

Good luck,
TBerk

---

