---
title: "Ban a wifi network in Network Manager"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by clconway on 2010-10-26
My wifi connection drops sometimes and, for some reason, Network Manager attempts to connect to my neighbor's network, which requires a password (which I don't know). Is there any way to blacklist a wireless network so that the Network Manager will never attempt to connect to it?

---

### Post by JBAlaska on 2010-10-26
Edit your network manager wireless connection and add the BSSID (MAC Address) of your router. 

Note: This will stop background scanning (Which is what you want), but will disable roaming if you want to connect to another AP. Remove the BSSID if you need to roam again.

---

### Post by clconway on 2010-10-27
> **JBAlaska said:**
> Edit your network manager wireless connection and add the BSSID (MAC Address) of your router. 

Note: This will stop background scanning (Which is what you want), but will disable roaming if you want to connect to another AP. Remove the BSSID if you need to roam again.

But I do want to have roaming enabled by default when I'm not home.
The setting I'm looking for seems reasonable: what if my neighbor was running an open access point and was running [Firesheep]("http://codebutler.com/firesheep") on it? I would definitely want to make sure I never accidentally connected to his network. (That's not the case here, though. It's just annoying, because I don't know the password.)

---

### Post by Parksy on 2010-10-29
Have you tried connecting to that network before?  If you have, I think Network Manager will keep trying.

To prevent it from trying to connect again:
[LIST=1]
[*]Right click the Network Manager tray icon.
[*]Click Edit Connections (I think that's what it's called).
[*]Click on the Wireless tab.
[*]Find that network in the list in delete it.
[/LIST]

---

### Post by clconway on 2010-10-29
I must have tried before, since I can see half a dozen other locked networks with strong signal and it never tries to connect to those. But the network in question is not listed in the Wireless Connections dialog and never has been (maybe because I've never actually connected to it?). There must be a configuration parameter somewhere that makes the Network Manager think this is a good network to connect to, but I can't find it; it's not in gconf or /etc/NetworkManager.

---

