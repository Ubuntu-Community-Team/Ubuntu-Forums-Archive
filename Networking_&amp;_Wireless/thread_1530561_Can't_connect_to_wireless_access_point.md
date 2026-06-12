---
title: "Can't connect to wireless access point"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by jerrynewt on 2010-07-13
I am using a Netgear WPN824 v3 router and a Marvel wireless card via ndiswrapper. I see the wireless networks (with wicd) but when I try and connect it says "could not connect to access point". Any ideas ?? I am running 10.04 32 bit ubuntu on an e-machine.

---

### Post by jerrynewt on 2010-07-14
bump

---

### Post by jerrynewt on 2010-07-16
bump please.

---

### Post by 4hm on 2010-07-17
Have you tried re-installing the driver for your wireless card?  Do you have other computers that have worked wirelessly on your router?

---

### Post by jerrynewt on 2010-07-17
Yes my daughter's windows netbook connects fine and her boyfriend's (Windows) also connects just fine. I will try and reinstall the driver. The wireless network is recognized just fine but will not connect on this desktop with the Marvel wireless card.

---

### Post by gordintoronto on 2010-07-17
Please tell us, "I did X and Y, and expected ABC, but instead Z happened." "Will not connect" carries no information.

If you know the SSID, encryption type and password, it should connect easily.

What Marvel card do you have? Why did you dump Network Manager?

---

### Post by jerrynewt on 2010-07-17
I first tried to use Network Manager and no results in even seeing the wireless network, and I had used wicd in the past on one of my older laptops with graet success, so I installed wicd to see if it would connect. No such luck, so I installed ndiswrapper via Synaptic and installed the driver for the Marvel card. Ndiswrapper says the driver is installed and recognized. While initially trying to set the Netgear router up I am not using encryption and the Access Control feature on the router is disabled for the time being. When wicd scans and finds the wireless network (essid "NETGEAR") and I try and connect it gets an ip address and then says "verifying access point". After about a minute of verifying I get a message box saying "could not connect to access point".

---

### Post by gordintoronto on 2010-07-17
I have also preferred Wicd in the past, but currently prefer Network Manager. It didn't work for you previously because you hadn't installed ndiswrapper. "Verifying access point" is a Wicd message.

Are you using DHCP?

---

### Post by jerrynewt on 2010-07-17
Yes I am using DHCP. Thanks for the response.

---

