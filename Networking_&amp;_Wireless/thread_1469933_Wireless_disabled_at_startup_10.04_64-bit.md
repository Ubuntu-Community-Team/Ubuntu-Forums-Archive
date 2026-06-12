---
title: "Wireless disabled at startup 10.04 64-bit"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by guyspencer on 2010-05-02
I have a Thinkpad x61 with intel wireless chipset. At startup, wireless is always disabled, and bluetooth is always enabled. Function+F5 has no effect. Can you tell me how to enable automatic wireless connection at startup?

---

### Post by beastrace91 on 2010-05-02
> **guyspencer said:**
> At startup, wireless is always disabled... Function+F5 has no effect.

How do you enable it if the function hotkey does not work?

EDIT: Also what kind of wifi card?

~Jeff

---

### Post by guyspencer on 2010-05-02
> **beastrace91 said:**
> How do you enable it if the function hotkey does not work?

EDIT: Also what kind of wifi card?

~Jeff
I right click the wireless icon in the top bar and choose Enable Networking. I don't think thinkpads have a card, per se, but rather built in wireless chip set. Mine is Intel. Function+F5 toggles the bluetooth on and off, and can completely turn off the wireless radio, but it does not turn it on and automatically connect. Even when enabled via Function+F5, the wi-fi signal light is off until I right click and Enable Networking. This all worked in 9.10. I have gone into Network Settings and confirmed that Connect Automatically is enabled.

---

### Post by beastrace91 on 2010-05-03
All laptops have a wireless card ;) post the output of **lspci** and it will tell us what card your thinkpad is sporting.

As for not starting up by default - check your bios settings, some laptops disable the wifi by default at startup. I know this is the case with my EEE PC.

~Jeff

---

