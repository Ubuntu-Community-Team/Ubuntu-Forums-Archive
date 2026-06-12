---
title: "Linksys DHCP Active IP table problem..."
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by j*tech on 2011-04-03
I recently acquired a Linksys BEFW11S4 v.4 router which I am using for my wired home network (wireless is turned off).  Yesterday I was checking my router settings and I noticed under *"Status>DHCP Clients Table>DHCP Active IP table"* there was a weird looking Client name.  I deleted it and when I checked back this morning it was there again.  I checked my devices (PC, router, Xbox) and none have this MAC.  


How can someone connect to my wired network when wireless is disabled and I have changed my SSID and created a very strong password?  Wouldn't someone need to know my SSID/ password?  I do not have a WEP passphrase currently, but I felt it was not necessary since my network is wired.  


What is my best course of action now?

---

### Post by j*tech on 2011-04-05
Ok, so can anyone tell me how someone could get into my network when wireless is turned off?  I thought wired networks had a higher level of security.  I have UFW on, wireless turned off on my router, and a unique SSID and strong password.  How is it possible im being attacked???  Any info is greatly appreciated, thanx...

---

### Post by pricetech on 2011-04-05
If wireless is indeed disabled, someone would have to connect to your router with a cable, or from the Internet via your WAN connection.

Do you have any way to look for a wireless signal ??  I recall having that issue with a router once or twice where it still broadcast even though it was supposed to be disabled.

By the way, what you listed as a MAC address is an IP address.  The other string of characters isn't a MAC either, assuming you didn't typo.

---

### Post by j*tech on 2011-04-05
If someone was connecting via my Internet connection (modem), wouldn't they still need my router SSID and password to get into my network?  I also have UFW configured to deny all incoming.


Very good point...I am toying with packet sniffers right now (Wireshark and Netstumbler), but I'm going to try and get my hands on my brothers Ipod Touch or a friends laptop...


Thanx :lolflag:, I need to edit that...

---

### Post by j*tech on 2011-04-06
I figured it out.  I was misreading my 360's MAC :redface:.  I was checking for it under System settings when it was under Network settings.

---

