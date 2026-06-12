---
title: "Recognized wireless but not connect"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by panuque on 2012-03-02
I have a Belkin Wireless USB adapter. In Windows 7 I had no problems to detect the hardware. Yesterday I installed Ubuntu 11.10 and I put the USB; detects the network but when trying to connect Ubuntu ask me for the password, I put it on, and he tries a few minutes trying to connect. After those few minutes Ubuntu again ask for the password, and so eternally. 

I do not know if it can be by type of security issue of the router (WPA) or USB driver, although I doubt the latter because otherwise I would not have detected the networks. I tried to install the driver with the **ndsiwrapper **but nothing. I did a **lsusb **and shows me the Belkin.

Thanks!

---

### Post by panuque on 2012-03-02
should i install WICD?

---

### Post by Mike235 on 2012-04-02
I have the same problem with a wireless pci adapter on my desktop. Works fine on windows, and ubuntu 11.10 recognizes the device but i get the same thing. Keeps trying to connect and asking for the password.

Would really like some help on this. Tia!

---

### Post by wave979 on 2012-04-11
Hi guys I have the same problem running Ubuntu 10.10. I'm using Belkin's G wireless usb network adapter FCC: ID K7SFSD7050A

My available networks show up, but after I put the correct password I does not connect. "Unable to connect to network"

As the other member said. I ran a lsusb command and the usb adapter shows up, so I believe is not a driver issue? I may be wrong please help

---

### Post by bogan on 2012-04-12
Hi!, **Mike979**, your problem is with a PCI card, the others on this thread are using a USB Adapter; please start your own Thread and Post the output of: ```
 lspci -nnk | grep -e net -e Net 
``` Chao!

@**wave979** &** panuqu**e,

Please  Post the output of: ```
 lsusb -v | grep -e net -e Net 
``` Chao!, **bogan**.

---

