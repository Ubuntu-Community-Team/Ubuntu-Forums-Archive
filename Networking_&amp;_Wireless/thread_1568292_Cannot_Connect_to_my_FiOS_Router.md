---
title: "Cannot Connect to my FiOS Router"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by superhawk_saves on 2010-09-05
Hi, I recently just upgraded my operating system to Ubuntu 10.04 LTS and I can't seem to get my wireless card to connect to our new Verizon Actiontec router.  I am using an Encore Electronics 802.11n Wireless USB Adapter (model: ENUWI-N), which had worked with an earlier version of Ubuntu and our old router.  The adapter recognizes the SSID of the new router but will not connect with the correct WEP key or even with the encryption turned off.  I have tried deleting the wireless profiles and manually re-creating them and still no dice.  I have also gone to the website of the chipset manufacturer and found the [latest drivers]("http://www.ralinktech.com/support.php?s=2") (RT2870USB(RT2870/RT2770)) for the adapter, which, according to the Synaptic Package Manager, I do not currently have installed.

Where do I go from here?  Do I need to install the new drivers, and if so how do I do that?

Any help is greatly appreciated.

---

### Post by bilkay on 2010-09-05
Have you tried connecting with another device? If you have dual-boot, try connecting with the other OS.

---

### Post by superhawk_saves on 2010-09-05
> **bilkay said:**
> Have you tried connecting with another device? If you have dual-boot, try connecting with the other OS.

I originally switched to Ubuntu because my Windows XP kept giving me looping blue screens on start up.  I managed to get it working and the USB adapter does connect to our router with WEP encryption enabled while running Windows.

---

### Post by superhawk_saves on 2010-09-07
any other help?  I'd really like to know how to install the proper drivers if anyone knows.

---

### Post by wmatthews on 2010-09-07
> **superhawk_saves said:**
> any other help?  I'd really like to know how to install the proper drivers if anyone knows.

All I know so far is that it uses the RT2870 chipset so you should be able to use the driver for that chipset.  

I found [this]("http://ubuntuforums.org/showthread.php?t=766850") and [this]("http://ubuntuforums.org/showthread.php?t=960642") in the forum.

Hope this helps!

---

### Post by superhawk_saves on 2010-09-08
> **wmatthews said:**
> All I know so far is that it uses the RT2870 chipset so you should be able to use the driver for that chipset.  

I found [this]("http://ubuntuforums.org/showthread.php?t=766850") and [this]("http://ubuntuforums.org/showthread.php?t=960642") in the forum.

Hope this helps!Followed the directions given in these threads and now the adapter works properly, THANK YOU! :D

---

### Post by wmatthews on 2010-09-08
No problem...

---

