---
title: "set up ubuntu karmic or jaunty desktop as a router"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by rossmoore on 2009-12-05
I've struggled to find good howto that has worked for me - can anyone help?
I'd like to set my machine up like this:

1 server. It has a wired network and a wireless card. It also has all my data. I'd like to connect the wired connection to my pppoe modem. I'd like to set up a WPA2 wireless network on the wireless card. I'd like my server to act as router and dhcp server.
So I should be able to surf the net on the server (running ubuntu desktop). And I should be able to switch on my laptop elsewhere in the house and both use the server as a router, connecting me to the internet and also connect to samba shares on the server.

I thought, reading various howtos, that this would be possible with NetworkManager and Firestarter (which would set up the dhcp and necessary nat/routing). That doesn't seem to be getting me anywhere.

I'm happy to use the terminal if someone has the networking knowhow and patience to guide me.

Thanks,
Ross

---

### Post by Iowan on 2009-12-05
You didn't mention which How-To's didn't work for you... Hope [this]("https://help.ubuntu.com/community/Router") one can help.

---

### Post by rossmoore on 2009-12-06
No, you're right. I've tried so many they're all probably getting a bit confused - and quite a few are a couple of years old, so packages have changed etc. That link looks like it would be useful, but it doesn't involve creating a new, WPA2 wireless network as an access point. This is something I should be able to achieve in NetworkManager, but it just crashes.
I'm beginning to wonder if the real problem might be my ath9k PCI wireless chipset driver. I don't know how to find out if it can be put into the master mode that seems to be necessary for this - the chipset is, apparently, supported but the relevenat command (iwconfig wlan0 mode master) fails.

The thing with networking is that unless it all works, you don't know which bit is failing... Very hard to debug.

---

### Post by rossmoore on 2009-12-14
Yes, I can confirm that the issue is setting the ath9k driver to "master" mode. iwconfig doesn't support it for mac80211 drivers (of which ath9k is a part). Instead you are meant to use something called hostapd which I only partially understand - but even this doesn't seem to work.

If anybody knows how to set the ath9k into master mode, or otherwise create a wireless AP with this chipset (atheros 928x) then please let me know.

---

