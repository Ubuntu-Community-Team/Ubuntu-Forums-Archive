---
title: "Wireless adaprer does not recognise my home network"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by Denist@ on 2011-02-10
At home I use ADSL and my machine has no problem to connect to wired network. But I still can not set up my wireless network. Network Manager scans for other networks in range and find few but my own network is not listed. My other machine (Windows 7 OS) does not have that problem. What could be the problem? Is it the encryption of the network? I've tried with Wicd also - no progress. Did anyone else have the same problem? Thanks!

---

### Post by grahammechanical on 2011-02-10
First, if Network Manger is scanning and finding wireless networks, then the wireless adapter is working and Network Manager is doing its job.

Your network should be on the list if it is in range. The encryption method only becomes an issue when you first try to connect to the network. You will be asked to set the encryption method and enter the passphrase. Network manager will remember and try to connect.

How many networks are being detected?  Only a few are listed as available. Others are put under More Networks. Is that where your network is hiding?

Regards.

---

### Post by HouTex on 2011-02-10
I have a similar problem.  I am running ubuntu 9.10.  I have two WAPs--a Linksys and a D-Link 1522 (I need two for my house).  My Broadcom 4310 wirless card (with the STM driver) sees and connects to the Linksys (it did so right out of the box with no issues), but it never sees the D-link 1522.  I can connect to the D-Link by establishing a new wireless net work in NetWork Manager, but Firefox can't open any websites nor can I ping anything.  But the wireless card clearly sees other networks in the area and it connects with no problems to my Linksys.  The D-link 1522 is set to Access Point mode and it is NOT set up as a hidden network.  I've tried everything in the sticky thread re: Broadcom 43xx cards without success.  The D-Link 1522 is set for WAP encryption--but I don't believe that is the problem because I can't access it even if it is configured with no encryption.  I'm wondering if the problem is with the D-link WAP itself.  What WAP or wireless router are you using?

---

### Post by Denist@ on 2011-02-10
The wireless router is COMTREND, it was a FREE gift from the telecom company. Anyway, I just found out, this exact model has serious issues with encrypted networks and buggs very often. I tried to make some adjustments manually but it still doesn't work. I've changed the security type - It is WEP now, I also turned on MAC filter but no result for now :(
Will it help if I 'create' this network in NetworkManager?

---

### Post by HouTex on 2011-02-10
Well, I can connect to my D-Link 1522 by going to "Create New Wireless Network"  but I still can't open up any web pages in Firefox.

---

