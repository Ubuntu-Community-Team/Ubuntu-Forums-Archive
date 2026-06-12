---
title: "Ubuntu thinks my internet modem is a cd"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by solbjorn on 2012-12-08
Hej, 
i would like to change my internet modem. The one I have now (Telekom Austria) is working perfect, and was recognized all the time as an usb stick. 
If i plugg the new one (telering) ubunut thinks i just inserted a cd!! 
i tried with mounting the device manually but it didn't work out. so i reallly need your help!! 

Thanks in advance

---

### Post by lemming465 on 2012-12-22
What version of Ubuntu are you running?
Could you be more specific about the vendor and model of the new modem?
Is it a PCI device or a USB device or what?
Could you attach the output of```
sudo lspci -v
sudo lsusb -v
```
with the device connected?

We need more information before we can provide useful advice.

---

