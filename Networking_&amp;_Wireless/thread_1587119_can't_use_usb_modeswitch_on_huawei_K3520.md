---
title: "can't use usb modeswitch on huawei K3520"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by chanweian on 2010-10-03
Hi everyone, just installed ubuntu!!
i'm having problems trying to get ubuntu to recognise my usb modem because its one of those "flip-flop"/"zero-cd" devices.
[B]
okay so this is what is inside the usb-modeswitch.conf file
[/B]
```
########################################################
# Huawei E169

DefaultVendor= 0x12d1
DefaultProduct=0x1001

TargetClass=0xff

CheckSuccess=20

HuaweiMode=1
```

**this is what i type in the terminal:**

```
sudo usb_modeswitch
```

**and this is what i get out:**

```
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Accessing device 002 on bus 005 ...
Using endpoints 0x02 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
     Product: HUAWEI Mobile
  Serial No.: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Original device can't be accessed anymore. Good.
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 No new devices in target mode or class found

```

let me know if you need anymore information, and thanks in advance!

---

### Post by alexfish on 2010-10-03
hi

need more info

from the terminal ,can post results of these commands,

code:
[COLOR=Blue]usb-devices[/COLOR]

from the above command post only the [COLOR=Blue]parts relevant to the device[/COLOR]

code:

