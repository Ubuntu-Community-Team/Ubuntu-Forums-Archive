---
title: "Mobile Broadband Connection Disconnects &amp; Disappears from Network Manager"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by hopeididgood on 2011-06-30
In the past couple of days I've been having an issue with my mobile broadband connection.  It disconnects and then the connection disappears from the Network Manager menu.  (To be clear, if I go to "Edit Connections" the connection is still listed there -- it just doesn't appear as an option to connect to -- like the device isn't inserted into the computer.)

When this occurs, the device still shows up as Mass Storage in Computer, but it's as the modem isn't on or getting power.  The only way I can get the modem to appear back in the Network Manager is to shut everything down and restart.

Is there anyway to prevent this from happening?
Is there anyway to get the computer to find the modem part of the device when this happens -- without having to restart?  
Is this simply a matter that the modem is four or five years old and wearing out?  

I have a Dell XPS M1530 with Ubuntu 10.04.  The usb device is a UTStarcom UM150.  

If there is info that you need posted to answer this question just let me know -- though I'll need you to walk me through it.  Despite using Ubuntu for a couple years now, I still feel like a complete newbie.  

Thank you for any assistance you can provide.

---

### Post by Skyo on 2011-12-21
Same problem here - bump.
Im am using Ubuntu 10.04 and my UMTS modem [XS Stick W14] disconnects and dissappears from the panel.
Restarting is not an option.... (but works for me).

---

### Post by big10 on 2011-12-21
Same here - and it wont detect it again unless restarted. I am facing similar issue with WIFI as thats more urgent to me. below is the link.

[http://ubuntuforums.org/showthread.php?t=1897318](http://ubuntuforums.org/showthread.php?t=1897318)

---

### Post by p1977p on 2012-07-01
Solved the problem without reinserting the modem. follow the steps below:

1)  Install usb_modeswitch if not already installed.

2) run 'usb-devices' in terminal. you should get a output showing something like this:

> T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1436 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


Note that interface number 2 is data interface. Also note vendor code 12d1 and product ID 1436 for your modem. (these may differ)

3) run ```
sudo usb_modeswitch -v 12d1 -p 1436 -i 2 -R
``` in terminal
you should get something like this:> 
 $ sudo usb_modeswitch -v 12d1 -p 1436 -i 2 -R

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x02
Using endpoints 0x01 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Warning: no switching method given.
Resetting usb device .
 OK, device was resetNow it should show up in Networkmanager applet in taskbar. Click to connect.

---

### Post by Dr4k1 on 2013-05-23
What if I don't have data interface when run 'usb-devices', but my mobile brand working a couple of hours and then disconnect and disappear?

> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0017 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF6670VIPD010000
C:  #Ifs= 5 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


---

