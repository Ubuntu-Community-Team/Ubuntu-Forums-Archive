---
title: "Cannot connect to WPA encrypted router with Netgear WNA3100"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by Tenorman on 2012-01-11
Hi all

I've been trying every source possible to find a solution to this.  I'm running Ubuntu 11.04 and have just bought a Netgear N300 USB adapter, which from various sources I've found out is a WNA3100.  I've installed the Windows XP driver, bcmwlhigh5.inf from the CD, as has been suggested by many, and also tried bcmn43xx32.inf.  Both of these have no problem installing using either ndiswrapper or the graphical interface version ndisgtk (Wireless Network Drivers).  The adapter is recognised and finds plenty of wifi signals (lots from a distance away, the unit itself seems pretty good), but I can't connect to my WPA2 encrypted D-Link router.  It constantly asks for the passkey, which is correct, and doesn't connect.  I've turned off the encryption and it connects fine.  I have seen a few suggestions that I should set the router to pure WPA2, rather than WPA/WPA2 encryption, but unfortunately I can't find an option for doing that with my router.  Has anyone else had problems, or more hopefully solved problems, with this type of USB wifi adapter connecting to wifi routers?

Thanks
Colin

---

### Post by Tenorman on 2012-01-12
*bump*

Has no-one seen this problem before?  Any help at all?

Colin

---

### Post by kurt18947 on 2012-01-12
I have no experience with this device but believe it's a bit of a problem child in Linux right now.  Here is some info on the chipset:
[http://www.wikidevi.com/wiki/Netgear_WNA3100](http://www.wikidevi.com/wiki/Netgear_WNA3100)  **Chip 1:** **Broadcom** BCM43231 
I'm not a fan of NdisWrapper but I think in this case that might be the best solution.  Bear in mind with NdisWrapper that is is intended to use WinXP drivers and if your O.S. is 64 bit your windows drivers must be 64 bit as well. If the drivers from Netgear are in .exe format you'd need to somehow extract the .inf & .sys(?) files. The one time I used NdisWrapper I installed in WinXP then found the .inf & .sys files in Windows and copied them to a flash drive.  I wish I had a better solution for you.

---

### Post by Tenorman on 2012-01-12
Unfortunately this isn't the problem.  I'm running 32-bit so have the WinXP drivers.  I used Wine to run the windows driver installation and then copied the WinXP drivers out of the Wine C: drive.  Used Ndiswrapper to install them - the adapter appears to work.  It finds networks, it connects to open networks, it just won't connect using WPA/WPA2.  Very frustrating.

Colin

---

### Post by richarnd on 2012-07-28
Sorry for the thread necro, but I was able to get this working thanks to help from others. 

What worked for me was switching my router to WPA2 Personal (not mixed), as others suggested - AND switching to TKIP (vs. TKIP+AES) WPA encryption algorithm.

I have no idea why this works.

---

