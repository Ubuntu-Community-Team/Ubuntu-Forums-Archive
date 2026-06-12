---
title: "How to deactivate wlan card?"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by amir1981 on 2010-08-10
Hi,
I have bought a new laptop with win7 on it , I delete  win7 and install ubuntu64  everything is ok  but  my wireless card won't work ( it is recognized) and even I can connect to INTERNET but  nothing is download or upload so I have bought another  usb wireless card   but  now  when I  connect this new  card to my laptop it still tries to use the old one  and so  I could not connect to internet,  how can I  deactive the  old one  so my computer  just  see the new wireless card?

tnx

---

### Post by marc.verwerft on 2010-08-10
1. you can connect to the internet but cannot download or upload? Very strange - because 'browsing' is downloading html pages - I don't think your card is the problem.
Try to use the commandline (wget, ftp, curl, ...) to doublecheck. If anything goes wrong they will typically spit out more info then what you get from a browser.
2. linux is perfectly capable of using more then one card at the same time - no need to disable one. I don't know how two wireless cards are handled in the gui (network manager and such) but I'm quite sure that by correctly using iwconfig you can connect to the internet using your alternative card. Try 'man iwconfig'

Regards,

Marc

---

### Post by amir1981 on 2010-08-10
> - because 'browsing' is downloading html pages
No Actually I  mean  it shows that I'm connected but I  could not  browse download or  upload or anything else

---

### Post by Iowan on 2010-08-10
> **amir1981 said:**
>  ... how can I  deactive the  old one  so my computer  just  see the new wireless card?
First place to check would be the BIOS.

---

### Post by marc.verwerft on 2010-08-11
Maybe you can start here: [https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)

Other places that can help you:
- [http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html](http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html)
- [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Regards,

Marc

---

