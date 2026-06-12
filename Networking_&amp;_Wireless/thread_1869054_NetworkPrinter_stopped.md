---
title: "NetworkPrinter stopped"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by geofff on 2011-10-25
Over the last few days I've been trying to understand what has happened to stop all printing across the home network. I have two linux and one windows machines with wired connection via a router to a network printer. One box is on Ubuntu 10.10 and one on 11.4. 

After much head scratching it now seems that printing stopped after temporarily connecting a laptop in order to load linux mint which caused DCHP to reallocate addresses. The printer address was moved from 192.168.1.5 to 192.168.1.6. Having discovered this I presumed that I could simply reset the printer settings in System>Administration>Printing with the new ip address. On the windows box I deleted existing printers and reloaded, and this worked. On the Ubuntu 10.10 box it didn't. (My son still hasn't got round to testing his Ubuntu 11.04 box but I presume the same fixes will work there if needed). Ubuntu caused big problems.

I first attempted to load a new printer via Printing>add>find network printer, which it duly did. I added this printer to the list of printers, made it my default and tested. No joy. Printer properties gave 
Description: HP Color LaserJet CP1515n
Location: Blank 
Device URI: dnssd://HP%20Color%20LaserJet%20CP1518ni%20(770932)._pdl-datastream._tcp.local/
A test page wouldn't print and neither would anything else.
In 'Location' I manually added 192.168.1.6 but still no result. 

I went to Printing>help>troubleshoot which provided a status message warning: Printer 'HP-Color-LaserJet-CP1515n': 'com.apple.print.recoverable'. The same message which meant absolutely nothing to me was given when hovering the cursor over the print icon on the panel. The end of the diagnostic told me "sorry, there is no obvious solution to this problem".

After various searches I found the launchpad bug page about 'com.apple.print.recoverable':[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/447940]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/447940") and attempted to follow the supposed fix it gave, but again to no effect. 

Eventually I decided that the Device URI that the printer search had picked up must be wrong but didn't know what it might be. Further searches led me to [http://www.linuxformat.com/forums/viewtopic.php?p=47272]("http://www.linuxformat.com/forums/viewtopic.php?p=47272"). Eventually I discovered that deleting the dnssd address and replacing it with: socket://192.168.1.6 worked - I was at last able to print. Subsequently I've also discovered the following document [http://www.cups.org/doc-1.1/sam.html#COMMON_NETWORK]("http://www.cups.org/doc-1.1/sam.html#COMMON_NETWORK")which gives useful information about URIs for different printers, courtesy of grandtoubab at:
[http://ubuntuforums.org/showpost.php?p=8206382&postcount=4](http://ubuntuforums.org/showpost.php?p=8206382&postcount=4)

I hope this might help someone facing similar problems

Geoff

---

