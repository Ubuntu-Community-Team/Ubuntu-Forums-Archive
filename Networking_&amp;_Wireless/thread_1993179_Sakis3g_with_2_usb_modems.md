---
title: "Sakis3g with 2 usb modems"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by dicecode on 2012-06-01
Hello,

Has anyone tried using 2 USB 3G modems for redundancy? Currently I am running using 1 device and sakis3g is handling my 3g connection. 

(I am using the Command Line option - 
sakis3g  connect --nostorage --pppd APN="myprovider01APN" APN_USER="username" APN_PASS="password" USBINTERFACE="0" USBDRIVER="option" OTHER="USBMODEM" USBMODEM="12d1:1436" )

Now I have another USB modem from another provider (but using the same USB Modem model). How can I specify the second command line option? - the only difference is the BUS ID from the lsusb output)

Tried specifying ttyUSB ports but it keeps on changing. I know that plugging in one at a time solves the problem but curious if it's even possible to have both plugged in and one will autoconnect if the other fails (got the script covered) - stuck on the sakis3g part.


Bus 002 Device 005: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 001 Device 005: ID 12d1:140c Huawei Technologies Co., Ltd. 

Appreciate if anyone has any experience to share on this.

Thank you

---

