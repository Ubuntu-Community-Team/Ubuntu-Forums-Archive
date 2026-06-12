---
title: "Macbook Pro 5,5 Disconnecting"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Styot on 2010-03-20
To clarify, I have tried on both 9.10 Karmic and 10.04 Lucid and neither have worked, so please don't recommend downgrading.

Now, I have followed the instructions in the online documentation found here: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Wireless](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Wireless)
I installed the wireless driver on my Macbook Pro 13.3" (Macbook Pro 5,5) using the command "*sudo apt-get install bcmwl-kernel-source*".  It sees the wireless network that I'm trying to connect to, and when I select it, I enter the password (I have double checked the password on other computers), and it seems to start to connect.  But after a minute or so of the little spinning wheel in the panel, it says "Wireless disconnected", even if I haven't pressed any keys.

Any ideas?
I'm using the Broadcom STA driver.

To recap, I'm on 10.04 Lucid 64 bit and my Wireless sees networks, but automatically disconnects after a minute of trying to connect.  I'm using the Broadcom STA driver as stated above.

Thanks in advance!

Edit:
The network I'm trying to connect to has a WPA/WPA2 Personal password (as stated by Ubuntu).

---

### Post by Styot on 2010-03-21
Bump.  Can anybody help?

---

### Post by Styot on 2010-03-21
Never mind, I solved the issue.  I apparently wasn't able to connect to the WPA network, although it was saying it was WPA2.  So I changed the router settings to WPA2 (AES) and I can connect now.

---

