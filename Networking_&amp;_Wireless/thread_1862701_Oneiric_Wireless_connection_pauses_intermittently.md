---
title: "Oneiric: Wireless connection pauses intermittently"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by Harami on 2011-10-17
Hi! This is my first post on the forum and I hope that I am following the posting etiquette.

The wireless connection pauses on my laptop. The network manager shows that I am connected but if I monitor the connection speed, there is zero download and upload with an occasional few bytes per second activity. This continues for a while during which all internet activity is crippled. Ping etc. fails to send out packets. With divine intervention, the connection suddenly starts working again. These cycles repeat when I connect to both secured (WPA/WPA2) and unsecured networks.

The connection works perfectly when I switch to Windows 7 so the adapter seems to be fine. I have another laptop (with a different card running Lucid) on which the connection seems to work seamlessly (even while the one in question gets stuck), which probably suggests that there is no issue with the routers either.

I am using a Thinkpad T420S with a Realtek RTL8188CE WiFi adapter. The driver in use (by default) is rtl8192ce.

I would be grateful for any assistance. Thanks in advance!

---

### Post by Harami on 2011-10-17
I have attached the output of ```
dmesg | grep wlan0
```

---

### Post by GadiCohen on 2011-10-17
I had a similar problem, but eventually noticed that even though all the other wifi devices in the house were working, they were working much slower than they should, compared to the single wired desktop (2mbps instead of 8mbps).  Changed the wifi encryption from WEP to WPA2 (long story) and suddenly all the wifi devices, including my - until then - barely useable oneirc upgrade - all started working perfectly at full speed.  Hope that helps.

---

### Post by androscelta on 2011-10-19
Exactly the same problem, running on MSI U270 with same net card rtl8192ce. Connection pauses every couple of minutes on WEP Wifi and WPA Wifi. It only works properly with unprotected wifi nets or by wired connection.

I would apreciate some helps. thanks!

---

### Post by Harami on 2011-10-19
> **GadiCohen said:**
> I had a similar problem, but eventually noticed that even though all the other wifi devices in the house were working, they were working much slower than they should, compared to the single wired desktop (2mbps instead of 8mbps).  Changed the wifi encryption from WEP to WPA2 (long story) and suddenly all the wifi devices, including my - until then - barely useable oneirc upgrade - all started working perfectly at full speed.  Hope that helps.

Thanks for the assistance GadiCohen, but my problem occurs with the WPA/WPA2 connections. I have not tested with a WEP connection yet. Moreover, I am using the university network so change is not an option for me.

---

### Post by androscelta on 2011-10-19
I have tried to follow the instructions in the forum, so I've checked the wiki of [supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), and I found that you can download original driver from realtek webpage and compile it. For sure you can find how to compile on the net.
I have donde that, and now there are no pauses, although the speed is slower than with 11.04 (at least at home with WEP, I'll check with WPA)

Regards.

---

### Post by Harami on 2011-10-31
> **androscelta said:**
> I have tried to follow the instructions in the forum, so I've checked the wiki of [supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), and I found that you can download original driver from realtek webpage and compile it. For sure you can find how to compile on the net.
I have donde that, and now there are no pauses, although the speed is slower than with 11.04 (at least at home with WEP, I'll check with WPA)

Regards.

Thanks for your suggestion androscelta. My laptop is already using the rtl8192ce module which is what is also offered on the Realtek website.

Can someone please help?

---

