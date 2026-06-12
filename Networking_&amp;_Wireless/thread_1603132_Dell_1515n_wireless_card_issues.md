---
title: "Dell 1515n wireless card issues"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by lowpsitsi on 2010-10-22
I picked up a Dell 14z a few days back, when it came in the mail I had already had a ubuntu 10.10 usb drive waiting for it. I love the whole OS everything about it is great and I understand that there's going to be some issues. 

Everything runs seamlessly so far for me except my wireless. It tends to be very finicky. It usually says "Wireless Disabled" and it is greyed out so that I cannot enable it. It claims there are no networks both in the network manager and WICD. Which I know isn't true. Now I can ping my routers IP too is the weird thing. I'm running a Netgear WGR614v10 router. DHCP is setup. PPnP is running. 

I have tried installing some closed source drivers but have had issues completing the installations on them. The weird thing is yesterday I went into a coffee shop and all of a sudden a dozen or so connections popped up? It ran great and I began to think the issue had somehow fixed itself or my router was the problem. But as soon as I got home I had the "Wireless disabled" again. And I went back to the coffee shop to find it would no longer detecting any connections. I'm running on a Dell wireless 1515n half card. Which I believe is a broadcomm is some form.

Anybody have some thoughts on this?

---

### Post by Der Ritter on 2010-10-22
> **lowpsitsi said:**
> I picked up a Dell 14z a few days back, when it came in the mail I had already had a ubuntu 10.10 usb drive waiting for it. I love the whole OS everything about it is great and I understand that there's going to be some issues. 

Everything runs seamlessly so far for me except my wireless. It tends to be very finicky. It usually says "Wireless Disabled" and it is greyed out so that I cannot enable it. It claims there are no networks both in the network manager and WICD. Which I know isn't true. Now I can ping my routers IP too is the weird thing. I'm running a Netgear WGR614v10 router. DHCP is setup. PPnP is running. 

I have tried installing some closed source drivers but have had issues completing the installations on them. The weird thing is yesterday I went into a coffee shop and all of a sudden a dozen or so connections popped up? It ran great and I began to think the issue had somehow fixed itself or my router was the problem. But as soon as I got home I had the "Wireless disabled" again. And I went back to the coffee shop to find it would no longer detecting any connections. I'm running on a Dell wireless 1515n half card. Which I believe is a broadcomm is some form.

Anybody have some thoughts on this?

Strange. The 1515n is an atheros card which should be well-supported. Please run
```
sudo lspci -vnn
```then look for the section labelled "Network controller" that mentions "Atheros Communications Inc." and paste that section here.

---

### Post by Der Ritter on 2010-10-22
(sorry, double post)

---

### Post by lowpsitsi on 2010-10-22
11:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:0200]
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: ath9k
	Kernel modules: ath9k

---

### Post by Der Ritter on 2010-10-22
> **lowpsitsi said:**
> 11:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)


OK, apparently that particular card has caused some issues (see [this thread]("http://ubuntuforums.org/showthread.php?t=1194751")).

More than one person reported success by installing the latest package of backports:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```Do this, restart the computer, then fire up wicd and see if it works.

---

### Post by lowpsitsi on 2010-10-22
Thanks for the reply. unfortunately that didnt change it. WICD still says it doesnt detect any wireless connections.

---

### Post by lowpsitsi on 2010-10-28
Still having issues. The card seems to sporadically work. I've gotten wireless to work on my home router a handfull of times off of random reboots.

---

### Post by lowpsitsi on 2010-10-29
bump

---

