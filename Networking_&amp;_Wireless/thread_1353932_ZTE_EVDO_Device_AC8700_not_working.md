---
title: "ZTE EVDO Device AC8700 not working"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by filmyguy on 2009-12-13
I subscribe to BSNL's EVDO data card service in India. The device model is ZTE AC8700. How does one get it working in ubuntu. It runs beautifully in Windows XP. Any tips on installing the driver etc.?

---

### Post by gs777 on 2009-12-13
hey filmyguy
Assuming you are using Gnome desktop , I would suggest you to look in the gnome network applet. click on it and amenu will come out.Can you see the name of your EVDO card here ? If yes , then your card is detected and if no then Run the following command 
"lsusb" 
then post your results here

---

### Post by tannakartikey on 2010-02-02
**I have also same problem and here is the output of 'lsusb'**



Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 05c6:6000 Qualcomm, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 147e:1000 Upek 
Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 17ef:4808 Lenovo 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by pdc on 2010-02-02
you have double-posted;

see your other post

[http://ubuntuforums.org/showthread.php?p=8764481#post8764481](http://ubuntuforums.org/showthread.php?p=8764481#post8764481)

perhaps you don't go on using this thread?

---

