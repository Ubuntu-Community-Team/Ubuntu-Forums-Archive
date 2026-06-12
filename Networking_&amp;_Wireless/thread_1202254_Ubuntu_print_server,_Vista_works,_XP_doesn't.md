---
title: "Ubuntu print server, Vista works, XP doesn't"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by xtraspecialj on 2009-07-02
Ok, I have Samba installed and working on my Ubuntu 8.10 machine.  I have my HP PSC1510 printer installed onto the Ubuntu machine.  It works fine there and can be seen and printed to by my Vista laptop.   When adding the printer to my Windows XP desktop, I type the address to my printer in, it sees it, but says the print server doesn't have the correct drivers installed and offers me to search through a list.   The closest printer it has listed is a HP PSC950.  (Same thing happened when I installed it on the Vista machine, but the Vista's list had the PSC1510 listed, so I chose that and it worked fine)   I tried installing the PSC950 driver but it just prints garbage.  Is there any way I can get the correct driver loaded onto the Ubuntu machine so that when I add the printer in Windows XP, it automatically just finds the right driver and installs it?  I have tried manually adding the driver in on the XP machine, but I can't get that to work because HP's stupid driver insists on the Windows machine and the Printer be communicating before it will install the driver.  Stupid HP!!  If they were working together, I would'nt have to be installing the stupid driver manually!!!

---

### Post by superprash2003 on 2009-07-02
yea , i faced the same issue.. so i plugged in the printer directly to the xp machine and then installed the drivers that way , then unplugged it and put it back to the ubuntu machine , this time when i had to connect to the printer via the network i had the option of using the driver which got installed when the printer was connected via usb to the xp

---

### Post by dmizer on 2009-07-02
Just use the driver disk for the printer. Instead of letting XP search for the driver, use the "have disk" option. If you don't have the driver disk, you can download the driver here: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=mp-35363-1&lc=en&dlc=en&cc=us&product=428800&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=mp-35363-1&lc=en&dlc=en&cc=us&product=428800&os=228&lang=en)

---

### Post by superprash2003 on 2009-07-03
their drivers are in .exe format , so you cant use the have disk option for that.. as have disk option looks for .inf files

---

