---
title: "Wireless card help."
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Jrmurph3 on 2011-05-05
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP

Those are my authentication capabilities, obviously.  I am using a WEP encryption for my wireless router and according to this, it will not allow me to connect. Is there anyway to allow that? The wireless card works just fine in Windows, even on the same network encryption type.  Using a Intel Wireless/Pro 4965 ag. 

Note* this is my mother's router and whatnot. She won't change it the encryption type.

EDIT: SOLVED. MAKE SURE YOU CHOOSE THE CORRECT SECURITY SETTINGS. WEP 128-BIT PASSPHRASE IS DIFFERENT FROM WEP 128-BIT KEY. DUH!

---

### Post by gordintoronto on 2011-05-06
WEP is not secure, it has been cracked.

---

### Post by bart1452 on 2011-05-06
Since this is a general topic heading, In 10.10 I have a similar but reversed situation. My WPC54G card and WRT54G router will use WPA1 and WPA2, and under one window the card is set up to use WPA2, which the router is looking for, but the connection window only offers WEP and something about 802.XX. I can't log in because the right protocol isn't offered.

How do I get the connection window to offer WPA?. I reinstalled drivers in the NDISwrapper. No good. I used to run an open system but decided to lock it down, but it seems like it used to work OK under 8.04.

---

