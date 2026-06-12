---
title: "Issues with Novatel Wireless CDMA (Verizon) and Ubuntu 12.04"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by ominub on 2012-05-07
We have a couple Verizon aircards at work that we can use on trips and what not. Last week I tried one on my HP Pavilion dv7 running Ubuntu 12.04 and I could not get Ubuntu to recognize it as a modem. I created a mobile broadband connection in network manager, on the first page where you can choose a device, it was grayed out and nothing showed. 

The Aricard is a Verizon PC770
Trade name: Merlin
Model: CC760
Qualcomm 3G CDMA

lsusb shows:
After some frustration I started up a win XP virtual machine and shared the usb device (its a pci card not usb dongle, just for clarification). I plugged in the device, windows recognized it and prompted me to install the Verizon software, VZAccess Manager. I did but the software did not find the device. ](*,)

I closed the VM and clicked the network manager on the task bar and what do I find? Mobile Broadband is enabled and my device is listed. I reopened the create a new connection and the device was listed in there too. I went through the prompts and it connected without a problem. Perfect, now it will work from now on... right? Nay. After reboot, suspend, hibernate, removal of device, etc... the device is gone and mobile broadband is not even on the networking drop down. 

What the heck? If i reopen the winxp VM, start the VZAccess Manager, and it comes right back. So I'm lost.

here is the output of 'usb-devices' BEFORE opening the Windows XP Virtual Machine
```

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1410 ProdID=5020 Rev=00.00
S:  Manufacturer=Novatel Wireless Inc.
S:  Product=Novatel Wireless CDMA 
S:  SerialNumber=############
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storag

```AFTER opening the VM
```

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1410 ProdID=6000 Rev=00.00
S:  Manufacturer=Novatel Wireless Inc.
S:  Product=Novatel Wireless CDMA 
S:  SerialNumber=############
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```lsusb BEFORE:
```
Bus 004 Device 006: ID 1410:5020 Novatel Wireless
```lsusb AFTER:
```
Bus 004 Device 007: ID 1410:6000 Novatel Wireless
```Any ideas? I tried to find a command to manually enable mobile broadband but couldn't find anything. I thought that enabling mobile broadband might switch the driver but who knows.

---

### Post by alexfish on 2012-05-08
try this

```
sudo gedit /etc/usb_modeswitch.d/1410:5020
```Add this code 
```
########################################################
# Novatel Wireless devices

DefaultVendor= 0x1410
DefaultProduct=0x5020

TargetVendor=  0x1410
TargetProduct= 0x6000

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

```Save and exit
replug device : see what happen : use the "usb-devices" command to see if drivers loading

---

### Post by ominub on 2012-05-08
the file doesn't already exist so there is an error when i try to save it. what should i save the file as? 

[FONT=monospace]1[/FONT]410:5020?

thanks for your help.

Edit:
the folder '40-usb_modeswitch.rules' didn't exist either. I created it, and saved the file as '1410:5020'. 'usb-devices' gave the same output. 

did i create the file correctly? thanks.

---

### Post by ominub on 2012-05-08
I tried manually running usb_modeswitch here is the output... must be doing something wrong.


```
michael@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 003 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 004 Device 003: ID 1410:5020 Novatel Wireless 
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90

michael@ubuntu:~$ usb_modeswitch -b 004 -v 1410 -p 5020 -V 1410 -P 6000

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 004 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x08 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

michael@ubuntu:~$ 

```

---

### Post by alexfish on 2012-05-08
hi

possible /causes

1. need to run usb-modeswitch as root "sudo usb_modeswitch "
2. the VM ware is grabbing the device : Re this used to be Kernel problem

have you tried root : yes/no

if have vmware try this command

```
sudo usb_modeswitch -v 0x1410 -p 0x5020 -M "5553424312345678000000000000061b000000020000000000000000000000"
```will then look further

to see if the file are in correct place try
```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/40-usb_modeswitch.rules/1410:5020
```also need to add rule at libs
```
sudo gedit lib/udev/rules.d/40-usb_modeswitch.rules
```add this line below (LABEL="modeswitch_rules_begin") ```
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5020", RUN+="usb_modeswitch '%b/%k'"
```

---

### Post by ominub on 2012-05-09
Okay, I ran usb_modeswitch as root
Output:
```
michael@ubuntu:~$ sudo usb_modeswitch -b 004 -v 1410 -p 5020 -V 1410 -P 6000

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 004 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x08 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Novatel
   Model String: Mass Storage
Revision String: 1.00
-------------------------
USB description data (for identification)
-------------------------
Manufacturer: Novatel Wireless Inc.
     Product: 
  Serial No.: 091124603460000
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

``````

michael@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 003 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 004 Device 007: ID 1410:5020 Novatel Wireless 

```No changes...

then i ran:
```
sudo usb_modeswitch -v 0x1410 -p 0x5020 -M "5553424312345678000000000000061b000000020000000000000000000000"

``` and this successfully switched the driver and I had use of the device. I have VirtualBox not VMWare... not sure if that makes a difference.


disconnect/reconnect and it's gone again.

I just added the line to the 40-usb-modeswitch.rules file. Rebooting now and then I'll update.

Update:
Still doesn't switch automatically. Any other ideas? I guess I could just write a script to run at startup but if root is required I'm not sure how to do that.

---

### Post by alexfish on 2012-05-09
Think maybe done a Oopsy with this

"sudo gedit /etc/usb_modeswitch.d/40-usb_modeswitch.rules/1410:5020"

```
sudo cp /etc/usb_modeswitch.d/40-usb_modeswitch.rules/1410:5020  /etc/usb_modeswitch.d/1410:5020
```should have twig when said the  "40-usb_modeswitch.rules" did not exist ,

---

### Post by ominub on 2012-05-09
Ha ha. ok I ran that. you added a "can" at the front of that command. It must have been a typo.

That did it. I plugged it in and came right up on the network manager drop down. thank you so much for your help.

SOLVED!

---

### Post by rstaph on 2012-07-11
> **alexfish said:**
> Think maybe done a Oopsy with this

"sudo gedit /etc/usb_modeswitch.d/40-usb_modeswitch.rules/1410:5020"

```
sudo cp /etc/usb_modeswitch.d/40-usb_modeswitch.rules/1410:5020  /etc/usb_modeswitch.d/1410:5020
```should have twig when said the  "40-usb_modeswitch.rules" did not exist ,

The rest of the commands you gave got me out of storage mode on my USB760 but remove or reboot and I have to reissue them.

Should I just create the directory 40-usb_modeswitch.rules if it doesn't exist?

I'm on 10.04 armel but the instructions in this thread worked the best of all the ones I've found.  I do not have access to a gui environment, so the howto I found using nm-connection-editor got me no where.

---

### Post by alexfish on 2012-07-11
> **rstaph said:**
> The rest of the commands you gave got me out of storage mode on my USB760 but remove or reboot and I have to reissue them.

Should I just create the directory 40-usb_modeswitch.rules if it doesn't exist?

I'm on 10.04 armel but the instructions in this thread worked the best of all the ones I've found.  I do not have access to a gui environment, so the howto I found using nm-connection-editor got me no where.
Hi

not sure if pointing in the right direction

but there is a usb_modswitch for arm at,

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

alexfish

---

