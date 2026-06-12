---
title: "Broadcom Network card issue?"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by Smartflight on 2010-12-13
I installed Ubuntu 10.10 amd64 online today. I was using 10.04 32-bit before, and the network drivers were easy to find and install. Ubuntu did the job for me and they worked flawlessly. It was a relief I didn't need to search around.

Even though 10.10 (64bit) found the drivers for me, both ethernet and wireless, they do not seem to be working alright. I installed both, made a restart. I found that the WiFi light on my laptop stays on, even if the wireless network is turned off using either the key combination (Fn+F2), or manually turning it off.

Issues with the ethernet? I am right now using ethernet but it does not care to detect the connection. Empathy won't connect automatically as a result- says no network connection. But here I am, posting this. Evidently, there is a connection, right?

Issues with the wireless? The WiFi light stays on all the time, and it isn't able to get hang of the connection I have at home. It just won't show any wireless connections available. When I tried to connect by giving it the SSID and the encryption type and password, it didn't work. Just kept asking for the password again and again (I have checked with the router- the password is correct).

Any help here?
Oh yeah, the card details are in the screen-shot attached.

---

### Post by chemdtn687 on 2010-12-13
I have 2 dell laptops with broadcom cards installed running lucid (10.04).. I might be able to help..

are you using the sta wireless drivers or the bcm43xx drivers..
what model laptop??
what is the output of ifconfig and iwconfig??

---

### Post by Smartflight on 2010-12-14
> **chemdtn687 said:**
> I have 2 dell laptops with broadcom cards installed running lucid (10.04).. I might be able to help..

are you using the sta wireless drivers or the bcm43xx drivers..
what model laptop??
what is the output of ifconfig and iwconfig??

I figured out the issue.
Two proprietary drivers were found, and I accidentally installed both of them.

Solved. Using Broadcom B43 Wireless Driver now.

---

