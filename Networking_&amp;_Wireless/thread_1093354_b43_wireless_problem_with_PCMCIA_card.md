---
title: "b43 wireless problem with PCMCIA card"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by trevornetley on 2009-03-11
The following is the gist of an email I sent to [email]bcm43xx-dev@berlios.de[/email] concerning what appears to be a currently intractable problem with a b43 supported wireless chipset bcm4306 ver3, but on a PCMCIA card which seems to cause problems. **I am not looking for 'try this-try that' type of response since I have solved the problem to my own satisfaction by reverting to bcm43xx driver**, however I thought I should post to the forum as well as to bcm43xx-dev, both for information and to see if any better-informed member has a pertinent comment or can see a flaw. I have added the result of the iwconfig and lshw -C Network queries to what is asked for by bcm43xx-dev since that may be more transparent than the lspci they want. I have written up the 'deprecated' bcm43xx driver restoration in [thread]1091247[/thread] in case it is of any help.



I have an Asus WL-100G Deluxe PCMCIA card with bcm4306 ver3 chipset installed in an IBM ThinkPad R40. I have been using this successfully with the now 'deprecated' bcm43xx driver for some while, first of all with ubuntu 6.10 and  WPA-Supplicant and now with ubuntu 8.04 and Network Manager.

**The rest of this post is deleted. Problem solved - I was trying to use the European channel 12 which is not available on Hardy or Intrepid versions of b43. I have moved to 10, since all I needed to do was avoid my close neighbour's channel 11 network.**

---

