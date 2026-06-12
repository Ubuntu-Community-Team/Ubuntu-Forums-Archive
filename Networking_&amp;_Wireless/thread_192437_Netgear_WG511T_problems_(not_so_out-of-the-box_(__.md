---
title: "Netgear WG511T problems (not so out-of-the-box :(  )"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by NaOH on 2006-06-08
I'm curious if anyone has encountered problems with the WG511T on Dapper.  It seems the general consensus is that this cardbus wireless adapter is good to go out of box.  I've tried connecting on Breezy and Dapper but with no success.  The card is seen under network as ath0, the network monitor show it is at least detecting my wireless network, but beyond that no internet (through browser or synaptic or update manager, nil).  I have tried both DHCP and manually entering my network info, still nothing.  I should also note under Network Tools the card is shown as "unkown device," and the LED's flash a simple unchanging pattern, although i doubt that is very pertinent.  Any thoughts?  Is this a job for ndiswrapper?

---

### Post by scarolan on 2006-06-09
Exact same problem here.  I can run iwlist scan from the command line and I see two different networks.  When I attempt to get onto my network, either with DHCP or static IP address, there is no connection.  

I really hope there's a way to make this work.  I need reliable wifi access from this laptop, and I bought this card specifically because the chipset was supposed to be supported by the ath0 drivers. . .

---

### Post by scarolan on 2006-06-09
Maybe this will help you - I got it working by making sure the access point was set to Open, and not Shared or something else.

---

### Post by NaOH on 2006-06-09
hate to ask such a noob question, but how exactly do you set your accesspoint to open?

---

