---
title: "Linksys wireless problems"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by jsweeny on 2009-07-03
I just installed the latest version of Ubuntu.  My usb wireless adapter finds my router but I am not able to connect to it.  It is a linksys wusb54gsc.  Can anyone help me?

---

### Post by Boondoklife on 2009-07-03
Do you get an error when you try to connect? Can you give a little more information?

---

### Post by superprash2003 on 2009-07-04
post output of
1)iwconfig
2)sudo iwlist scanning

---

### Post by jsweeny on 2009-07-04
I think that the problem might be with my router.  Ubuntu asks me for a password and even though I know my password for my router it wont accept it.  Any ideas.  Maybe this is a linksys problem not an ubuntu one.

---

### Post by Boondoklife on 2009-07-04
Tried connecting to it with a wire and resetting the WEP/WPA password

---

### Post by jsweeny on 2009-07-04
I needed the wpa shared key in order to connect to the router.  If anyone else is having problems with this go to the router ip address, 192.168.1.1 put in your username a password or just type "admin" in the password field.  Then click on wireless tab and the sub tab wireless security.  The encryption/password you need to access it is the WPA shared key.  It is a alpha numeric and is case sensative.  Good luck.

---

