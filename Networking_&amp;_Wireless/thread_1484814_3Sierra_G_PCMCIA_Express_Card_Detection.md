---
title: "3Sierra G PCMCIA/ Express Card Detection"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by flashyrox on 2010-05-16
I am providing this information to anyone who has been having trouble with detection of their sierra wireless 503 pcmcia express card. Or anyone with a pcmcia card coverter and an expresss card 3g modem that fits into a pcmcia card such as the one i have:

[http://www.sierrawireless.com/en/sitecore/content/Sierra%20Wireless/Support/Downloads/AirCard/Data_Cards/Elite_Express_for_Telstra.aspx](http://www.sierrawireless.com/en/sitecore/content/Sierra%20Wireless/Support/Downloads/AirCard/Data_Cards/Elite_Express_for_Telstra.aspx)

The pcmcia card is a converter to a express card. Which means i usually just leave the pcmcia card in the slot and only slot in the express 3G modem into the pcmcia slot when needed.

In ubuntu, detection worked the first time i put the express card into the pcmcia card slot_ but not the next time!!!_.

 I could not figure out why this was, after spending hours on forums without any luck i finally realised that ubuntu was only detecting the pcmcia card and not the express card that i placed inside it.  To put it more simply:

[U]I removed the PCMCIA Express Card converter out of the slot entirely and then when ubuntu started up and i logged in.
i then placed the combined pcmcia converter AND the express modem into the pcmcia slot and it was detected instantly!![/U]

I have spent the last 4 hours  tearing my hair out because i could not figure out why my 3G/HSPA card was not detecting on ubuntu 10.04. 

I hope this helps anyone out there who was having the same issue and that they can save 4 hours of their life by reading this!!

---

