---
title: "HUAWEI Mobile broadband E352 HSPA+ USB, ID 12d1:14fe"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by kornelis on 2011-09-21
Hi,  I risked buying a 3g usb modem stick from t-mobile, but the device seems unsupported. It's  Mobile broadband E352 HSPA+ USB,  lsusb gives the ID 12d1:14fe  

I had hoped to solve the problem through usb_switch, but no luck.   A lot of technical data I came up with is in my thread on the usb_switch forum: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=754](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=754)  

Please look at that thread to see what I already tried.   The modem never gets detected (tried wvdialconf as well), I tried old Huawei commands for usb_switch both manually and automatically, no effect that I could understand as positive. 

I'm about to give up, but if anybody here thinks I still have got a change to the get the modem working I'd like to know how. Thanks.     
Kornelis

---

### Post by kornelis on 2011-09-23
Solved by upgrading usb_modeswitch manually. The latest package (usb-modeswitch and usb-modeswitch-data) Ubuntu has is 1.1.7, but the latest version of the program is 1.1.9. Fetched and compiled the source and installed with checkinstall.

---