[COLOR=Blue]ls -al /dev/serial/by-id/*[/COLOR]

---

### Post by chanweian on 2010-10-03
[COLOR=Blue]usb-devices:[/COLOR]
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

[COLOR=Blue]ls -al /dev/serial/by-id/*:
[/COLOR]```
lrwxrwxrwx 1 root root 13 2010-10-04 10:04 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-10-04 10:04 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0 -> ../../ttyUSB1

```

---

### Post by alexfish on 2010-10-04
hi

from the listing(usb-devices), the device has been recognised but may have been incorectly switched

I:  If#= 0 Alt= 0 #[COLOR=Blue]EPs= 3[/COLOR] Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid <====== this line with ([COLOR=Blue]EPs= 3{interupt on port}[/COLOR]) normaly the modem
I:  [COLOR=Blue]If#= 1[/COLOR] Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <====== shows driver (option)
I:[COLOR=Blue]  If#= 2[/COLOR] Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <====== shows driver (option)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage <= storage part of the device

from the (ls -al /dev/serial/by-id/* . shows two ports available
 
[COLOR=Blue]if01-port0[/COLOR] -> ../../[COLOR=Blue]ttyUSB0[/COLOR] <=== normaly the Huawie modem port (but the above shows only 2EPs so may not work)
[COLOR=Blue]if02-port0[/COLOR] -> ../../[COLOR=Blue]ttyUSB1[/COLOR] <=== normaly a Huawie control port

Can I ask if Network Manager recognises the device or can connect to the internet

If Network Manager does not work (what happens if the usb-modeswitch is disabled)

regards

alexfish

---

### Post by chanweian on 2010-10-04
hi i couldnt find 'network manager' so here is a screenshot of all the network options i could find, i'm assuming that the device wasnt detected as the list was greyed out when i opened the 'Set up a mobile broadband connection' dialog box.

in this case both with modeswitch enabled and disabled, the device was not detected as a modem.

---

### Post by alexfish on 2010-10-04
hi

thought that would be the case

there is a connection manager which may work(you can only try)

can you have a look here

[http://www.sakis3g.org/](http://www.sakis3g.org/)

**read all including the links etc **(like instructions)

If you decide to install , un-install existing usb_modeswitch 
download full version( usb_modeswitch embedded )

there is a dedicated forum 

but if your stuck feel free to post back here

alexfish

---

### Post by chanweian on 2010-10-05
It still didnt work ):

But nvm, when i tried my friend's exact same modem it worked perfectly without any configuration, so i traded with him since he doesnt use ubuntu.

Not sure about this but I think that mine doesnt work because i had unlocked it previously and that somehow has affected it??

Anyway, thanks so much for your time and help!

---

### Post by alexfish on 2010-10-05
> **chanweian said:**
> It still didnt work ):

But nvm, when i tried my friend's exact same modem it worked perfectly without any configuration, so i traded with him since he doesnt use ubuntu.

Not sure about this but I think that mine doesnt work because i had unlocked it previously and that somehow has affected it??

Anyway, thanks so much for your time and help!

hi

Not a happy outcome

although not conclusive,(as this device could have developed the fault on it's own)

if the firmware is altered (from un-trusted sources) , or unlocked  there are risks

so for all Readers this should act a Caution as to what may happen

if you have followed this thread and noticed this line

[COLOR=Blue]I: If#= 0 Alt= 0 #EPs= 3 Cls=03(HID ) Sub=01 Prot=02 Driver=usbhid[/COLOR] <====== this line with (EPs= 3{interupt on port}) normaly the modem

in normal conditions (for this device ) the line should look something like

[COLOR=Blue]I: If#= 0 Alt= 0 #EPs= 3 Cls=03(HID ) Sub=01 Prot=02 Driver=option[/COLOR]

alexfish

---

### Post by chanweian on 2010-10-06
He's right,
I entered usb-devices into the terminal with the working modem and this is what came out:
```
T:  Bus=02 Lev=02 Prnt=03 Port=05 Cnt=03 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1465 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

---

### Post by maxiecool2 on 2011-09-20
has there been any progress on this subject? 
my usb modem is doing exactly what alexfish is saying it is doing

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#= 43 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

searching through many forums i havent been able to find a configuration to work with,
i have tried using sakis3g in debug mode to find out what it thought was causing the modem not to switch properly
this is its output [07249] [13:50:59] USB Device 12d1:1001 provides 1 interruptable endpoint(s).
[07249] [13:50:59] Interfaces collected from lsusb are: 0
[07249] [13:50:59] Collected 1 interface(s): 0
[07249] [13:50:59] Only one interface available. Will use that one unconditionally.
[07249] [13:50:59] Got valid USB interface 0 of USB modem "12d1:1001".
[07249] [13:50:59] Device 12d1:1001 sysfs dir found: /sys/bus/usb/devices/2-1/2-1.2
[07249] [13:50:59] Kernel provides AVOID_RESET_QUIRK for device 12d1:1001.
[07249] [13:50:59] Succesfully enabled AVOID_RESET_QUIRK for device 12d1:1001.
[07249] [13:50:59] Failed to enable AVOID_RESET_QUIRK for device 12d1:1001.
[07249] [13:50:59] Device has storage part on interface #3.
[07249] [13:50:59] Device 12d1:1001, provides storage interface #3.
[07249] [13:50:59] Device 12d1:1001 sysfs dir found: /sys/bus/usb/devices/2-1/2-1.2
[07249] [13:50:59] Storage interface #3 is binded by usb_storage driver.
[07249] [13:50:59] Device 12d1:1001 sysfs dir found: /sys/bus/usb/devices/2-1/2-1.2
[07249] [13:50:59] Information from sysfs:
USB Manufacturer: ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
USB Product:      HUAWEI_Mobile
USB Serial:       ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
[07249] [13:50:59] Checking interface #3 of device 12d1:1001.
[07249] [13:50:59] SCSI device is settled:
SCSI Vendor:      HUAWEI__
SCSI Model:       SD_Storage______
SCSI Revision:    2.31
[07249] [13:50:59] No storage device(s) with inserted media exist. Safe to unlock HAL.
[07249] [13:50:59] Device 12d1:1001 sysfs dir found: /sys/bus/usb/devices/2-1/2-1.2
[07249] [13:50:59] Found already loaded driver "usbhid".
[07249] [13:50:59] Driver "usbhid" already attached to interface #0 of device "12d1:1001".
[07249] [13:50:59] Verbosing: 14% Locating tty
[07249] [13:50:59] PID 8668 is still running.
[07249] [13:50:59] PID 8668 is still running.
[07249] [13:50:59] Device 12d1:1001 sysfs dir found: /sys/bus/usb/devices/2-1/2-1.2
[07249] [13:50:59] Interface #0 sysfs dir is: /sys/bus/usb/devices/2-1/2-1.2/2-1.2:1.0
[07249] [13:50:59] Failed to retrieve sysfs tty for interface #0.
[07249] [13:50:59] Waiting for driver usbhid to create tty of device 12d1:1001 (interface #0). [1 second(s) will have pass]
... it continues on to fail to connect

i am running natty nahwal with kernel 2.6.38-11-generic

my syslog:
Sep 20 00:59:22 lap002 kernel: [ 2492.973065] usb 2-1.2: new full speed USB device using ehci_hcd and address 11
Sep 20 00:59:22 lap002 kernel: [ 2492.989128] hub 2-1:1.0: unable to enumerate USB device on port 2
Sep 20 00:59:22 lap002 kernel: [ 2493.188526] usb 2-1.2: new full speed USB device using ehci_hcd and address 12
Sep 20 00:59:23 lap002 kernel: [ 2493.667088] usb 2-1.2: device not accepting address 12, error -32
Sep 20 00:59:23 lap002 kernel: [ 2493.683381] hub 2-1:1.0: unable to enumerate USB device on port 2
Sep 20 00:59:23 lap002 kernel: [ 2493.882653] usb 2-1.2: new full speed USB device using ehci_hcd and address 14
Sep 20 00:59:23 lap002 kernel: [ 2494.361327] usb 2-1.2: device not accepting address 14, error -32
Sep 20 00:59:23 lap002 kernel: [ 2494.377630] hub 2-1:1.0: unable to enumerate USB device on port 2
Sep 20 00:59:24 lap002 kernel: [ 2494.576922] usb 2-1.2: new full speed USB device using ehci_hcd and address 16
Sep 20 00:59:24 lap002 kernel: [ 2495.055584] usb 2-1.2: device not accepting address 16, error -32
Sep 20 00:59:24 lap002 kernel: [ 2495.127544] usb 2-1.2: new full speed USB device using ehci_hcd and address 17
Sep 20 00:59:24 lap002 kernel: [ 2495.223482] option 2-1.2:1.1: GSM modem (1-port) converter detected
Sep 20 00:59:24 lap002 kernel: [ 2495.223572] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
Sep 20 00:59:24 lap002 kernel: [ 2495.223956] option 2-1.2:1.2: GSM modem (1-port) converter detected
Sep 20 00:59:24 lap002 kernel: [ 2495.224031] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
Sep 20 00:59:24 lap002 kernel: [ 2495.225271] scsi16 : usb-storage 2-1.2:1.3
Sep 20 00:59:25 lap002 kernel: [ 2496.222691] scsi 16:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Sep 20 00:59:25 lap002 kernel: [ 2496.224638] scsi 16:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Sep 20 00:59:25 lap002 kernel: [ 2496.231631] sr1: scsi-1 drive
Sep 20 00:59:25 lap002 kernel: [ 2496.231795] sr 16:0:0:0: Attached scsi CD-ROM sr1
Sep 20 00:59:25 lap002 kernel: [ 2496.233530] sr 16:0:0:0: Attached scsi generic sg3 type 5
Sep 20 00:59:25 lap002 kernel: [ 2496.235244] sd 16:0:0:1: Attached scsi generic sg4 type 0
Sep 20 00:59:25 lap002 kernel: [ 2496.253571] sd 16:0:0:1: [sdc] Attached SCSI removable disk


thanks!

---

### Post by maxiecool2 on 2011-09-20
partial good news!
using detach storage flag drops the usbhid driver
now how to load the option driver in its place!

---

