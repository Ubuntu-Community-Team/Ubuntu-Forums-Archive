---
title: "Connecting my Starcomms (Epi Valley) modem to Internet"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by aspyre on 2010-04-22
Please i need guidance on how to connect my modem to the Internet, the help file on my Ubuntu 9.10 does not match the features available. I am using a modem from Starcomms (a local CDMA services provider in Nigeria) made by Epi Valley. Help, please.

---

### Post by alexfish on 2010-04-22
Hi aspyre
 

   I need further info as regards the type of modem you are using
 

 Is it a USB or Serial connection
 

 Have you registered or configured the modem with windows , with some ISP's this may be necessary
 

  Do you have details of  type of the modem , IE Huawie or ZTE etc + the model number
 

 Mean time , below is what you can do to see if it will configure in ubuntu , this will also include the use of the Terminal if the device is not recognized by the network manager , if you are a novice the Terminal is available from the Applications / Accessories .
 

 
[LIST=1]
[*]Boot up the computer without the     device
[*]Give the time for the computer to     settle . Then connect  the device
[*]Allow the device to settle ,     Notice if there is a device or file etc  appears on the desktop
[*]check to see if the Network     Manager in the top right panel  has recognized the device it may     show make new connection or similar , if so click on it to start the     wizard , follow the wizard, check with your provider for details not     provided by the wizard
[*]if  the device etc has shown     on the desktop right click with the mouse and from the mouse menu     eject or safely remove the device, allow time to settle ,check the     network manager again , go back to 4
[*]Device not recognized , this is     where we need the terminal . Open up the terminal and type or copy     these two commands in the terminal and post the results
[/LIST]
 

   if usb
   
  Code:
 

 lsusb
 

 this will show the ID's of the device
 

 for all devices
 

 Code
 

 dmesg | grep -e "modem" -e "tty"  
 

 this will show the modem and the tty lines it is on
 

  the above ID's returned by the lsusb command  may indicate if modem is only been recognized as a mass storage device or the modem its self, so maybe usb modeswitch may switch the device to modem mode. But follow the above first
 

 regards
 

 alexfish

---

### Post by djynnius on 2010-06-09
I am having issues cant get my debian to see the modem as a modem. I dont know where to start from.

---

### Post by djynnius on 2010-06-11
finally fixed my Epivalley Starcomms USB Modem issues on debian! All I rquired was 
1. the newest version of usb-modswitch which would only install after i installed libusb, 
2. then usb-modswitch_data

then my debian began seeing the USB as a modem but I had a new issue couldnt connect even after entering my username (0702xxxxxxx@starcomms.com) and password (07028xxxxxx) correctly I circumvented this by installing wvdial

Note if u already had it installed it might not work so you have to force a reinstall

# wvdial --reinstall install wvdial

then open etc/wvdial.conf and edit 
 so you have number as #777
 password as 0702xxxxxxx
 username as [email]0702xxxxxxx@starcomms.com[/email]

and run wvdial

thats it!

---

### Post by ogfx on 2011-05-28
@djynnius: Thanks for all d help...please how do I install these packages when my ubuntu dosen't browse using my izap modem??

---

