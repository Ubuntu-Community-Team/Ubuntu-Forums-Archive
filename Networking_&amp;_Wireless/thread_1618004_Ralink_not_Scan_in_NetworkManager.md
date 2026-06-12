---
title: "Ralink not Scan in NetworkManager"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by VeNoMZiTo on 2010-11-10
Hi,

I have Ralink (usb device) with RT3370sta module working. For example if a put in bash: #iwlist ra0 scan, i get 2 networks, but in NetworkManager nothing. When I compiled I changed:

# Support wpa_supplicant
HAS_WPA_SUPPLICANT = y

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

But NetworkManager don't work. There is anyway to do NetworkManager work?

Thank You and sorry for my english!.

---

### Post by uncaspi on 2010-11-10
What did you compile?

---

### Post by VeNoMZiTo on 2010-11-10
I compile this: RT8070/RT3070USB(RT307x) from [www.ralinktech.com](www.ralinktech.com). and setting "y" the two options for NetworkManager

#iwlist ra0 scan -> Works
NetworkManager -> No

Thanks!

---

### Post by uncaspi on 2010-11-10
See this thread

[http://ubuntuforums.org/archive/index.php/t-837548.html](http://ubuntuforums.org/archive/index.php/t-837548.html)

---

### Post by VeNoMZiTo on 2010-11-10
Uncaspi thanks, my problem is only with NetworkManager. My Ralink works perfect with iwconfig but not with NetworkManager. And module was compiled with Wpa Suplicant for NetworkManager.

---

