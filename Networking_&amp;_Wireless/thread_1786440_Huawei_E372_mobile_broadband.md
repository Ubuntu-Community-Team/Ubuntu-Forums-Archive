---
title: "Huawei E372 mobile broadband"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by macgywer on 2011-06-19
Hello!

Any idea how I can get the huawei e372 to be recognized by ubuntu 11.04, so i can connect to the internet?

---

### Post by Matbro on 2011-06-28
Hi

Maybe this will work for you, my Huawei E367 was only discovered as a storage device in 11.04, though it worked perfectly in 10.10

After you connected your modem, run "lsusb" in a terminal and look for the huawei line. notice the xxxx:yyyy numbers 

[I]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1d57:2400  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 12d1:1506 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

enter:
sudo modprobe usbserial vendor=0x12d1 product=0x1506 (replace with your numbers)

run "dmesg" and see if you get any TTY messages

[I]usb 1-2: generic converter now attached to ttyUSB1
usbserial_generic 1-2:1.3: generic converter detected
usb 1-2: generic converter now attached to ttyUSB2[/I]

If you get similar result, the modem will be discovered in network manager (you have to enable "Enable Mobile Broadband" in the GUI)
/Mats

---

### Post by Bashar &quot; on 2011-09-21
> **Matbro said:**
> Hi

Maybe this will work for you, my Huawei E367 was only discovered as a storage device in 11.04, though it worked perfectly in 10.10

After you connected your modem, run "lsusb" in a terminal and look for the huawei line. notice the xxxx:yyyy numbers 

[I]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1d57:2400  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 12d1:1506 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

enter:
sudo modprobe usbserial vendor=0x12d1 product=0x1506 (replace with your numbers)

run "dmesg" and see if you get any TTY messages

[I]usb 1-2: generic converter now attached to ttyUSB1
usbserial_generic 1-2:1.3: generic converter detected
usb 1-2: generic converter now attached to ttyUSB2[/I]

If you get similar result, the modem will be discovered in network manager (you have to enable "Enable Mobile Broadband" in the GUI)
/Mats


having same issue and didnt get the TTY mesages, my lsusb is:
Bus 002 Device 007: ID 12d1:1505 Huawei Technologies Co., Ltd. 

and ran the command modprobe usbserial vendor=0x12d1 product=0x1505 as root but no luck

any other advises?

---

### Post by dave01945 on 2011-09-21
you could try this script it has always worked for me when the modem hasn't been detected properly it contains everything needed for mobile broadband

[Sakis3g](http://www.sakis3g.org/)

just run it as 

```
./sakis3g --interactive
```

---

### Post by Bashar &quot; on 2011-09-21
Thanks, but this solution solved it for me [http://www.santinoli.com/open/e1692-howto.html](http://www.santinoli.com/open/e1692-howto.html)

i just updated the numbers, so my usb_modeswitch.conf looks like this:
```

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=1

# Huawei E372
DefaultVendor=  0x12d1
DefaultProduct= 0x1505

TargetVendor=   0x12d1
TargetProduct=  0x140c

MessageContent="55534243000000000000000000000011060000000000000000000000000000"

CheckSuccess=5


```

then i run usb_modeswitch -c /etc/usb_modeswitch.conf

of course before that need to install usb_modeswitch using apt-get install usb-modeswitch

Thanks :)

---

### Post by alexfish on 2011-10-25
> **Tomas_L said:**
> excuse me, where can i pick the unlocked already E372 HUAWEI dongle? is there any1  take from mobile2wifi.co.uk? how about that?

unlock modems at own risk . can have a look here there is a bit about a Huawie device

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm) ; if it goes wrong  : Tuff

---

### Post by Bashar &quot; on 2011-11-05
> **Bashar " said:**
> Thanks, but this solution solved it for me [http://www.santinoli.com/open/e1692-howto.html](http://www.santinoli.com/open/e1692-howto.html)

i just updated the numbers, so my usb_modeswitch.conf looks like this:
```

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=1

# Huawei E372
DefaultVendor=  0x12d1
DefaultProduct= 0x1505

TargetVendor=   0x12d1
TargetProduct=  0x140c

MessageContent="55534243000000000000000000000011060000000000000000000000000000"

CheckSuccess=5


```

then i run usb_modeswitch -c /etc/usb_modeswitch.conf

of course before that need to install usb_modeswitch using apt-get install usb-modeswitch

Thanks :)


