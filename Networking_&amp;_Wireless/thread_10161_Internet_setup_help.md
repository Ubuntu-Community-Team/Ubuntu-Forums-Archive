---
title: "Internet setup help"
date: 2005-01-05
forum: Networking &amp; Wireless
---

### Post by bulio on 2005-01-05
Hi everyone,

I recently got my ubuntu cds in the mail, and I was wondering how to setup ubuntu live for dsl internet. I have a dsl modem wich connects to my pc using pppoe internet authentication. The setup is like this:

Computer-Usb cable-->Modem-->Phone Jack

The modem is an efficient networks speedstream 5200 usb/ethernet modem. Since I don't have an ethernet port, I use usb to connect my modem to the pc. I did a command sudo lsusb and it did recognize the modem as a device, but I don't htink as a modem. How can I set it up so it will work on the internet?

Thanks

---

### Post by tiiim on 2005-01-05
[QUOTE=bulio]Hi everyone,

I recently got my ubuntu cds in the mail, and I was wondering how to setup ubuntu live for dsl internet. I have a dsl modem wich connects to my pc using pppoe internet authentication. The setup is like this:

Computer-Usb cable-->Modem-->Phone Jack

The modem is an efficient networks speedstream 5200 usb/ethernet modem. Since I don't have an ethernet port, I use usb to connect my modem to the pc. I did a command sudo lsusb and it did recognize the modem as a device, but I don't htink as a modem. How can I set it up so it will work on the internet?

Thanks[/QUOTE]
 i dont know if ur modem is supported it maybe try googling for drivers.... usb modems are annoying if you had ethernet it would be way easier.... if you cant find drivers you may have to purchase and comptable modem which there is comptable usb modems out there

---

### Post by hardcandy on 2005-01-05
To start you will need to have the usbnet module loaded. Let's hope it is enabled by default. Just to make sure, do a "sudo modprobe usbnet" and if you do not see any error messages it should load, or you get a message it is already loaded which is even better. 
Then unplug it and replug it and wait a minute and see if you can access anything using a web browser and the modem address. "http://192.168.254.254/" is the modem set up address. 
Hopefully this will work, if no usbnet module present, maybe look around and see if a package is available. 
If not luck with getting the modem and linux to work with a straight connection, there are usb-ethernet adapters available (so you could connect to the modem via ethernet cable)which work with linux. [http://www.linux-usb.org/](http://www.linux-usb.org/)  (look in the ethernet section)

---

### Post by hardcandy on 2005-01-05
And I found this, a firmware upgrade for certain serial numbers of that modem which will upgrade it to a router, so you could connect several computers, pdas, etc  to it. 

[http://www.hardwaresecrets.com/article.php?cat=modem&id=84&pagenumber=1](http://www.hardwaresecrets.com/article.php?cat=modem&id=84&pagenumber=1)

---

