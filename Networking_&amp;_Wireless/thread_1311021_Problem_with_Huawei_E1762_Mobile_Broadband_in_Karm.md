---
title: "Problem with Huawei E1762 Mobile Broadband in Karmic"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by myandylai on 2009-11-02
I encounter a problem with my Huawei E1762 Mobile Broadband in Karmic (9.10) which I was using without any problem in Jaunty (9.04) using usb-modeswitch.

In Karmic Huawei E1762 not even detecting the Storage Device (Windows base software). It only detect the SD Storage Slot (without SD Card). In Jaunty it detect the Storage Device (Windows base software) but not the SD Storage Slot.

[IMG]http://i889.photobucket.com/albums/ac92/ltetlie/novista.png[/IMG]

Now when I use usb_modeswitch it show up something like this,

without HuaweiMode=1
#################################     
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 005 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: J&#65533;&#65533; 
&#65533;
   Model String:k
Revision String: 
-------------------------

Device description data (identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Warning: no switching method given.
##################################

with HuaweiMode=1
##################################
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 005 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: H&#65533;&#65533;
   Model String: <Sww
Revision String: w.sv
-------------------------

Device description data (identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent
-> Run lsusb to note any changes. Bye.
##################################

sudo lsusb

##################################
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
##################################

when it is working it should be someting like this in "lsusb"

##################################
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
##################################

here's my /etc/usb_modeswitch.conf

##################################
DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=   0x12d1
TargetProduct=  0x1003

HuaweiMode=1
##################################

and I also try this, but no luck

##################################
sudo rmmod usb-storage

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1003

sudo pppd ttyUSB0
##################################

NOW here's the funny part, when I start my Vista first and insect the Huawei E1762 dongle and restart to Karmic without removing the Huawei E1762 dongle. All the storage device including the Windows Software part come out.

[IMG]http://i889.photobucket.com/albums/ac92/ltetlie/huawei_sdstorage.png[/IMG]

[COLOR=Red]EVERTHING WORKS[/COLOR]. Not even necessary to unmount any of the Storage Device. Straight can connect to my ISP network. 

[IMG]http://i889.photobucket.com/albums/ac92/ltetlie/connected.png[/IMG]

lsusb

####################################
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
####################################

Any one have idea on how to enable the Huawei E1762 in Karmic without login to Vista first. Thanks.

---

### Post by hogsmate on 2009-11-02
yeah same thing happens to me too when i reboot from seven it works im using Huawei E220 :(
there is a bug it seems check the link
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

### Post by myandylai on 2009-11-03
Still not working even change Kernel to [2.6.31-14]("http://people.canonical.com/%7Eapw/lp451337-karmic/").

Anyone had temporary solution yet?

---

### Post by pdc on 2009-11-03
No;

what would make you re-install 9.04 ?

---

### Post by Muflon on 2009-11-03
> **hogsmate said:**
> yeah same thing happens to me too when i reboot from seven it works im using Huawei E220 :(
there is a bug it seems check the link
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Hi Hogsmate

I am using the E220 as well and it works for me with Karmic.

[http://ubuntuforums.org/showthread.php?t=1286938](http://ubuntuforums.org/showthread.php?t=1286938)

I was using it last night.  When I connect it and the blue/green light on the dongle goes solid (stops flashing) it works and sometimes it doesn't.  Using the route command I noticed differences between when it works and when it doesn't.  When it works the route command reports 3 entries and in the last entry the Gateway field is a domain name and not an IP address.  When it doesn't work I just disconnect and reconnect in Network Manager until the route command produces the correct results.

I will post some examples tonight when I get home.

Muflon

---

### Post by myandylai on 2009-11-03
pdc: I think i am going to stick with Karmic for a while cause I like the way that I can easy disconnect the WIFI connection on Karmic (9.10). Jaunty(9.04) would need to disable Wireless Network to disconnect from a connected WIFI link.

Temporary I can use my ADSL service to connect to internet. Mobile broadband I usually use it when I am on the road or I may use it in Windows Vista.

Thanks for the advice. If thing got too difficult to enable the Mobile Broadband device in Karmic I would change back to Jaunty.

---

### Post by Muflon on 2009-11-03
> **Muflon said:**
> Hi Hogsmate

I am using the E220 as well and it works for me with Karmic.

[http://ubuntuforums.org/showthread.php?t=1286938](http://ubuntuforums.org/showthread.php?t=1286938)

I was using it last night.  When I connect it and the blue/green light on the dongle goes solid (stops flashing) it works and sometimes it doesn't.  Using the route command I noticed differences between when it works and when it doesn't.  When it works the route command reports 3 entries and in the last entry the Gateway field is a domain name and not an IP address.  When it doesn't work I just disconnect and reconnect in Network Manager until the route command produces the correct results.

I will post some examples tonight when I get home.

Muflon

As promised here is my experience:

Plug in Vodafone dongle having already configured it using Network-manager.  Dongle flashes green and I then connect the Mobile Broadband 'Vodafone TopUp and Go' connection.  Dongle green light stops flashing.  Route command shows:

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
```

The internet connection doesn't work, so I disconnect the connection using Network-manager and then reconnect it.  After doing this a further 7 times I finally get the following route results:

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
host64.msm.che. *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         host64.msm.che. 0.0.0.0         UG    0      0        0 ppp0

```

Notice the 'host64.msm.che.' entry and the internet now works.  I am writing this post using the E220.

Hope this helps.

Muflon

---

### Post by pdc on 2009-11-03
thanks for this Muflon; 

I connected my E220 to a liveCD of Ubuntu 9.10 and 9.04 and got the continuous light! and the OS believed it was connected; but firefox would not load the webpage;

using the route command, I got the 

> default         10.64.64.64and then booted easypeasy (a UNR variant that is installed on our Eee)

I got connected; got firefox connected; and route gave me

> default         10.64.64.64 with firefox connecting to websites; so that doesn't seem to be the discriminating factor?

---

### Post by Muflon on 2009-11-04
Hi pdc

Did you try the disconnecting and reconnecting in 9.10.  In my example it took 7 attempts before it worked.

I think the route command is reporting a symptom of the underlying problem.  I haven’t managed to get to the bottom of why it works sometimes and not other yet.

Best of luck!

Muflon

---

### Post by hogsmate on 2009-11-04
hey guys this might be a bit stupid but it worked for me 
when i log in to ubuntu the modem doesn't work but it says or the notification area says that the network connection is established and available but cant browse or chat or do an installation using apt-get then wat i did was i logged out and logged in again vola it works fine :D i think its the easiest way to overcome this till this bug is fixed.
:popcorn:):P

---

### Post by myandylai on 2009-11-04
It seem Kernel [2.6.31.5]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.5/") may temporary fix this issue. But the kernel header for 2.6.31.5 (linux-headers-2.6.31-02063105-generic_2.6.31-02063105_i386) seem to have some problem.

[IMG]http://i889.photobucket.com/albums/ac92/ltetlie/linux-header-bad.png[/IMG]

but the Kernel Image (linux-image-2.6.31-02063105-generic_2.6.31-02063105_i386) was fine.

[IMG]http://i889.photobucket.com/albums/ac92/ltetlie/linux-images-ok.png[/IMG]

Anyone have workaround so I can try out the kernel on my little Huawei E1762 Mobile Broadband device.

Thanks.

---

### Post by brunoscunha on 2009-11-14
I rather wait for the fix. Logging in, logging out, logging in and logging out or whatever other way is not an option for me. This issue should be dealt with as soon as possible. Many people depend on huaway E220

---

### Post by brunoscunha on 2009-11-14
Installed 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

>  from ttyUSB0
<6>[  133.935677] option 5-1:1.0: device disconnected
<6>[  133.935756] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  133.935777] option 5-1:1.1: device disconnected
<6>[  134.044090] usb 5-1: reset full speed USB device using uhci_hcd and address 3
<6>[  134.186965] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  134.187133] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  134.191282] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  134.191453] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  134.588857] option: option_instat_callback: error -108
<6>[  134.590198] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  134.590245] option 5-1:1.0: device disconnected
<6>[  134.590406] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  134.590445] option 5-1:1.1: device disconnected
<6>[  134.704130] usb 5-1: reset full speed USB device using uhci_hcd and address 3
<3>[  134.824084] usb 5-1: device descriptor read/64, error -71
<6>[  134.992219] usb 5-1: USB disconnect, address 3
<3>[  135.000599] scsi 7:0:0:0: rejecting I/O to dead device
<6>[  151.868109] usb 5-1: new full speed USB device using uhci_hcd and address 4
<6>[  152.024559] usb 5-1: configuration #1 chosen from 1 choice
<6>[  152.035149] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  152.035313] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  152.037556] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  152.037691] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  152.038766] scsi12 : SCSI emulation for USB Mass Storage devices
<7>[  152.039040] usb-storage: device found at 4
<7>[  152.039045] usb-storage: waiting for device to settle before scanning
<7>[  157.037941] usb-storage: device scan complete
<3>[  177.818249] option: option_instat_callback: error -108
<6>[  177.818499] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  177.818548] option 5-1:1.0: device disconnected
<6>[  177.818709] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  177.818749] option 5-1:1.1: device disconnected
<6>[  177.928086] usb 5-1: reset full speed USB device using uhci_hcd and address 4
<6>[  178.070652] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  178.070818] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  178.075611] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  178.075779] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  178.117436] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  178.141439] sr0: scsi-1 drive
<7>[  178.141696] sr 12:0:0:0: Attached scsi CD-ROM sr0
<5>[  178.141838] sr 12:0:0:0: Attached scsi generic sg1 type 5
<3>[  190.645715] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  190.645748] sr: Sense Key : No Sense [current] 
<6>[  190.645758] sr: Add. Sense: No additional sense information
<3>[  190.844813] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  190.844845] sr: Sense Key : No Sense [current] 
<6>[  190.844856] sr: Add. Sense: No additional sense information
<3>[  190.920788] option: option_instat_callback: error -108
<6>[  190.920920] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  190.920945] option 5-1:1.0: device disconnected
<6>[  190.921042] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  190.921063] option 5-1:1.1: device disconnected
<6>[  191.033076] usb 5-1: reset full speed USB device using uhci_hcd and address 4
<6>[  191.175203] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  191.175373] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  191.180425] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  191.180602] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  191.577124] option: option_instat_callback: error -108
<6>[  191.587267] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  191.587302] option 5-1:1.0: device disconnected
<6>[  191.587459] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  191.587497] option 5-1:1.1: device disconnected
<6>[  191.697088] usb 5-1: reset full speed USB device using uhci_hcd and address 4
<6>[  191.761178] usb 5-1: USB disconnect, address 4
<6>[  208.752115] usb 5-1: new full speed USB device using uhci_hcd and address 5
<6>[  208.908546] usb 5-1: configuration #1 chosen from 1 choice
<6>[  208.919971] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  208.920217] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  208.933273] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  208.933453] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  208.939011] scsi19 : SCSI emulation for USB Mass Storage devices
<7>[  208.941214] usb-storage: device found at 5
<7>[  208.941217] usb-storage: waiting for device to settle before scanning
<7>[  213.941998] usb-storage: device scan complete
<3>[  234.806288] option: option_instat_callback: error -108
<6>[  234.806527] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  234.806575] option 5-1:1.0: device disconnected
<6>[  234.806737] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  234.806777] option 5-1:1.1: device disconnected
<6>[  234.916128] usb 5-1: reset full speed USB device using uhci_hcd and address 5
<6>[  235.058684] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  235.058857] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  235.060223] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  235.060369] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  235.083460] scsi 19:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  235.105491] sr0: scsi-1 drive
<7>[  235.105753] sr 19:0:0:0: Attached scsi CD-ROM sr0
<5>[  235.105899] sr 19:0:0:0: Attached scsi generic sg1 type 5
<3>[  245.646754] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  245.646786] sr: Sense Key : No Sense [current] 
<6>[  245.646796] sr: Add. Sense: No additional sense information
<3>[  245.848855] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  245.848887] sr: Sense Key : No Sense [current] 
<6>[  245.848897] sr: Add. Sense: No additional sense information
<3>[  245.944847] option: option_instat_callback: error -108
<6>[  245.944983] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  245.945008] option 5-1:1.0: device disconnected
<6>[  245.945091] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  245.945111] option 5-1:1.1: device disconnected
<6>[  246.056115] usb 5-1: reset full speed USB device using uhci_hcd and address 5
<6>[  246.199248] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  246.199416] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  246.200832] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  246.200975] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  246.614224] option: option_instat_callback: error -108
<6>[  246.616761] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  246.616806] option 5-1:1.0: device disconnected
<6>[  246.616974] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  246.617014] option 5-1:1.1: device disconnected
<6>[  246.672401] usb 5-1: USB disconnect, address 5
<3>[  246.676192] scsi 19:0:0:0: rejecting I/O to dead device
<3>[  246.680470] scsi 19:0:0:0: rejecting I/O to dead device
<6>[  263.764073] usb 5-1: new full speed USB device using uhci_hcd and address 6
<6>[  263.920957] usb 5-1: configuration #1 chosen from 1 choice
<6>[  263.931303] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  263.931474] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  263.936880] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  263.937118] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  263.963807] scsi26 : SCSI emulation for USB Mass Storage devices
<7>[  263.966480] usb-storage: device found at 6
<7>[  263.966483] usb-storage: waiting for device to settle before scanning
<7>[  268.969402] usb-storage: device scan complete
<3>[  289.807661] option: option_instat_callback: error -108
<6>[  289.807814] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  289.807840] option 5-1:1.0: device disconnected
<6>[  289.807924] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  289.807949] option 5-1:1.1: device disconnected
<6>[  289.920057] usb 5-1: reset full speed USB device using uhci_hcd and address 6
<6>[  290.067929] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  290.068064] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  290.068232] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  290.068296] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  290.105065] scsi 26:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  290.143878] sr0: scsi-1 drive
<7>[  290.144031] sr 26:0:0:0: Attached scsi CD-ROM sr0
<5>[  290.144109] sr 26:0:0:0: Attached scsi generic sg1 type 5
<3>[  300.658135] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  300.658151] sr: Sense Key : No Sense [current] 
<6>[  300.658156] sr: Add. Sense: No additional sense information
<3>[  300.910260] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  300.910276] sr: Sense Key : No Sense [current] 
<6>[  300.910281] sr: Add. Sense: No additional sense information
<3>[  301.073297] option: option_instat_callback: error -108
<6>[  301.074005] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  301.074031] option 5-1:1.0: device disconnected
<6>[  301.074117] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  301.074137] option 5-1:1.1: device disconnected
<6>[  301.185057] usb 5-1: reset full speed USB device using uhci_hcd and address 6
<6>[  301.344142] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  301.344242] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  301.352218] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  301.352323] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  301.748633] option: option_instat_callback: error -108
<6>[  301.753920] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  301.753938] option 5-1:1.0: device disconnected
<6>[  301.754014] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  301.754033] option 5-1:1.1: device disconnected
<6>[  301.865055] usb 5-1: reset full speed USB device using uhci_hcd and address 6
<6>[  301.936042] usb 5-1: USB disconnect, address 6
<6>[  318.940085] usb 5-1: new full speed USB device using uhci_hcd and address 7
<6>[  319.100529] usb 5-1: configuration #1 chosen from 1 choice
<6>[  319.105532] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  319.105698] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  319.107570] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  319.107710] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  319.109741] scsi33 : SCSI emulation for USB Mass Storage devices
<7>[  319.110019] usb-storage: device found at 7
<7>[  319.110024] usb-storage: waiting for device to settle before scanning
<7>[  324.128278] usb-storage: device scan complete
<3>[  344.991251] option: option_instat_callback: error -108
<6>[  344.991387] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  344.991412] option 5-1:1.0: device disconnected
<6>[  344.991496] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  344.991517] option 5-1:1.1: device disconnected
<6>[  345.104134] usb 5-1: reset full speed USB device using uhci_hcd and address 7
<6>[  345.242645] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  345.242827] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  345.243867] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  345.243999] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  345.268432] scsi 33:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  345.290434] sr0: scsi-1 drive
<7>[  345.290570] sr 33:0:0:0: Attached scsi CD-ROM sr0
<5>[  345.290649] sr 33:0:0:0: Attached scsi generic sg1 type 5
<6>[  355.247485] PPP BSD Compression module registered
<6>[  355.298740] PPP Deflate Compression module registered
<3>[  357.643634] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  357.643665] sr: Sense Key : No Sense [current] 
<6>[  357.643675] sr: Add. Sense: No additional sense information
<3>[  357.864745] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  357.864777] sr: Sense Key : No Sense [current] 
<6>[  357.864787] sr: Add. Sense: No additional sense information
<3>[  357.989814] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  357.989846] sr: Sense Key : No Sense [current] 
<6>[  357.989856] sr: Add. Sense: No additional sense information
<3>[  357.996826] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
<6>[  357.996852] sr: Sense Key : No Sense [current] 
<6>[  357.996862] sr: Add. Sense: No additional sense information
<3>[  358.004711] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
<6>[  358.004754] sr: Sense Key : No Sense [current] 
<6>[  358.004764] sr: Add. Sense: No additional sense information
<3>[  358.028842] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  358.028873] sr: Sense Key : No Sense [current] 
<6>[  358.028884] sr: Add. Sense: No additional sense information
<7>[  358.040827] ISO 9660 Extensions: Microsoft Joliet Level 3
<3>[  358.053789] option: option_instat_callback: error -108
<6>[  358.055158] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  358.055192] option 5-1:1.0: device disconnected
<6>[  358.055355] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  358.055396] option 5-1:1.1: device disconnected
<6>[  358.165088] usb 5-1: reset full speed USB device using uhci_hcd and address 7
<6>[  358.307226] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  358.307397] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  358.310077] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  358.310238] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
<3>[  358.709116] option: option_instat_callback: error -108
<6>[  358.710681] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
<6>[  358.710725] option 5-1:1.0: device disconnected
<6>[  358.710896] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  358.710934] option 5-1:1.1: device disconnected
<6>[  358.828114] usb 5-1: reset full speed USB device using uhci_hcd and address 7
<6>[  358.892202] usb 5-1: USB disconnect, address 7
<6>[  358.892230] sr 33:0:0:0: [sr0] Unhandled error code
<6>[  358.892237] sr 33:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
<3>[  358.892247] end_request: I/O error, dev sr0, sector 43708
<4>[  358.893065] ISOFS: unable to read i-node block
<4>[  358.893077] isofs_fill_super: get root inode failed
<6>[  375.892124] usb 5-1: new full speed USB device using uhci_hcd and address 8
<6>[  376.046556] usb 5-1: configuration #1 chosen from 1 choice
<6>[  376.061431] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  376.061621] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  376.065600] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  376.065760] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  376.075394] scsi40 : SCSI emulation for USB Mass Storage devices
<7>[  376.075542] usb-storage: device found at 8
<7>[  376.075544] usb-storage: waiting for device to settle before scanning
<7>[  381.073964] usb-storage: device scan complete
<3>[  402.002331] option: option_instat_callback: error -108
<6>[  402.002579] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  402.002627] option 5-1:1.0: device disconnected
<6>[  402.002794] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  402.002835] option 5-1:1.1: device disconnected
<6>[  402.112133] usb 5-1: reset full speed USB device using uhci_hcd and address 8
<6>[  402.254731] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  402.254906] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  402.258274] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  402.258447] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  402.288569] scsi 40:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  402.312515] sr0: scsi-1 drive
<7>[  402.312693] sr 40:0:0:0: Attached scsi CD-ROM sr0
<5>[  402.312795] sr 40:0:0:0: Attached scsi generic sg1 type 5
<3>[  414.643700] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  414.643731] sr: Sense Key : No Sense [current] 
<6>[  414.643741] sr: Add. Sense: No additional sense information
<3>[  414.882873] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  414.882889] sr: Sense Key : No Sense [current] 
<6>[  414.882894] sr: Add. Sense: No additional sense information
<3>[  414.981790] option: option_instat_callback: error -108
<6>[  414.983259] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  414.983286] option 5-1:1.0: device disconnected
<6>[  414.983366] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  414.983386] option 5-1:1.1: device disconnected
<6>[  415.092121] usb 5-1: reset full speed USB device using uhci_hcd and address 8
<6>[  415.235257] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  415.235433] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  415.239958] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  415.240165] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  415.637133] option: option_instat_callback: error -108
<6>[  415.638323] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  415.638339] option 5-1:1.0: device disconnected
<6>[  415.638415] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  415.638434] option 5-1:1.1: device disconnected
<6>[  415.749089] usb 5-1: reset full speed USB device using uhci_hcd and address 8
<3>[  415.868106] usb 5-1: device descriptor read/64, error -71
<6>[  416.037094] usb 5-1: USB disconnect, address 8
<6>[  432.821097] usb 5-1: new full speed USB device using uhci_hcd and address 9
<6>[  432.974587] usb 5-1: configuration #1 chosen from 1 choice
<6>[  432.980568] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  432.980732] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  432.986670] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  432.986842] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<6>[  432.992485] scsi47 : SCSI emulation for USB Mass Storage devices
<7>[  433.013324] usb-storage: device found at 9
<7>[  433.013327] usb-storage: waiting for device to settle before scanning
<7>[  438.018023] usb-storage: device scan complete
<3>[  458.990369] option: option_instat_callback: error -108
<6>[  458.990616] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  458.990666] option 5-1:1.0: device disconnected
<6>[  458.990834] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  458.990875] option 5-1:1.1: device disconnected
<6>[  459.100129] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<6>[  459.238801] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  459.238971] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  459.240912] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  459.241057] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<5>[  459.279564] scsi 47:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
<4>[  459.303554] sr0: scsi-1 drive
<7>[  459.303812] sr 47:0:0:0: Attached scsi CD-ROM sr0
<5>[  459.303957] sr 47:0:0:0: Attached scsi generic sg1 type 5
<3>[  471.641723] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  471.641756] sr: Sense Key : No Sense [current] 
<6>[  471.641766] sr: Add. Sense: No additional sense information
<3>[  471.842822] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
<6>[  471.842854] sr: Sense Key : No Sense [current] 
<6>[  471.842864] sr: Add. Sense: No additional sense information
<3>[  471.949815] option: option_instat_callback: error -108
<6>[  471.949966] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  471.949990] option 5-1:1.0: device disconnected
<6>[  471.950069] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  471.950090] option 5-1:1.1: device disconnected
<6>[  472.060090] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<6>[  472.203286] option 5-1:1.1: GSM modem (1-port) converter detected
<6>[  472.203472] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
<6>[  472.203606] option 5-1:1.0: GSM modem (1-port) converter detected
<6>[  472.203742] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
<3>[  502.991362] option: option_instat_callback: error -108
<6>[  502.993661] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
<6>[  502.993709] option 5-1:1.0: device disconnected
<6>[  502.993873] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
<6>[  502.993913] option 5-1:1.1: device disconnected
<6>[  503.108073] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<3>[  503.228047] usb 5-1: device descriptor read/64, error -71
<3>[  503.452100] usb 5-1: device descriptor read/64, error -71
<6>[  503.668123] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<3>[  503.788121] usb 5-1: device descriptor read/64, error -71
<3>[  504.012129] usb 5-1: device descriptor read/64, error -71
<6>[  504.228129] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<3>[  504.644121] usb 5-1: device not accepting address 9, error -71
<6>[  504.756125] usb 5-1: reset full speed USB device using uhci_hcd and address 9
<3>[  505.164144] usb 5-1: device not accepting address 9, error -71
<6>[  505.164215] sr 47:0:0:0: Device offlined - not ready after error recovery
<3>[  505.164255] sr 47:0:0:0: rejecting I/O to offline device
<3>[  505.164334] sr 47:0:0:0: rejecting I/O to offline device
<6>[  505.164662] usb 5-1: USB disconnect, address 9
<6>[  505.276146] usb 5-1: new full speed USB device using uhci_hcd and address 10
<3>[  505.396081] usb 5-1: device descriptor read/64, error -71
<3>[  505.620104] usb 5-1: device descriptor read/64, error -71
<6>[  505.836108] usb 5-1: new full speed USB device using uhci_hcd and address 11
<3>[  505.956508] usb 5-1: device descriptor read/64, error -71
<3>[  506.180101] usb 5-1: device descriptor read/64, error -71
<6>[  506.396070] usb 5-1: new full speed USB device using uhci_hcd and address 12
<3>[  506.808140] usb 5-1: device not accepting address 12, error -71
<6>[  506.920128] usb 5-1: new full speed USB device using uhci_hcd and address 13
<3>[  507.328145] usb 5-1: device not accepting address 13, error -71
<3>[  507.328176] hub 5-0:1.0: unable to enumerate USB device on port 1
<6>[  550.590248] [drm] TV-16: set mode NTSC 480i 0
<6>[  550.756279] [drm] TV-16: set mode NTSC 480i 0
<6>[  551.080753] [drm] TV-16: set mode NTSC 480i 0
<6>[  551.248228] [drm] TV-16: set mode NTSC 480i 0
<6>[  552.679583] [drm] TV-16: set mode NTSC 480i 0
<6>[  552.846301] [drm] TV-16: set mode NTSC 480i 0
<6>[  553.171884] [drm] TV-16: set mode NTSC 480i 0
<6>[  553.337159] [drm] TV-16: set mode NTSC 480i 0
<6>[  553.658770] [drm] TV-16: set mode NTSC 480i 0
<6>[  553.826201] [drm] TV-16: set mode NTSC 480i 0
<6>[  565.124388] [drm] TV-16: set mode NTSC 480i 0
<6>[  565.289789] [drm] TV-16: set mode NTSC 480i 0
<6>[  565.612247] [drm] TV-16: set mode NTSC 480i 0
<6>[  565.778257] [drm] TV-16: set mode NTSC 480i 0
<6>[  566.103490] [drm] TV-16: set mode NTSC 480i 0
<6>[  566.268919] [drm] TV-16: set mode NTSC 480i 0
<6>[  567.282325] [drm] TV-16: set mode NTSC 480i 0
<6>[  567.448172] [drm] TV-16: set mode NTSC 480i 0
<6>[  591.353824] [drm] TV-16: set mode NTSC 480i 0
<6>[  591.519590] [drm] TV-16: set mode NTSC 480i 0
<6>[  591.838795] [drm] TV-16: set mode NTSC 480i 0
<6>[  592.004277] [drm] TV-16: set mode NTSC 480i 0
<6>[  593.434592] [drm] TV-16: set mode NTSC 480i 0
<6>[  593.600311] [drm] TV-16: set mode NTSC 480i 0
<6>[  593.920181] [drm] TV-16: set mode NTSC 480i 0
<6>[  594.086315] [drm] TV-16: set mode NTSC 480i 0
<6>[  594.402595] [drm] TV-16: set mode NTSC 480i 0
<6>[  594.568025] [drm] TV-16: set mode NTSC 480i 0
bruno@bruno-laptop:~$ uname -r
2.6.31-15-generic
bruno@bruno-laptop:~$ uname -a
Linux bruno-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
bruno@bruno-laptop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@rothera) (gcc version 4.4
.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 (Ubuntu
 2.6.31-15.50-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7b0000 (usable)
[    0.000000]  BIOS-e820: 000000005f7b0000 - 000000005f7c5400 (reserved)
[    0.000000]  BIOS-e820: 000000005f7c5400 - 000000005f7e7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f7e7fb8 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x5f7b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:


---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by alexfish on 2009-11-19
hi same problems but  with  "vodafone top up an go"  its a huawei device on system Ubuntu 9.10 


i downloaded usb-modeswitch via synaptic 

went  to this site very useful and worth a visit  their supported devices are list


[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

.................................................................................................................
 I copied the " usb_modeswitch.conf " to my  "/etc/usb_modeswitch.conf" which was empty ?

saved and rebooted


after letting the system settle approx 30 seconds i put the device in ,one thing i did notice is


 1) when the cd/file appeared on the desk i hovered the mouse over the network manager 

 2) the cd/file changed colour , this was the cd/file   safely remove drive

    cd/file appeared again ,repeated 1)

 this time the it did not changed colour / connected through the nextwork manager and the browser connected 1st time
 ...................................................................................................................
 I don't if know if this is of any help 


 but the site above may be worth a visit

