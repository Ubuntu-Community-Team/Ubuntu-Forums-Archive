---
title: "iPhone Can't Find Ad-hoc Network"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by nesquik on 2011-06-09
I'm trying to share my laptop's ethernet connection via WLAN with my iPhone 4, but the network won't appear in the iPhone's Wi-Fi networks list.

I selected "Create New Wireless Network..." and called it "UbuntuAdhoc". I tried each security type. Manually typing in the SSID doesn't work either.

Windows 7 + Connectify works perfectly.

Acer Aspire 5051AWXMI, running Ubuntu 11.04
Wi-Fi adapter: Broadcom BCM4318

---

### Post by Plumtreed on 2011-06-09
This may sound like a dumb comment but this point wasn't mentioned in your thread. Do you 'start up' you AdHoc connection in the laptop?

---

### Post by nesquik on 2011-06-09
> **Plumtreed said:**
> This may sound like a dumb comment but this point wasn't mentioned in your thread. Do you 'start up' you AdHoc connection in the laptop?

Yes.

---

### Post by Plumtreed on 2011-06-10
I don't have an iPhone but invariably I have to search for the AdHoc connection in a 'Hidden Network' section when I want to connectanything. Does something like 'Search for a Hidden Network' appear?
You also need to edit your AdHoc to 'Share with other computers'.

---

### Post by nesquik on 2011-06-10
Yes, it's set to Ad-hoc mode and "Shared to other computers" method. Ubuntu Network manager also says "Connection established". But it still doesn't appear in the iPhone's networks list. When manually typing in "UbuntuAdhoc" iPhone says "Could not find the network "UbuntuAdhoc"".

---

### Post by nesquik on 2011-06-10
Solved, I'm now using ndiswrapper.

---

