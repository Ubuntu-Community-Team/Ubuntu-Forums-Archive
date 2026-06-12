---
title: "extension &quot;ATIFGLRXDRI&quot; missing on display error"
date: 2009-09-07
forum: Multimedia Software
---

### Post by adamb24 on 2009-09-07
Hi, I recently switched back to ubuntu when 9.04 came out, and and having trouble getting the opengl installed. I have an ati radeon 512 x1650 card, and originally when the driver was installed fglrxinfo said mesa was installed for direct rendering. Now i downloaded the newest driver, 9.8 from the ati site and installed it manually through the terminal. And when i ran fglrxinfo it gave me this error message

 extension "ATIFGLRXDRI" missing on display ":0.0".
Segmentation fault 

Anyone know how to fix this? Keep in mind I havent rebooted the computer yet as I'm a little unsure about how to proceed. Any help is appreciated.

ok, so I rebooted my computer and now i get this error

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

If anyone can tell me whats going on i'd appreciate it.

---

### Post by adamb24 on 2009-09-07
bump

---

### Post by pme 72 on 2009-09-08
Someone correct me if I am wrong but I believe your card is only supported by the free drivers in 9.04. Hardy Heron 8.04 and Intrepid Ibex 8.10 both have support for proprietary drivers for your card if you need them. 

[https://help.ubuntu.com/community/RadeonDriver:](https://help.ubuntu.com/community/RadeonDriver:)
    
    "It is important to note that with the release of 9.04, the fglrx driver dropped support for the r500 line of cards. If you are upgrading from 8.10 or a previous release and use one of these cards, it is strongly suggested that you remove fglrx prior to upgrading to avoid any problems. However, you can still remove the fglrx driver after the upgrade if it causes problems."

Development of the free driver is an on going process. You can follow the progress here: 

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

