---
title: "Huawei E1820 3G dongle not working with Ubuntu 12.04"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by arunb on 2013-05-24
Hi,

I have installed Ubuntu 12.04 (64 Bit) on my new Lenovo G580 laptop. I have updated the system and have managed to get all the hardware working, except for the Huawei E1820 3G dongle. 

here are the contents of lsusb...

> Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 011: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 5986:0294 Acer, Inc 

Strangely the dongle works perfectly in Ubuntu 9.10. After insertion of the dongle into the USB port, the mobile partner folder is also displayed and also the networkmanager shows the connection as mobile broadband..

But in 12.04 neither does the mobile partner icon appear or networkmanager appears to detect the hardware.

thanks
a

---

### Post by karthickraja on 2013-05-24
Hi, Arnub. I am too looking for a way around this one.
[TABLE]
[TR]
              [TD="class: postcell"]               
I have a USB datacard which worked well with the backtrack5r3  (Which is based on Ubuntu 10.04LTS ) but it is not getting detected in  Ubuntu 12.04LTS/13.04


The USB modem which I have been using will be first mounted as a  CD-ROM with the drivers for  windows version and the dial up script for  linux. 
 
So to get connected to the internet I will eject/unmount the CDROM first and then dial up the connection.

  
The actual problem here is the CDROM is not getting mounted on the Ubuntu 12.04 LTS/13.04.

You could try this method [http://ubuntuforums.org/showthread.php?t=2028061](http://ubuntuforums.org/showthread.php?t=2028061).

In my case the above method didn't work but a blog post helped me to connect to the internet. Here is the link [http://amit-mendapara.blogspot.in/2010/11/amazing-bsnl-3g.html](http://amit-mendapara.blogspot.in/2010/11/amazing-bsnl-3g.html)


But still I am desperately looking for a way to have the CDROM of the USB  datacard to be mounted in Ubuntu 13.04(which I am currently using)

Hope it helps for you.





[/TD]
[/TR]
[/TABLE]

---

### Post by arunb on 2013-05-24
its strange that the dongle works with an older version of Ubuntu (9.10, karmic) and not with the latest one.

---

### Post by praseodym on 2013-05-24
Hi,

12d1:1446 is the storage mode, install the package "usb-modeswitch"

12d1:1001/ 12d1:140c/ 12d1:1436/ 12d1:14ac are the modem modes.

---

### Post by axelsvag on 2013-05-25
I have exactly the same problem , the modem work with live Ubuntu 13.04  , but the real installation broke everything , and modeswitch is installed on Ubuntu 13.04 .....

---

### Post by axelsvag on 2013-05-25
I have exactly the same problem , the modem work with live Ubuntu 13.04  , but the real installation broke everything , and modeswitch is installed on Ubuntu 13.04 .....

---

### Post by praseodym on 2013-06-04
12d1:1446 is the storage mode. Please try
```

sudo usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'
```

---

