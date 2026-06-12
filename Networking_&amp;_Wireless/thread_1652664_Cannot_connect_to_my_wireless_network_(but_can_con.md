---
title: "Cannot connect to my wireless network (but can connect to other networks)"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by MDguy on 2010-12-25
I am running Ubuntu (dual booting with Vista) on a Lenovo Thinkpad r-51 with a Tenda W311U wireless adapter.  My computer's wireless in Ubuntu was okay just a few days ago, but all of a sudden, whenever I try to connect to my network (WPA2 secured), it will ask me for the password again and again. However, Ubuntu will still allow me to connect to unsecured networks.  Vista will connect to my network fine with the same network card.

Here are my settings:
```
---Wireless--
SSID:<My network SSID>
Mode:Infrastructure
BSSID:<blank>
Device MAC address:<blank>
Cloned MAC address:<blank>
MTU:automatic
--Wireless Security--
Security: WPA & WPA2 Personal
Password:<my WPA key>
--IPv4 Settings--
Method: Automatic (DHCP)
--IPv6 Settings--
Method: Ignore
```Thanks for help in advance!

---

### Post by MDguy on 2010-12-27
I installed wicd and removed network manager, but wicd gives me this error message:
```
Connection failed: Bad Password
```even though I am sure I typed the key correctly.

---

### Post by Boondoklife on 2010-12-27
Try changing your password and trying again.

---

### Post by Boondoklife on 2010-12-27
Dupe post

---

### Post by MDguy on 2010-12-27
I changed the security to from WPA to WEP, and now it works again.  It appears that Ubuntu has some problems handling WPA security.

---

### Post by Boondoklife on 2010-12-27
Nah, it handles WPA and WPA2 just fine! I have it on 3 pc's and two routers.

Try to make sure your cards are wpa2 personal capable and use AES encryption

---

