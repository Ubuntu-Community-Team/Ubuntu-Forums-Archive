---
title: "Does Ubuntu/Linux support 802.11n speeds?"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Agnaramasi on 2010-02-15
Hello,
I recently replaced my six year old 802.11abg router with a new 802.11n router, hoping to take advantage of the 802.11n-capable wireless adaptor in my new laptop.  Unfortunately, my wireless connection persists in connecting at the 54Mbps maximum. 
My router is Netgear WNDR3700 and my wireless adaptor is Intel Wifilink 5300.
I'm wondering if this is a driver problem specific to my wireless adaptor or if Ubuntu/Linux simply do not yet support the greater 802.11n speeds?
If users could share advice or their own experiences, I would appreciate it.

---

### Post by teward on 2010-02-15
what wifi cards do is decide automatically what interface to use.  If G is a better choice (hence the 54Mbps), it will choose that.

Also, check the router's config, it might have N disabled by default...

---

### Post by Agnaramasi on 2010-02-15
The router is configured to broadcast both A and N (and in the Netgear firmware I don't see an N-only option).  My suspicion is that the linux driver might not be capable of connecting to N networks at speeds greater than 54 Mbps. Unfortunately, I don't have a Windows machine with which I can compare connection speeds. Is there a command to quickly ascertain the wireless mode the Intel adaptor has "selected" to operate in?
I appreciate your help.

---

### Post by poohstickz on 2010-02-15
Many (most?) Intel cards will only achieve transfer rates greater than 54 Mbs for 802.11n when you use AES security. Hence, enabling 802.11n or setting speeds greater than 54 Mbs isn't actually enough to get the faster speeds. If you've just installed a new router, that would be a good thing to check first. You need to make the corresponding change for your laptop too.

There's a lot of good information on this matter in the various [user's guides]("http://download.intel.com/network/connectivity/products/wireless/Intel_PROSetWireless_Software_User_Guide.pdf") that you can download from the Intel website. 

Additionally, you'll may have to enable N speeds via your driver or network manager but a good place to start would be your router's settings.

---

### Post by Agnaramasi on 2010-02-16
Thank you for your insightful reply. I've now determined that 802.11n speeds are indeed possible with my hardware under Ubuntu if I use AES encryption.  But I have run into a new problem, which I will describe in [this]("http://ubuntuforums.org/showthread.php?p=8837539#post8837539") new, more precisely named post.

---

