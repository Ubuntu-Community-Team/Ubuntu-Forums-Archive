---
title: "Why is my Ubuntu wireless inferior to my XP wireless?"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by zozza on 2011-01-29
Hello, 

I have an EEE PC running 10.04.  I have an inbuilt Atheros wireless card (AR928X) and also an external Alfa card (AWUS 036H) with a 5dB antenna. 

My university has an unencrypted wireless network that students access.  I can see the access point from the library.  If I am sitting at the back of the room then I cannot connect with either the Atheros card or the Alfa card.  Checking iwconfig with the superior Alfa card reveals a signal level of about 60dBm.  Line quality is about 40/70.  

However, when I load XP, I can connect with both the Atheros and Alfa.  The speed is good - like normal broadband.  

This would suggest that Ubuntu has inferior wireless capabilities to XP.

How can I rectify this situation?  I thought the point of Ubuntu is that it was superior to XP.

I can provide any details if people give me the appropriate commands.

Thanks.

---

### Post by gordintoronto on 2011-01-29
If the SSID of the university network includes upper-case, try switching to wicd.

Part of the problem is that some wireless hardware manufacturers are not supporting Linux. "Superior to XP" mostly relates to security and avoidance of malware.

---

### Post by zozza on 2011-01-30
The SSID is in lower case and I tried wicd anyhow with the same results.

I can use both wireless cards with Ubuntu; it's just that they are clearly inferior in terms of signal strength compared to the exact same situation in XP.

Is there really nothing that can be done to improve wireless performance in Ubuntu???

---

