---
title: "(another) WPA2 Enterprise / TLS Problem"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by wackywendell on 2009-03-15
I just installed Crunchbang Linux (based on Ubuntu 8.10), and my wireless isn't working with WPA2 Enterprise with TLS.

I was previously using vanilla Ubuntu 8.10, and before that 8.04; I had trouble with 8.04, but after upgrading to 8.10 I think I may have done some minor tweaking to get the wireless working with the WPA2.

When I select an unencrypted network with nm-applet, it works fine; but when I select the secure network, and use the same username, 3 certificates, and password as worked before, it fails. The systray icon goes to the two circles with rotating blue swoosh, with one green and one grey, and the tooltip says "Attempting to connect to network ..." (where ... is the network I want to connect to".

This, of course, might be a Crunchbang issue; however, I know very little about wireless, much less about linux and wireless, and I don't even know what commands to run to find out where its not working. When I run lspci, dmesg, or ifconfig (some commands I saw around), I don't see any glaring things that say ERROR: (something that looks vaguely like wireless), but if you tell me what output you want to see, I will be happy to post it.

The only error I can find is when I go to tray icon > Edit Connections > Wireless > Edit the secure connection, then hit OK without even changing anything, I get an error that says "Updating connection failed: client-cert." This happens even if I delete that connection and recreate it.

Thanks for your help in advance!

---

