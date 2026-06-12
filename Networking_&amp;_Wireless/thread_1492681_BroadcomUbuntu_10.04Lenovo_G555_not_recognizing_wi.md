---
title: "Broadcom/Ubuntu 10.04/Lenovo G555 not recognizing wireless connections"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by fordguydude on 2010-05-25
I just bought a new Lenovo G555 laptop and immediately installed ubuntu. According to the reviews on Newegg, this laptop works great with Ubuntu 10. 

Now that I'm on it, I cannot connect to a wireless network. Here are my details. 

Wireless Brand
```
Network controller: Broadcom Corporation Device 4727 (rev 01)
```

Interface
iwconfig says

```
lo             No wireless extensions

eth0                 No wireless connections
```

Modules
```
A lot.  
```  

I'll post if you need anything. I'm writing this all down on a different computer. 

Network Configuration
```
network UNCLAIMED
description: Network controller
product: Broadcom Corporation
vendor: Broadcom
physical id: 0
bus info: pci@0000:08:00.0
version: 01
width: 64 bits
clock: 33mhz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources memory:d1100000-d1103fff

```
There is A LOT more code that I can write down, let me know if you need anything else. 


Thanks for any help. I can't wait till I can finally use this wirelessly. My ubuntu desktop is great!

---

### Post by pdc on 2010-05-25
[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

here is a diagnostic wireless script; it is looked after by a linux specialist;download it; run it; it is safe;

read what it gives you: it will give advice; for further help, post the results back here

---

### Post by bkratz on 2010-05-25
There is a lot of useful info here

[http://www.uluga.ubuntuforums.org/showthread.php?p=8992826](http://www.uluga.ubuntuforums.org/showthread.php?p=8992826)

---

### Post by fordguydude on 2010-05-25
Wow that was easy. All I had to do was activate the driver. 

Finally, I am once again Windows Free!!!!!!

thanks guys.

---

### Post by bkratz on 2010-05-25
> **fordguydude said:**
> Wow that was easy. All I had to do was activate the driver. 

Finally, I am once again Windows Free!!!!!!

thanks guys.

congratulations! glad it worked for you. Please go to the thread tools and mark it as solved in case it helps someone else.

---

### Post by elcaesar on 2012-11-16
Hi, this thread its old but equally'll bring.


I have a Lenovo G555 and I had the same problem on the wireless card Broadcom BCM series. I searched Google until I found this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Broadcom_BCM43xx_Chipset_.28PCI.29]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Broadcom_BCM43xx_Chipset_.28PCI.29")

Explaining how to install drivers for these cards.

I hope I have helped. Regards.

---

### Post by wildmanne39 on 2012-11-17
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

