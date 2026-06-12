---
title: "Solution for the problem for frequent disconnection of USB modem"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by p1977p on 2012-10-14
I, like many others here,  have had problems using my Huawei USB 3G  modem. I am able to connect and surf, but for some unknown reason, the  modem disconnects after a variable period of time and the connection  disappears from the NetworkManager menu.

After much head banging, I finally seem to have found a way to have  continuous net access  without reinserting the modem. Kindly follow the  steps below:

1)  Install usb_modeswitch if not already installed.

2) run  ```
usb-devices
``` in terminal. you should get a output showing something like this:

```
$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:0b.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1436 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=cdc_ether
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 8
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:0b.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```Note that interface number 2 is data interface for my modem. Also  note vendor code 12d1 and product ID 1436 for my modem. (these may  differ in your case)

3) Now try resetting the mode by typing ```
sudo usb_modeswitch -v  YOUR_V_VALUE  -p YOUR_P_VALUE  -s 2 -R
``` in terminal. You should see something like  this:
```

 $ sudo usb_modeswitch -v 12d1 -p 1436  -s 2 -R

Note: target parameter missing; success check limited
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 007 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
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
 OK, device was reset

Checking for mode switch (max. 2 times, once per second) ...
 (For a better success check provide target IDs or class)
 Original device vanished after switching

Mode switch most likely succeeded. Bye.
```Now the Mobile Broadband  Connection should show up in Networkmanager applet in taskbar. Click to  connect. Happy surfing!

If this works well,  you can automatically do it by downloading and  running the following script (keepalive.sh) in a terminal with sudo  ```
$ sudo ./keepalive.sh  
```You have to edit it first and  change the -v -p options. This script checks every 45 sec for the online  status, so it might take a minute to get reconnected, but it works well  for me. It also prints a message every time it reconnects. Keep the terminal window minimsed till you are online. Stop the script by pressing Ctrl-C in the same terminal window. Yesterday  night I updated my Xubuntu system with this modem ( it reconnected  itself 12 times! )

Could a moderator please mark this thread sticky for the benefit of others in distress?

---

### Post by desconocido on 2013-01-08
> usb-devices

I'm running Karmic and I don't seem to have that command. Is it new?

---

### Post by p1977p on 2013-01-12
> **desconocido said:**
> I'm running Karmic and I don't seem to have that command. Is it new?

It is actually a script that parses the /usb/devices file and lists only the connected devices. It is a part of the *usbutils* package , or you can list the entire /usb/devices file at  **/sys/kernel/debug/usb/devices** or at **/proc/bus/usb/devices**.

---

### Post by desconocido on 2013-01-14
> **p1977p said:**
> It [usb-devices] is actually a script that parses the /usb/devices file and lists only the connected devices. It is a part of the *usbutils* package , or you can list the entire /usb/devices file at  **/sys/kernel/debug/usb/devices** or at **/proc/bus/usb/devices**.

On Karmic, I seem to have version 0.82 of *usbutils* already installed.
**/sys/kernel/debug/usb/devices** is an empty file and **/proc/bus/usb/devices** doesn't exist.

Perhaps I need to get a new version from Debian?

---

