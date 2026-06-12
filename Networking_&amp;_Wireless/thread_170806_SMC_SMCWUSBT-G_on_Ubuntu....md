---
title: "SMC SMCWUSBT-G on Ubuntu..."
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by Stealth on 2006-05-05
I recently bought a USB wireless adapter. Look through the wiki it seemed to be a good choice (SMC) as they are supported out of box. Unfortunately it seems it was meant for PCI or PCMCIA cards. However, this USB adapter is Atheros based, so I'm sure I can get it working one way or another. According to [this page here]("http://72.14.203.104/search?q=cache:cZD0f4FvYs8J:ndiswrapper.sourceforge.net/mediawiki/index.php%3Ftitle%3DUbuntu%26printable%3Dyes+SMC+SMCWUSBT-G+in+Ubuntu&hl=en&gl=us&ct=clnk&cd=1&client=firefox-a") brought up by Google, they are talking about using NDIS and:

> With the SMCWUSBT-G (USB) card, it works like a charm by compiling from source the latest version (1.8)...

It seems someone was using this same device for their ndis setup. "Works like a charm" makes me think he had it working fine. SO I'm pretty sure I can get mine working to. I see it under lsusb, also lists it under under usb:4, in usbhost, as usb UNCLAIMED. An AR5523 chipset it seems, from Atheros Communications. So the device is detected for sure. Now the drivers...

I'm assuming that the built in drivers don't work, as Ubuntu gives me no signs that I plugged the key in. I read something that madwifi doesn't support many USB adapters yet, so it looks like I gotta use NDIS. I can't seem to figure out how to use it though. I get the drivers from [here]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=5&userPartNumber=&modelNumber=1467&partNumber=3182&downloadType=0&os=0") but I don't see any .inf files as its an Installer. However, searching for them I see a folder called drivers in the SMC utility's folder (after installing it under Windows). There's 2 inf files there but installing them in via NdisGTK (or w/e the name of the GUI program is) says that the "hardware present: no". So...uhm...help? :D

---

### Post by Stealth on 2006-06-27
Well, almost 2 months later I have a small update on this. :-P

I'm pretty sure I got the right files needed in Ndis, because now ndis shows driver present AND hardware present (of course, only when the key is plugged in, otherwise its not present :-P) so ndis seems to detect it now, unfortunately I get no device (like eth0 or wlan0 as some wiki's I've read said should have) so what's up?

---