---

### Post by pdc on 2009-11-20
so you installed the programme "usb_modeswitch"?

---

### Post by alexfish on 2009-11-20
> **pdc said:**
> so you installed the programme "usb_modeswitch"?
  
  yes, it was the only way it to get rid of one the devices but still had problems getting the browser to connect 

  copied the file as per say ,  now connects  most of the time and remains stable
 
   think there is still a problem somewhere "kernel" ? don' know

          ran the system test  network test   it shows    http connection:success
                                                                                                                                            ftp   connection:success

                                 but the test your connection                     no internet connection

   which is not so  , doing the test   as I sit typing this in at the forum ?

  the site list is worth a visit, its good reading and hope it helps you and others

 

  ps i have downloaded the results of the test

---

### Post by alexfish on 2009-11-25
problems connecting RE: add ppa:network-manager/trunk

link

[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

---

### Post by rajesh.ravella on 2009-11-29
> **hogsmate said:**
> hey guys this might be a bit stupid but it worked for me 
when i log in to ubuntu the modem doesn't work but it says or the notification area says that the network connection is established and available but cant browse or chat or do an installation using apt-get then wat i did was i logged out and logged in again vola it works fine :D i think its the easiest way to overcome this till this bug is fixed.
:popcorn:):P


Ok Thanks for your update, let me try agian! and see ... if it works will let you know..

---

### Post by gasapi on 2009-12-07
Found a workaround to the problem.

The problem arises because the device is detected as a modem and a storage device at the same time.

So, when repeated attempts fail to connect, right-click on the device on the desktop and select Safely Remove Drive. The connection (which does not actually connect) terminates at this point. Then click on the Network Manager Applet and select the Mobile Broadband connection. It will connect. The storage device is not shown. It worked with my e220.

---

### Post by gasapi on 2009-12-25
The 2nd reply (3rd note) in the following thread solved the issue.

[http://ubuntuforums.org/showthread.php?t=1306053&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=1306053&highlight=pppoe)

Just have to add the PPA as directed in [https://edge.launchpad.net/~network-manager/+archive/trunk]("https://edge.launchpad.net/%7Enetwork-manager/+archive/trunk")

Good luck!

---

