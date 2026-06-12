---
title: "Pauses with Network Manager/wpasupplicant on Atheros"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by Scraplab on 2006-06-18
I've just got a Gigabyte WIAG-02 mini-PCI card - it's Atheros based (5005GS, I believe). It replaced a 3Com Atheros PCMCIA card, which worked fine.

I've got a strange problem where every couple of minutes I see the Network Manager connection strength drop to 30%, and the connection freezes. After approximately 10 seconds, it's back at full strength again. It's fine in Windows.

Syslog shows a lot of activity by wpa-supplicant and DHCP. I've included the dump of syslog for the last 1000 odd lines, chopped off a bit to show the start of one of the drops. Bear in mind that this has been happening for the last few hours.

Any ideas what's going on?

---

### Post by twisted_steel on 2006-06-20
I think I have a similar problem with the built-in Atheros card on my Thinkpad T42.  Every so often, the signal drops to 1 bar in the NetworkManager applet, and my connection just stops.  It reconnects itself shortly, but if I do anything too intensive right away - like loading a large webpage, the connection will drop again and the process will start over.  I find that if I leave it alone for a few minutes, it will be fine for another few days (I turn my laptop off at night, and on in the morning/afternoon).  It doesn't seem to be a problem with using up a lot of the connection, as when it's working I can stream music, download torrents, copy files, and do whatever I want.

I was thinking that maybe it's a problem with WPA key negotiation or something that eventually sorts itself out, but this is just a guess.

EDIT:
I'm using the ath_pci driver according to lsmod, but wpa supplicant seems to be using the madwifi driver.

---

