---
title: "Connect wireless printer"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by mringer on 2008-12-27
PC running X-Ub 8.04; printer is a HP photosmart C4380. Connected by wire to the USB port, it works. I would like to run it wireless. All of the relevant posts that I have seen appear to assume that the printer is wired onto a PC which is a dedicated print server, but I want the printer to actually run wireless. The printer's test page shows that it does not know what network it should be connecting to or what encryption to use. HP's manual tells me to use the disk that came with the printer, but this only works on WINDOWS . 

So: is it possible to program the printer in UB?

If so then the next problem I expect is that all the S-ware I have seen for connecting to a network printer requires me to enter the IP address. How do I discover that address? Since the printer presumably uses DHCP, the address will change: will I have to go through that performance every time I want to print anything?

---

### Post by mringer on 2008-12-29
Continued: I borrowed a Windows PC & tried the HP disk. This is badly designed, it is amazingly slow & it gives incorrect & misleading error messages. But it did actually work (after telling me it had failed).
So now the printer knows what network to connect to & what encrypt key to use and now the UB PC can connect to it. 

Score: windows 1 Ubuntu nil

---

### Post by jheaton5 on 2008-12-29
I have an HP Photosmart C8180. I also have a Linksys/Cisco wireless router.  When I turn the printer on, it goes through it's setup and automatically seeks out the wireless network which assigns it an IP address.

On my computer running Ubuntu 8.10, I installed HPLIP.  During the printer setup, it found the network printer and all was well.  Or so I thought.

The next time I cranked up the printer, the router assigned it a different IP address.  HPLIP did not scan the network to find the printer. Instead it assumed that it was still at the old address and gave me an error message saying that the printer was disconnected.  I have researched the net and this forum and have found many with the same issue.  Apparently, the only solution is to set the printer up with a static IP address.  My work around has been to set up a new printer each time the IP address changes under dhcp.  This way I can simply look at the HPLIP setup page to see which printer is connected and use that printer to print.  All the printers are set up with the same name except the last three characters in the name are the last three digits in the IP address.

---

