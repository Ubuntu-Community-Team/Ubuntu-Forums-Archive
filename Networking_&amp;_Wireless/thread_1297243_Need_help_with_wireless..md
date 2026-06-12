---
title: "Need help with wireless."
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by darbielove on 2009-10-21
The network software in Ubuntu does not show my wireless network. my wireless network does show up in Windows Vista. The built in card is a Broadcom 802.11b/g WLAN. The computer model is a Compaq Presario C571nr.

---

### Post by pastalavista on 2009-10-21
Check in System > Administration > Hardware Drivers to see if there are proprietary drivers you need to install. You will probably need to connect to the internet by wired ethernet in order to download the drivers, after which you should be able to use your wireless.

---

### Post by matyd on 2009-10-21
I think you will have to use ndiswrapper to get your wlan working. I had to do this with my compaq presario v2000... You will have to download ndiswrapper onto another computer and put it on your ubuntu computer via cd, usb, etc. 

Check this link out:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

That explains how to install it etc. Hope this helps...

matyd

---

### Post by t0mppa on 2009-10-21
> **matyd said:**
> I think you will have to use ndiswrapper to get your wlan working.

I think not, there's 3 native drivers available for Broadcom cards and they usually work fairly well.

@darbielove: Run **lshw -C network** on terminal and post back with the results to see which Broadcom chip your card is using and if it's getting associated with any drivers by default.

---

### Post by darbielove on 2009-10-21
All I had to do was goto: System > Administration > Hardware Drivers. It only worked after I installed ubuntu. Thank you all.

---

