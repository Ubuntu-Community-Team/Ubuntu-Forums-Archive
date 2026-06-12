---
title: "Network manager won't recognize WPA network"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by behindtheeye on 2010-01-09
Hi chaps,

We've just swapped our home broadband here to Talktalk and so I'm trying to connect wirelessly to the new D-link router on my Ubuntu 9.10 machine. The network is encrypted with WPA and this appears to be causing my problem.

I was using Wicd as the network manager and this seems to detect the network as being WEP encrypted. I tried entering the passkey here but it wouldn't connect. I decided to revert back to the default Ubuntu Network Manager but when trying to connect using this the connect dialog box only gives me WEP options, not WPA. 

I've changed the router settings to be only WPA and not WPA2 but it didn't make a difference.

I can connect fine using Windows XP on the same machine.

It's been a while since I originally set it up but I seem to recall having to use ndiswrapper to get my D-Link DWL-122 USB adapter working (if that's of any use!)

Anybody got any suggestions? Thanks!

---

### Post by behindtheeye on 2010-01-10
Quick bump

---

### Post by SlyAtBest on 2010-01-10
Hey,

sorry I don't have the solution, but I can confirm I'm having exactly the same issue.  I used ndiswrapper to install my network card.  It displays my network (WPA2 encrypted) but when i click to connect it doesn't allow the option for a wpa or wpa2 key.  I've tried right clicking the connections manager and selecting edit connections and editing the wireless which does allow me to select a wpa2 key but it doesn't do anything :-(

Any help?

---

### Post by behindtheeye on 2010-01-10
Sounds exactly the same, I also edited the connection and saw the WPA option but it doesn't work! Good to know someone else is in the same boat!

---

### Post by SlyAtBest on 2010-01-11
It's always nice to have another person to help *bump* a thread ;-)

---

### Post by Tom Stearns on 2010-01-11
> **SlyAtBest said:**
> It's always nice to have another person to help *bump* a thread ;-)

I have the same experience. My computer is an IBM X24 laptop with internal MiniPCI wireless card. When I install Xubuntu and run it at level 9.04 it finds the wireless card and makes the connection. If I allow the machine to "upgrade" itself to 9.1, which apparently includes networkmanager,  it loses sight of the WiFi network and refuses to connect. My fix is to revert to 9.04 and not allow the "upgrade."  Does this comport? Make sense?

---

### Post by behindtheeye on 2010-01-28
Well I fixed this by buying a (long-overdue) new wireless card, an Edimax EW-7128G which appears to work flawlessly with Ubuntu, plug and play! WPA works fine too ;)

---

