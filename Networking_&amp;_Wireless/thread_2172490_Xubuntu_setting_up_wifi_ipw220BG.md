---
title: "Xubuntu setting up wifi ipw220BG"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by Antonio_Cappuzzo on 2013-09-05
Ya hello im pretty new to ubuntu i installed a non pae kernel on my laptop but i have no internet connection.
It displays that im connected to the SSID but i cant access my router if i unplug the ethernet cable
may someone could help me getting it run?

---

### Post by coffeecat on 2013-09-05
I presume you mean the Intel ipw2200bg chipset.

I'm just guessing at potential problems here as it has been some years since I used that device. It's an old chipset and I wouldn't be surprised if it can't handle WPA2. Check your router wireless settings and make sure wireless is set to mixed WPA2/WPA or WPA only. Also, if it's a N-capable router make sure the settings allow it to connect with G (802.11g protocol) and is not set to N only.

You say:

> It displays that im connected to the SSID

Can you describe in more detail what you see?

---

### Post by Antonio_Cappuzzo on 2013-09-05
> **coffeecat said:**
> I presume you mean the Intel ipw2200bg chipset.

I'm just guessing at potential problems here as it has been some years since I used that device. It's an old chipset and I wouldn't be surprised if it can't handle WPA2. Check your router wireless settings and make sure wireless is set to mixed WPA2/WPA or WPA only. Also, if it's a N-capable router make sure the settings allow it to connect with G (802.11g protocol) and is not set to N only.

You say:



Can you describe in more detail what you see?

Well if i unplugg the ethernet cable i wont get access to the internet or router but it displays that im connected -.-

---

### Post by Jonathan Precise on 2013-09-05
> **Antonio_Cappuzzo said:**
> Well if i unplugg the ethernet cable i wont get access to the internet or router but it displays that im connected -.-

Well, it looks like it doesn't renew the IP addresses properly (that happened to me once).

---

