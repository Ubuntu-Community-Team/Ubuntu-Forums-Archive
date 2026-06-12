---
title: "Wireless problems with laptop (TE2100)"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by roncrump on 2006-04-23
Hi,

I am having a problem with my wireless network. The network will appear to be working happily, for a long period of time, with just our Win XP laptop connected to the router/ADSL modem and accessing the internet.

However, when I connect my Breezy laptop (Toshiba TE2100) it will connect for a couple of minutes then the connection will drop and it will indicate that I have no signal for the network (a little red diamond). Cannot then reconnect, even though network manager does try to.

There appears to be a secnd network running (called default) when the problems occur. I tried changing the channel on the router from 1 to 11, and if anything this has made it worse.

This problem appears, in my mind anyway, to have become worse. Could it be due to a Breezy update?

When I obtained the laptop, I did not know it had wireless built in, so I bought a PCI card. Installing Ubuntu with this card in place made this the default, is there any way I can access the internal wireless instead to see if this makes a difference? I think the internal wireless is 802.11b (but I may be wrong) in which case the new card is quicker and preferred in the long term.

Is it possible that the 'default' network is not real and that I am in some way creating it and hence my own conflict? In which case, where would I look to find it and delete it?

Any suggestions at all appreciated, it is driving me a little (more) nuts.

Thanks,
Ron

---

### Post by spd106 on 2006-04-24
For the internal card use **lspci** to see what kind it is and look on this wiki page to see if it's supported [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards").
You could also try ndiswrapper as it works with most cards and it's windows driver.

There are many external influences on wireless networks, but they should stop it working completely all of a sudden. If your card supports scanning try **sudo iwlist wlan0 scan** to see what other networks are nearby and their power or signal to noise ratio. Yours should be the strongest.

---

### Post by roncrump on 2006-04-27
Thanks for the suggestions. I'll have a play over the weekend.

---