just to note after upgrading to 11.10 the device works out of the box without the need of the abve.

for those who might read this in future

---

### Post by alexfish on 2011-11-16
> **Tomas_L said:**
> any body has used the [E586 huawei]("http://www.mobile2wifi.co.uk/index.php?main_page=product_info&cPath=1&products_id=1") wifi router? does it works for Ubuntu system?

have started a new thread here

			 			[E586 huawei (mobile wifi router )]("http://ubuntuforums.org/showthread.php?t=1881919")

alexfish

---

### Post by axle88 on 2012-02-02
> **Bashar " said:**
> Thanks, but this solution solved it for me [http://www.santinoli.com/open/e1692-howto.html](http://www.santinoli.com/open/e1692-howto.html)

i just updated the numbers, so my usb_modeswitch.conf looks like this:
```

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=1

# Huawei E372
DefaultVendor=  0x12d1
DefaultProduct= 0x1505

TargetVendor=   0x12d1
TargetProduct=  0x140c

MessageContent="55534243000000000000000000000011060000000000000000000000000000"

CheckSuccess=5


```

then i run usb_modeswitch -c /etc/usb_modeswitch.conf

of course before that need to install usb_modeswitch using apt-get install usb-modeswitch

Thanks :)


Hey all,

I work with a phidgets single board computer which runs a stripped down version of debian and am trying to install a huawei E 372 modem. I however 
cannot get the modem to connect. I have tried using usbserial and usbmodeswitch but could not get it to work. Below are screen dumps describing whaat I have tried so far. Heres what I did:

[B]vendor/product id's from lsusb
[/B]
root@phidgetsbc:/# lsusb
Bus 001 Device 004: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 003: ID 06c2:0045 Phidgets Inc. (formerly GLAB) PhidgetInterface Kit 8-8-8
Bus 001 Device 002: ID 0451:2077 Texas Instruments, Inc. TUSB2077 Hub

[B]I then ran this command:
[/B]
modprobe usbserial vendor=0x12d1 product=0x1505

[B]The following are the new lines from dmesg
[/B]
usbserial: Unknown parameter `vendor'
usbserial: Unknown parameter `vendor'
usbcore: registered new interface driver usbserial
usbserial: USB Serial Driver core

[B]Any idea why this could be happening?
[/B]


[B]I then tried another approach by trying to 'switch' the modem using usb_modeswitch. This failed with the following terminal output:
[/B]
root@phidgetsbc:/# usb_modeswitch -c /usr/usbmode/usb-modeswitch-1.2.3/usb_modeswitch.conf 
Looking for target devices ...
No devices in target mode or class found
Looking for default devices ...
found matching product ID
adding device
Found device in default mode, class or configuration (1)
Accessing device 004 on bus 001 ...
Getting the current device configuration ...
OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
OK, driver found ("usb-storage")
OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
Vendor String: HUAWEI
Model String: Mass Storage
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Huawei Technologies
Product: HUAWEI Mobile
Serial No.: not provided
-------------------------
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
OK, message successfully sent
Resetting response endpoint 0x81
Could not reset endpoint (probably harmless): -62
Resetting message endpoint 0x01
Could not reset endpoint (probably harmless): -62
Device is gone, skipping any further commands

Checking for mode switch (max. 5 times, once per second) ...
Searching for target devices ...
Searching for target devices ...
Searching for target devices ...
Searching for target devices ...
Searching for target devices ...
No new devices in target mode or class found

[B]Mode switch has failed. Bye.
[/B]

[B]Here are the new lines from dmesg after trying to switch the modem with usb-modeswitch.
[/B]
usb 1-1.5: usbfs: process 1710 (usb_modeswitch) did not claim interface 0 before use
usb 1-1.5: USB disconnect, device number 4
usb 1-1.5: new full speed USB device number 5 using s3c2410-ohci
usb 1-1.5: New USB device found, idVendor=12d1, idProduct=14ac
usb 1-1.5: New USB device strings: Mfr=3, Product=2, SerialNumber=0
usb 1-1.5: Product: HUAWEI Mobile
usb 1-1.5: Manufacturer: Huawei Technologies
scsi2 : usb-storage 1-1.5:1.4
scsi3 : usb-storage 1-1.5:1.5
scsi 2:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
scsi 3:0:0:0: Direct-Access HUAWEI TF CARD Storage 2.31 PQ: 0 ANSI: 2
sd 3:0:0:0: [sda] Attached SCSI removable disk


