---
title: "Modeswitch for the Huawei E5830"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-02-28
I struggle with the Huawei E5830 and usb_modeswitch - actually I am not  sure whether I struggle more with the Huawei device or modeswitch. 
 
What I found out so far: 
Under Linux the device has (before modeswitch) the vendor id 12d1 and  the product id 1446. 
 
Under Windows the device has (after it is recognized as UMTS modem) the  vendor id 12d1 and the product id 1401 
 
 
I tried the following command for modeswitch in Linux: 
'usb_modeswitch -v 0x12d1 -p 0x1446 -V 0x 12d1 -P 0x1401' 
 
modeswitch gives me the following result: 
'Looking for target devices ... 
  Found devices in target mode or class (1) 
Looking for default devices ... 
  No default device found. Is it connected? Bye.' 
 
What am I doing wrong and does anybody have any suggestions. Do I need  additional information for the Huawei E5830 and how can I get the  information? Or am I using usb_modeswitch the wrong way? 
 
 
I also tried to use the 'usb_modeswitch.conf' file as following: 
 
######################################## 
# Huawei E5830 
 
DefaultVendor= 0x12d1 
DefaultProduct= 0x1446 
 
TargetVendor= 0x12d1 
TargetProduct= 0x1401 
 
 
Still no success. I think some parameter is missing and I do not know  how to identify it. 
 
 Any hint that could help me is welcome. Thank you in advance 
 
Sven

---

### Post by iponeverything on 2010-02-28
With my UMTS device, I just right click on device and "eject", then it shows up in network manager..

(under 9.10)

---

### Post by Sven6210 on 2010-03-01
What is your UMTS device? It's not the E5380.

I also found out that the E5380 changes the mode automatically. When connecting with the computer it first has the ids 12d1:1446, after it is switched on and logged to the network it automatically has the ids 12d1:1401. Therefore usb_modeswitch is not necessary.

---

### Post by iponeverything on 2010-03-02
Mine is a ZTE MF626.

---

### Post by pdc on 2010-03-03
so we are not talking about this device are we?

[http://cgi.ebay.com.au/Unlocked-HUAWEI-E5830-MiFi-WiFi-Wireless-Modem-E6939_W0QQitemZ180475854568QQcmdZViewItemQQptZAU_Modems?hash=item2a0532fee8](http://cgi.ebay.com.au/Unlocked-HUAWEI-E5830-MiFi-WiFi-Wireless-Modem-E6939_W0QQitemZ180475854568QQcmdZViewItemQQptZAU_Modems?hash=item2a0532fee8)

THe Huawei E5830 modem that is called MiFi-WiFi;

---

### Post by Sven6210 on 2010-03-04
Yes, pdc, we are talking about the E5830 as shown on ebay. In my last post I wrong way, the way it is written in the headline is right.

---

