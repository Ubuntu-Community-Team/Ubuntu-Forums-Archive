---
title: "where is prisim2_usb????"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by polishemokid on 2006-05-09
I am new to linux, and i cant get my MA111 to read, i have heard about using some prisim2_usb where do i find this? and how do i install or use this? thanx

---

### Post by jml on 2006-05-09
A few questions first.  Can you see the usb adaptor when you open the network management application?  If it is listed, then highlight it, click on properties and configure the settings.  Close out then click on activate. After several minutes the process will finish.  Close out the network manager and you should be able to connect.  Be sure to set things up initially with an unencrpted network.  Once that is working, try to configure WEP encryption if needed.  Ubuntu does not support WPA encryption.

If it is not listed, then you will need to use the Widows driver included on the installation CD.  You will need to use ndiswrapper to use it.  Here is a link to the wireless troubleshooting guide to help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Hope this helps.

Joe

---

### Post by polishemokid on 2006-05-10
no it doesnt show at all

---

### Post by az on 2006-05-10
[https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111](https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111)

---

