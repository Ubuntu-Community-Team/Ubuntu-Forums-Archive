---
title: "Modem – Router interconnect problem"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by grr51 on 2010-12-22
Hi,
 
 Although this is not directly related to Ubuntu, somebody may have encountered the same problem and might be able to help.

 I have been unsuccessfully trying for some time to add a wireless Router to a friend existing ADSL Internet connection.   
 
 Modem:
 - Thomson Speedtouch ST516
 - S/W release: 6.2.29.2
 
 The Modem is configured as follows:
 - Mode: Bridge
 - VPI/VCI = 0.35
 - DHCP = Disabled
 
  The added Router is the following:
 - Linksys WRT120N
 - Firmware: 1.0.05, build 3, Sept 3, 2010
 
 When the Router is added (still only in wired connection) with all the required login credentials, it is not possible to connect to the Internet, although all the LEDs of the Modem and Router show normal conditions!
 
 I power cycled everything in different order without success.
 
 I brought the Router to my home, changed the login credentials, connected it to my Modem, a SpeedStream 5360, and everything worked flawlessly.
 
I am really baffled and needs some advice before giving up for good.
 
 Thanks.

---

### Post by grr51 on 2010-12-25
The problem was solved by enabling DHCP on the Modem, although this is contrary to all the recommendations I have seen on various posts regarding Modem bridge mode configuration.

---

