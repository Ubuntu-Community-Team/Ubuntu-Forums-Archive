---
title: "Getting 2 different MAC addresses for same adapter"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by jfmanamtr on 2011-01-12
I am running a dual boot PC, Ubuntu 10.10 & Win7. I do sticky static IPs on my local network, but it doesn't work cause the Ethernet adapter gets a different MAC address in Windows 7 (EF:9F:E9:F7:F7:F7) than it shows for Ubuntu 10.10 (00:13:74:00:5C:38). I am not sure if this is a Windows problem or something up with Ubuntu. The card is an on-board Atheros L2 fast Ethernet adapter. I have tried updating the drivers in Windows & nothing is working. Any help or ideas would be greatly appreciated.

~JFM

---

### Post by Kirboosy on 2011-01-12
You should be able to edit /etc/network/interfaces file to make the changes accordingly.

I'm guessing Windows is using a spoofed MAC Address.

```
sudo gedit /etc/network/interfaces
```

---

### Post by karthick87 on 2011-01-12
Sorry for the interruption.What you mean by spoofed MAC address?

---

### Post by Kirboosy on 2011-01-12
> **karthick87 said:**
> Sorry for the interruption.What you mean by spoofed MAC address?

MAC addresses are like a physical number assigned to that piece of hardware. Almost like (in the United States) a Social Security Number. Its supposed to be unique and only belong to that one piece of hardware.

From a hacking standpoint you can tell the hardware to use a fake MAC address through software/configuration. There are many things you can do with this...

If a network has MAC Filtering on it you can spoof a "allowed MAC address" and connect anyways.

---

### Post by jfmanamtr on 2011-01-12
Ok. That  is what I was afraid of. I know that I can modify it in Ubuntu, but I would rather make Windows show the right MAC address. Any ideas on how to do this? 

~JFM

---

### Post by karthick87 on 2011-01-12
@Caboose885 Thank you :)[URL="http://ubuntuforums.org/member.php?u=900617"]
[/URL]

---

### Post by Kirboosy on 2011-01-12
> **jfmanamtr said:**
> Ok. That  is what I was afraid of. I know that I can modify it in Ubuntu, but I would rather make Windows show the right MAC address. Any ideas on how to do this? 

~JFM



[LIST]
[LIST]
[*]       Go       to Start->Settings->Control Panel and double click on Network and       Dial-up Connections.     
[*]       Right       click on the NIC you want to change the MAC address and click on       properties.     
[*]       Under       “General” tab, click on the “Configure” button     
[*]       Click       on “Advanced” tab     
[*]       Under       “Property section”, you should see an item called “Network       Address” or "Locally Administered Address", click on it.     
[*]       On       the right side, under “Value”, type in the New MAC address you want to       assign to your NIC.  Usually       this value is entered without the “-“ between the MAC address numbers.     
[*]       Goto       command prompt and type in “ipconfig /all” or “net config rdr” to       verify the changes.  If the       changes are not materialized, then use the second method.     
[*]       If       successful, reboot your system
[/LIST]
[/LIST]
An even easier way to fix it is to stop using Windows ;)

---

### Post by jfmanamtr on 2011-01-12
Awesome. That fixed the issue. Thanks. I would love to stop using Windows, but I need it for 2 things, my job (stupid proprietary software) & playing my video games (tried WINE & that doesn't seem to work). 

~John

---

### Post by Kirboosy on 2011-01-12
Make sure you are running the 1.3 version of WINE.

*```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```*

```
sudo apt-get  update
```Good luck.

Oh by the way please mark this thread as solved. :D

---

