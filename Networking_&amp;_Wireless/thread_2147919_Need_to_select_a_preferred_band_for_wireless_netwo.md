---
title: "Need to select a preferred band for wireless network"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by ZTiger on 2013-05-23
In our corporate work environment we have many wireless access points and several bands. The 5 Ghz band has the least interference and I would like to set that as my preferred band (an option that can be done on Windows, not sure about Mac). 

Due to the density of Access points and the fact that most share the same SSID I also have a lot of access point jumping. I'm told the windows system get around this issue by preferring the 5Ghz band.

How can I configure my wireless to prefer the 5Ghz band with the ubuntu network manager? 


= Relevant Specs =
OS: Ubuntu 13.04
Wireless: Intel Centrino Ultimate-N 6300

---

### Post by praseodym on 2013-05-23
Hi,

you can add the MAC-addresses of the selected APs in the field "BSSID" in the network-manager applet. Check
```

sudo iwlist scan
```

---

### Post by ZTiger on 2013-05-24
@praseodym

Still no dice. I should add that authentication is needed to the network

IT requires WPA2-Enterprise encryption using PEAP authentication. I did not have wpa_supplicant installed. 

I will try to get it to connect manually, however I'm curios if this is something that should theoretically work using Ubuntu's "Network Manager"?

---

### Post by praseodym on 2013-05-24
You need the certificate for WPA2-Enterprise.

---

