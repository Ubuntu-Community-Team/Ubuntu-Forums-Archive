---
title: "Help Configuring Wireless network"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by AMcCann on 2009-10-16
I recently got my wireless card drivers installed using ndisgtk. The wireless card is installed but i need help configuring it. 
Ive pretty much ONLY gotten the drivers install. I went to network configure, and tried automatic config. Im not even sure where to select which wireless signal to use.
Im new to ubuntu please help.

---

### Post by hooliox79 on 2009-10-16
if you already tried karmic koala or version 9.04, you may want to check this LINK  [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

wicd will help you solve the problem in no time

if you're still on version 8.04 try ndiswrapper
1. put your UBUNTU cd on the cd-rom unit
2. go to system> administration> synaptic package manager
3. go to the menu Edit>Add CD-ROM
4. click on the right (over the list of packages)
5. write ndiswrapper and mark for installation 
  ndisgtk, ndiswrapper-common, ndiswrapper-utils
6. apply button
7. exit the synaptic p. m.> go back to System>Adminstration>Windows Driver  (you should see it at the bottom) it will allow you to install a new driver, be sure to have the driver... :)

---

### Post by hooliox79 on 2009-10-16
There should be an icon on the panel by the Date(ON IT'S LEFT), click it and it will show you if there is any available network

---

### Post by hal10000 on 2009-10-16
It could help if you post more information about your wireless card (model, chipset, usb or pci etc.)

---