[B]I hope this clears things up a bit. Theres probably something here that im just not seeing. Any help is greatly appreciated!
[/B]
BTW I was able to install the modem on a desktop computer running debian. I also tried using the sakis3g script but this did not work either.

---

### Post by alexfish on 2012-02-03
can post results of these commands from the terminal, locate the lines which indicate the device and post only those lines

```
usb-devices
```or
```
lsusb -t
```
and
```
lsusb -v
```

alexfish

---

### Post by axle88 on 2012-02-03
> **alexfish said:**
> can post results of these commands from the terminal, locate the lines which indicate the device and post only those lines

```
usb-devices
```or
```
lsusb -t
```
and
```
lsusb -v
```

alexfish

**Heres what I got from usb-devices**

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
[B]P:  Vendor=12d1 ProdID=1505 Rev=00.00
[/B]S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

[B]and here is the output from lsusb -v
[/B]
Bus 001 Device 004: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1505 E398 LTE/UMTS/GSM Modem/Networkcard
  bcdDevice            0.00
  iManufacturer           3 Huawei Technologies
  iProduct                2 HUAWEI Mobile
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          1 Huawei Configuration
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

### Post by alexfish on 2012-02-04
from previous posts when you ran the usb_modeswitch the device is switching from "1505" to "14ac"

switch the device to be seen as "14ac" .post the results of

```
usb-devices
``` locate the lines which indicate the modem and only those lines

```
grep usb /sys/bus/usb/devices/*/modalias | grep p14ac
```Noted:
from your switching data , the only reason for a fail reply  is your device is not listed
```

########################################################
# Huawei EC156

DefaultVendor= 0x12d1
DefaultProduct=0x1505

TargetVendor=  0x12d1
TargetProduct= 0x140b

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20
```a config with more than one target product looks like
```
]########################################################

# Huawei EC156

DefaultVendor= 0x12d1
DefaultProduct=0x1505

TargetVendor=  0x12d1
TargetProductList= 0x140b,14ac

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20
```do not update the config data files .until we can see a driver loading , hence the above request to switch the device as is , then post the requested data , may prove the Messagecontent is correct.

alexfish

---

### Post by manish671 on 2012-02-05
[FONT=Arial][SIZE=2]Thanks everybody.  I use Huawei UMG1831. It worked for me in just 2 steps

1 Following change in[/SIZE][/FONT][FONT=Arial][SIZE=2]**  /etc/usb_modeswitch.conf**[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]EnableLogging=1 # earlier it was 0[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]# Huawei UMG1831 [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]DefaultVendor=  0x12d1 [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]DefaultProduct= 0x1446 [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]TargetVendor=   0x12d1 [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]TargetProduct=  0x1404 [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]MessageContent="55534243123456780000000000000011060000000000000000000000000000"[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]2 [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]**sudo usb_modeswitch -c /etc/usb_modeswitch.conf**[/COLOR][/SIZE][/FONT]
 [FONT=Arial][SIZE=2]it said many things then bye. Immediately Network manager recognized the modem.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]After new Ubuntu installation Ubuntu automatically recognized the modem but then in 2-3 hours it went off and no luck. So I started using mobilepartner and it was working fine except that Software Center could not recognize the net-connection.  I was able to browse and do updates from terminal or package manager but not from Software center. 
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]One can find target product and messageContenet from here[/SIZE][/FONT]
[FONT=Arial][SIZE=2]a) [http://www.dd-wrt.com/wiki/index.php/3G_/_3.5G](http://www.dd-wrt.com/wiki/index.php/3G_/_3.5G) and[/SIZE][/FONT]
[FONT=Arial][SIZE=2]b) [/SIZE][/FONT]www.**sakis3g**.org/  [FONT=Arial][SIZE=2]download sakis3g then untar and look in folder sais3g/dependencies/usb-modeswitch-data/usbmodeswitch.d/   I tried to work with sakis but during installation it gave message that dependencies could not be met. [/SIZE][/FONT]

