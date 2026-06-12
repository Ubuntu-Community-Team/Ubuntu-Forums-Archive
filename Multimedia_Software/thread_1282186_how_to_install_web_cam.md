---
title: "how to install web cam"
date: 2009-10-04
forum: Multimedia Software
---

### Post by venkat_kannappa on 2009-10-04
i am having creative web cam the output of lsusb is follows

cabin7@cabin7-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4064 Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


i am unable to install this web cam ? how to install it ? 

kannappan

---

### Post by ad_267 on 2009-10-04
Have you tried to use it with an application like Cheese? You shouldn't need to install any drivers, if it's supported it will just work.

There's a list of supported creative webcams here: [http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx)

Your model has approval listed as "pending", I'm not sure what that means. You might need to follow the instructions here to compile the kernel module: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)

---

