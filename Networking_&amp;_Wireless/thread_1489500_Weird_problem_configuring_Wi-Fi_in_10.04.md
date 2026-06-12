---
title: "Weird problem configuring Wi-Fi in 10.04"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by pranavdes on 2010-05-21
I did a fresh install of Ubuntu 10.04 on my IBM thinkpad R51 laptop and have been facing a weird problem with respect to configuring my Wi-Fi connection. 
At home I have been using a hidden connection with WPA 2 Personal encryption.  Ubuntu detects and installs necessary drivers for my Wi-Fi Device. My home network gets detected when I make it discoverable, but it refuses to connect to it. If I remove the encryption I get a connection. I thought that might be a problem with pass-phrase but it is not. If my home network is hidden with encryption and if I ask NetworkManager to connect to it without any encryption (providing same ssid through Connect to a hidden network) it tries to connect to it. In the mean time (while it is still negotiating and failing (from daemon.log file)) if I again ask it to connect to same network to with encryption turned on it connects successfully. It sometimes happen in one go or I may have to repeat the process of 1st connecting without encryption and then with encryption and it eventually succeeds.  BTW if I try to connect with just encryption (without doing the 1st step) daemon.log mentions timeout in negotiation or something.

I know its not much of a problem but its annoying and I would not like to remove encryption and/or change to being discoverable again.

My router is Linksys WAG 200G with unmodded firmware version 1.00.09 (if that is of any help)

---