[FONT=Arial][SIZE=2]Again thanks everybody.[/SIZE][/FONT][SIZE=2]
[/SIZE]

---

### Post by axle88 on 2012-02-06
> **alexfish said:**
> from previous posts when you ran the usb_modeswitch the device is switching from "1505" to "14ac"

switch the device to be seen as "14ac" .post the results.


alexfish

Hey alexfish,

[B]I first switched the modem to product id 14ac. Below is the output from usb-devices. 
[/B]
T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ac Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

[B]I then ran the second command that you suggested. Below is the output.
[/B]
root@phidgetsbc:/# grep usb /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-0:1.0/modalias:usb:v1D6Bp0001d0301dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/1-1.5:1.0/modalias:usb:v12D1p14ACd0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.5:1.1/modalias:usb:v12D1p14ACd0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.5:1.2/modalias:usb:v12D1p14ACd0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.5:1.3/modalias:usb:v12D1p14ACd0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.5:1.4/modalias:usb:v12D1p14ACd0000dc00dsc00dp00ic08isc06ip50
/sys/bus/usb/devices/1-1.5:1.5/modalias:usb:v12D1p14ACd0000dc00dsc00dp00ic08isc06ip50
/sys/bus/usb/devices/1-1.7:1.0/modalias:usb:v06C2p0045d0903dc00dsc00dp00ic03isc00ip00
/sys/bus/usb/devices/1-1:1.0/modalias:usb:v0451p2077d0100dc09dsc00dp00ic09isc00ip00

---

### Post by barong234 on 2012-02-06
package you gonna need is modeswitch (for flip-flop USB Devices), wvdial (modem dialer). check your device by issuing command lsusb. if the device known as CD-ROM eject it, then issue anoter lsusb.
after that, configure your modeswitch and made dialer with wvdial.

---

### Post by manish671 on 2012-02-06
[SIZE=2]If it is Huawei E372 then target should be 12d1:1506
Thanks.
[/SIZE]

---

### Post by alexfish on 2012-02-07
Hi axle88

ok the device is switching but not sure if correct message content is been sent

but no driver is loading as seen in
```
T: Bus=01 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#= 5 Spd=12 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=14ac Rev=00.00
S: Manufacturer=Huawei Technologies
S: Product=HUAWEI Mobile
C: #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```the device lists as using the option module

can see if your kernel lists with this command
```
grep -i v12D1p14AC /lib/modules/`uname -r`/modules.alias
```so send the command with
```
sudo modprobe option
```if the device  not listed with the grep command , need to send another command```
echo "12d1 14ac" >/sys/bus/usb/drivers/option/module/drivers/usb-serial:option1/new_id
```then see if the driver is loading with the command
```
usb-devices
```the next problem may be modem manager picking the correct port , look as could be ttyUSB0 or ttyUSB1
if Network Manager will configure the device all is good, if not then can use ppp directly

see what happens in Network Manager first , if  met with failure , then can look  at configuring ppp
and will also need further info about this device, this will hopefully help others to get connected

wvdial should not be necessary for these types of  devices.

alexfish

---

### Post by alexfish on 2012-02-22
Have done some follow up info about these new Huawie devices in the a :How To

RE:[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 

May also apply to 11.10

**suggest reading all of first post + the links Regarding Huawei Mobile Partner + the Driver**

Also note any links to USB MODSWITCH FORUM , Some of these Devices have "TWO MODES" so require TWO different switching messages , one two use standard 3g and one two switch the device to 4g Mode or WiFi
if switching to 4g mode or WiFi  , presently  you will need the linux driver from Huawie  . RE **Huawei Mobile Partner + the Driver**

alexfish

---

### Post by hfdragon on 2012-09-05
Hello,

I have a new E372.. and also have problems to make it functionnal.

If the modem is plugged at boot time, it's working (switching) ok.

If not, it seems it's not switching to modem mode.

Anyone has a solution ? (Using Ubuntu 12.04 and USB 3.0)

Thanks ins advance for your answers.

---

