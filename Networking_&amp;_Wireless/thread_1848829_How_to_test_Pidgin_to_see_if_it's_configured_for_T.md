---
title: "How to test Pidgin to see if it's configured for Tor?"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by Aegimius on 2011-09-23
Testing my browser to see if is configured for Tor is easy: Yahoo is often in a foreign language, the "is my browser configured for Tor?" page says its working and "whatismyip" gives me foreign IP addresses and not my home router's IP. So Tor is loaded and my Firefox is using Tor. 

Now I just tried to configure Pidgin for using Tor. I changed the proxy settings based on the info on this forum, but I have no easy way of testing Pidgin to see if it is configured properly and running through Tor. About the only "evidence" Pidgin is now using Tor is my account loads more slowly. Are there terminal commands for testing Pidgin to see if it is using Tor? Any suggestions?

---

### Post by haqking on 2011-09-23
> **Aegimius said:**
> Testing my browser to see if is configured for Tor is easy: Yahoo is often in a foreign language, the "is my browser configured for Tor?" page says its working and "whatismyip" gives me foreign IP addresses and not my home router's IP. So Tor is loaded and my Firefox is using Tor. 

Now I just tried to configure Pidgin for using Tor. I changed the proxy settings based on the info on this forum, but I have no easy way of testing Pidgin to see if it is configured properly and running through Tor. About the only "evidence" Pidgin is now using Tor is my account loads more slowly. Are there terminal commands for testing Pidgin to see if it is using Tor? Any suggestions?

I dont think pidgin works well with a global proxy setting.

Best to set each protocol to use the tor proxy instead.

I know gmail has proxy issues which is why i do it on a per protocol basis

---

