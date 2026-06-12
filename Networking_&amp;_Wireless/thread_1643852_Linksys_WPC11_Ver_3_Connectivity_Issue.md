---
title: "Linksys WPC11 Ver 3 Connectivity Issue"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by -kg- on 2010-12-12
I have an old laptop (Compaq Presario 12XL400) on which I have installed Lucid 10.04.  The optical drive in this computer is inoperative, so I had to use a Flash drive installation, and the computer is so old that it won't boot to a USB device natively, so I used the Plop boot manager on a floppy disk.  Other than my wireless issue, the installation works perfectly in every aspect.

When I did the installation, I used a USB wireless "dongle" that my nephew supplied, which worked "out of the box" with the Live USB.  The WPC11 didn't work with the Live USB edition, so I figured that I might be able to get it to work once Ubuntu was installed.

According to [this page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WPC%2011"), the WPC 11 ver 3 should work out of the box.  It has the Prism/Intersil chipset and, to my understanding (and the information presented on the same page) should work using the "Orinoco_cs" drivers (though it doesn't).  I have checked using the "lspcmcia" command, and the Orinoco_cs drivers are present when the card is plugged in.

Through research, I've found several threads where the problem was solved by "reinstalling Ubuntu with no wireless networking devices plugged in", of which [this thread]("http://ubuntuforums.org/showthread.php?t=1560968&highlight=wpc11") is the most recent I can find.  Before I do this (no problem really), I wanted to make sure on a few points and find out if I've missed any further fixes for the issue.

Wireless is the only method to connect to high-speed Internet that I have with this computer.  The only other method is dial-up...it has no Ethernet port.  Will this affect the installation such that I'm unable to get the "driver" necessary?  As I said, I connected with the USB wireless dongle, but it seemed to have taken over the networking and would not allow the Linksys to operate.

Again, is there anything I've missed?  I noticed under the "Hardware Compatibility" page (first link above) the following statement:

> Detected in Network Settings as eth0 and started working after WAP details were input

What does that mean?  What are the "WAP details?"  If that is what one would normally put in to connect to the wireless AP/Modem, then all is well.  But if this is some other information that I'm unaware of, then I'll need to know what that is.

---

### Post by -kg- on 2010-12-13
Well, I've resolved the issue, though not in the way I would have preferred to resolve it.  It took 3 experimental re-installations, but I now have a working system, with wireless and without ndiswrapper.

I must say the Orinoco_cs driver is rather touchy.  It is unstable at the best and just doesn't work at the worst, unless the OS is installed and set up ***just right.***  I found out that it ***does not*** like auto-login, and I was never able to find how to transfer control of devices from one to another in network manager.

Only by fresh-installing Lucid with no wireless device installed, then afterward sticking the WPC11 device in the PCMCIA slot could I get it to work properly.  Of course, strangely enough it seems that the vers. 2.5 and vers. 4 use a Realtek chipset, while the vers. 3 uses the Intersil/Prism chipset.  Figures I'd get the weird one!  :P

I'm still interested in how one would go about it were I to decide to switch to another device on this laptop.  It isn't likely to happen, but it would be good knowledge in the event that I or someone else were to be forced to go through it.

As an addendum...I just turned the computer on and started to show Dad how to use it.  Guess what?  The crazy thing wouldn't auto-connect!  When it does that, it also will not show any "Available Networks."  The only way to connect is to select "Connect to hidden wireless network", select my network from the menu, then hit the "Connect" button.  It will then connect to the AP/Modem.

I can't understand why it doesn't display that network as available in the first place?  All my other wireless devices (including that one, under Windows) not only show my network, but my next door neighbor's as well, as available networks.  This won't, and after connecting to my network the signal strength is pretty good.  The thing is, I've seen it display available networks, but it usually doesn't.

It still isn't working properly, so even though I can connect the laptop to the wireless modem, I technically can't mark this thread as solved.  Either the driver is buggy or I'm not setting something up right.  Any ideas, anyone?

---

