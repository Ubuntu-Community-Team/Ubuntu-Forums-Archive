---
title: "Can I use NAS for applications ?"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by oygle on 2013-06-02
Currently using Ubuntu 12.04. We need to drastically reduce our power usage, and at 180 Wh for computer, monitor, router and UPS, am very interested to consider using a NAS device, as some only consume 21 Wh. Therefore, can I do the following with a NAS ..

1. Boot to different drives, like from grub, as in addition to using Ubuntu, I have a HDD with win xp pro.

2. Use the NAS for applications. On the ubuntu desktop, run KMail, OpenOffice, KMyMoney, Filezilla, etc,etc. On the XP desktop, run MS Office products and MS Money and MS Works.

3. Be suitable as both a 'file server' and a 'desktop'. Some applications have high resource needs (CPU/ram). How powerful are the CPU's in a NAS device, as compared to a desktop computer ? How much RAM can you have ?

4. Use a printer and scanner, and other such devices, run off the NAS.

---

### Post by tgalati4 on 2013-06-02
Retail NAS boxes are similar to a cell phone:  low-power ARM processor.  So yes, you can run all of those services, but you won't get the performance that you are used to with a Desktop with an AMD or Intel processor.  There are low-power motherboards using Via chipsets or even the RaspberryPi prototyping board that you could run a flavor of linux to perform both NAS and desktop functions.

Most NAS boxes have just enough memory to run the NAS functions and not nearly enough to run any desktop environment.  You would be better off building your own low power server.  Search the web, there are a lot of blogs of folks building low power servers--then add a desktop environment, make it dual-boot if you need Windows.  To save power, get a kill-a-watt meter and start looking around your house.  You can often save enough power through other methods, that the PC will be in the noise level for typical residential power consumption.

Another strategy is to get rid of all the desktop computers and switch everything to laptops and set up one laptop or desktop to be a file/print server with external drives.  Use Wake-on-Lan to wake it up when needed from other machines.

---

