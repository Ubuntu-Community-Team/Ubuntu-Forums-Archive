---
title: "USB Broadband no longer working"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by LordVeovis on 2011-10-15
Today I finished my download of the new 11.10, and as always, I use the live environment to test for any major bugs before install.  I didn't see any that would stop me from installing, so I did.  Fresh install as of a couple hours ago.

In the Live environment, my USB broadband is recognized and works perfectly.  After install and reboot, it is not detected as a modem and therefore I cannot use it to connect to the Internet.  LSUSB shows the modem as: ```
Bus 002 Device 004: ID 1bbb:0000 T & A Mobile Phones
```

What do I need to to to have Ubuntu recognize it as a modem properly.  From my limited research, as I have to reboot to Live USB to use the modem, I have seen that it is likely not switching properly.  How can I get it to permanently?

---

### Post by zayustman on 2011-10-15
same problem here!

i have my modem Huawei E156G not detect too. it also happend when i install 11.04 natty, but then i stop using it and getting my self back to 10.10 Maverick coz it works fine. I hope there's any changes in 11.10 Oneiric, but it still the same problem

could someone help us to this bugs/issue??

thanks

---

### Post by iamnotthemessiah on 2011-10-15
same problem here, worked fine in 11.04
lsusb shows it as Huawei Technologies Co., Ltd. E620 USB Modem

ive found out that if i unplug the modem when rebooting/starting and plugging it in when i reach the login screen makes it appear in the network manager after 1-2 minutes after i log in and then i can manually start the connection...very annoying

---

### Post by alexfish on 2011-10-15
suggest using sakis3g
**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CCQQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=0ZWZTr2QJoKzhAemkojbAw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

sakis3g will expect the data file to be in the /etc/usb_modeswitch.d
can extract the file
```
sudo su
cd /etc/usb_modeswitch.d
tar xvf /usr/share/usb_modeswitch/configPack.tar
```

to setup the modem use the terminal 
```
sakis3g setup
```keep the system updated

alexfish

---

### Post by LordVeovis on 2011-10-15
> **alexfish said:**
> suggest using sakis3g
**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CCQQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=0ZWZTr2QJoKzhAemkojbAw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

sakis3g will expect the data file to be in the /etc/usb_modeswitch.d
can extract the file
```
sudo su
cd /etc/usb_modeswitch.d
tar xvf /usr/share/usb_modeswitch/configPack.tar
```

to setup the modem use the terminal 
```
sakis3g setup
```keep the system updated

alexfish

Will this get my modem to show in the network manager?  If this was just a 'use sakis3g to connect' that doesn't solve my problem and wont entirely work.  When I use Sakis3g I am able to connect, however the network manager doesn't think I am connected.  If I use the Software Manager it will not let me install new programs as Ubuntu is not aware that I am online.  At least that is what it seems like.

---

### Post by pdc on 2011-10-15
so for the first poster

the ID shows the device has not flipped    ....ie still seen as a virtual CD-ROM device;

> # [I]Alcatel X200/X200L/X060S
ATTRS{idVendor}=="1bbb", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'[/I]"

is the entry for this device in usb_modeswitch........saying .........if you identify this device, run usb_modeswitch ...........

as alex says, sakis will work as it has usb_modeswitch built-in;

........ so either one installs usb_modeswitch or the sakis I guess;

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

one gets these regressions as "advances" are made..............the early installers of new versions stumble on issues; so that the later installers have a smoother path..........

---

### Post by LordVeovis on 2011-10-15
> **pdc said:**
> so for the first poster

the ID shows the device has not flipped    ....ie still seen as a virtual CD-ROM device;



is the entry for this device in usb_modeswitch........saying .........if you identify this device, run usb_modeswitch ...........

as alex says, sakis will work as it has usb_modeswitch built-in;

........ so either one installs usb_modeswitch or the sakis I guess;

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

one gets these regressions as "advances" are made..............the early installers of new versions stumble on issues; so that the later installers have a smoother path..........

usb_modeswitch is already installed.  I want to know how to make it switch my device properly.  I know it is possible, I just don't know how to do that.

---

### Post by zayustman on 2011-10-15
My modem Huawei E156G but in lsusb detection looks like :
```
lsusb

Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem

```

---

### Post by pdc on 2011-10-15
to LordVeovis

Josh (usb_modeswitch) would suggest 

[http://www.draisberghof.de/usb_modeswitch/#trouble](http://www.draisberghof.de/usb_modeswitch/#trouble)

.......coz if usb_modeswitch is installed; and running;

.....it *should* flip your device

to zayustman:

can you copy and paste this command into a terminal and see if you get any ttyUSB0 or such response

> dmesg | grep tty

---

### Post by LordVeovis on 2011-10-16
In the log it looks like it thinks it is switching it... not sure it is tho.  Here is the output.

```
USB_ModeSwitch log from Sun Oct 16 15:18:06 2011

Using global config file: /etc/usb_modeswitch.conf

Raw args from udev: /2-7:1.0

Bus ID for device not given by udev.
 Trying to determine it from kernel name (2-7:1.0) ...

USB dir exists: /sys/bus/usb/devices/2-7

SCSI dir exists: /sys/bus/usb/devices/2-7
Warning: SCSI attribute "vendor" not readable.
Warning: SCSI attribute "model" not readable.
Warning: SCSI attribute "rev" not readable.
----------------
USB values from sysfs:
  idVendor	1bbb
  idProduct	f000
  manufacturer	USBModem
  product	HSPA Data Card
  serial	1234567890ABCDEF
  bNumConfigurations	1
----------------
bNumConfigurations is 1 - don't check for active configuration
Found packed config collection /usr/share/usb_modeswitch/configPack.tar.gz
Searching entries named: /usr/share/usb_modeswitch/1bbb:f000*
Searching overriding entries named: /etc/usb_modeswitch.d/1bbb:f000*
SCSI attributes not needed, moving on.

Using overriden config 1bbb:f000 from collection /etc/usb_modeswitch.d
! matched, now switching
 (running command: /usr/sbin/usb_modeswitch -I -W -D -c /etc/usb_modeswitch.d/1bbb:f000 -u -1 2>&1)

Verbose debug output of usb_modeswitch and libusb follows
(Note that some USB errors are expected in the process)
--------------------------------

Reading config file: /etc/usb_modeswitch.d/1bbb:f000

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.9 (C) Josua Dietze 2011
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x1bbb
DefaultProduct= 0xf000
TargetVendor=   0x1bbb
TargetProduct=  not set
TargetClass=    not set
TargetProductList="0000,0017"

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="55534243123456788000000080000606f50402527000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice disabled
Success check enabled, max. wait time 20 seconds
System integration mode enabled


Looking for target devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1bbb:f000
   found matching vendor ID
  searching devices, found USB ID 046d:09b8
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 1d6b:0002
 No devices in target mode or class found
Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1bbb:f000
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 046d:09b8
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 1d6b:0002
 Found devices in default mode, class or configuration (1)
Accessing device 005 on bus 002 ...
Skipping the check for the current configuration
Using endpoints 0x01 (out) and 0x81 (in)

USB description data (for identification)
-------------------------
Manufacturer: USBModem
     Product: HSPA Data Card
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01

Checking for mode switch (max. 20 times, once per second) ...
 Searching for target devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1bbb:0000
   found matching vendor ID
   found matching product ID from list
  searching devices, found USB ID 046d:09b8
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 1d6b:0002

Found target device, now opening

Found target device 006 on bus 002

Target device description data
-------------------------
Manufacturer: USBModem
     Product: HSPA Data Card
  Serial No.: 1234567890ABCDEF
-------------------------
 Found correct target device

Mode switch succeeded. Bye.

ok:no_data
--------------------------------
(end of usb_modeswitch output)

USB dir exists: /sys/bus/usb/devices/2-7
Driver module is "option", ID PATH is /sys/bus/usb-serial/drivers/option1
Now checking for newly created serial devices ...
 no new serial devices found
Device not in bind_list
Driver was loaded already
Trying to add ID to driver "option"
 ID added to driver; check for new devices in /dev
 still no new serial devices found
Checking for AVOID_RESET_QUIRK attribute
 AVOID_RESET_QUIRK activated

All done, exiting
```

After further reading of this it looks like it is switching, but failing to find the serial device afterwards.  Any thoughts?

---

### Post by pdc on 2011-10-16
hmmmmmmmmmmmm..

looks like it has switched

if you **copy and paste** this command 

> dmesg | grep tty

do you see any ttyUSB0 etc ..........that should confirm successful flip

(I suggest copy and paste as what seems like a line between dmesg and grep is what is called a pipe command; is SHIFT-\ and creates this pipe )

you can find it if you wish by looking for the \ key.............

if we are still struggling, we can get you to join the usb_modeswitch forum and ask for Josh's advice

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

---

### Post by LordVeovis on 2011-10-16
> **pdc said:**
> hmmmmmmmmmmmm..

looks like it has switched

if you **copy and paste** this command 



do you see any ttyUSB0 etc ..........that should confirm successful flip

(I suggest copy and paste as what seems like a line between dmesg and grep is what is called a pipe command; is SHIFT-\ and creates this pipe )

you can find it if you wish by looking for the \ key.............

if we are still struggling, we can get you to join the usb_modeswitch forum and ask for Josh's advice

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Thanks for your help so far.  It is showing up in dmesg ```
[ 6249.388531] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB0
[ 6249.388879] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB1
[ 6249.389836] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB2

```
 not sure why it will not show up in the network manager then.

EDIT: Wait let me make sure it is not saki3g that is making those show up...
EDIT: No just removing and reconnecting the device is getting the above dmesg

---

### Post by alexfish on 2011-10-16
> **LordVeovis said:**
> Will this get my modem to show in the network manager? If this was just a 'use sakis3g to connect' that doesn't solve my problem and wont entirely work. When I use Sakis3g I am able to connect, however the network manager doesn't think I am connected. If I use the Software Manager it will not let me install new programs as Ubuntu is not aware that I am online. At least that is what it seems like.
 
looking at other posts indicates there is further debuging required
 
for now can try this code and see if sofware centre will work
 
```
 
sudo su
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces


```
 
will now look at all info, not sure if this is a udev  or modem-manager problem , 
 
alexfish

---

### Post by pdc on 2011-10-16
> *not sure why it will not show up in the network manager then*.

help us understand what you mean by that please

.........I guess I am assuming you have set up an entry already for your country and provider network..............

---

### Post by alexfish on 2011-10-16
> **LordVeovis said:**
> Thanks for your help so far.  It is showing up in dmesg ```
[ 6249.388531] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB0
[ 6249.388879] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB1
[ 6249.389836] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB2

``` not sure why it will not show up in the network manager then.

EDIT: Wait let me make sure it is not saki3g that is making those show up...
EDIT: No just removing and reconnecting the device is getting the above dmesg
hi

need some info 
 
do not run sakis3g prior to this

post the results of these commands from the terminal 

```
udevadm info --export-db | grep DEVLINKS=/dev/scd*
``````
usb-devices
``` locate the lines which indicate the device and post only those lines

```
ls -al /dev/serial/by-id
``````
nm-tool
```regards

alexfish

---

### Post by LordVeovis on 2011-10-16
> **pdc said:**
> help us understand what you mean by that please

.........I guess I am assuming you have set up an entry already for your country and provider network..............

Using the Network Manager Applet in the top right corner does not show the modem nor does it even show the ability to enable or disable mobile broadband.  This is like any other computer that does not have a mobile broadband card connected.  It should show the card, and the ability to enable / disable it, upon connecting one.  I have verified this on other versions of ubuntu as well.  It did previously work with 11.04 and it worked in the Live Environment for 11.10.

I installed 11.10 with the Broadband connected, so when it booted up there was already an entry with all of the correct mobile broadband information there.  I have removed and re-added the info as well, no change.

---

### Post by LordVeovis on 2011-10-16
> **alexfish said:**
> hi

need some info 
 
do not run sakis3g prior to this

post the results of these commands from the terminal 
(...)
regards

alexfish

udevadm:```
E: DEVLINKS=/dev/scd0 /dev/disk/by-id/ata-PIONEER_DVDRW_DR-TD08HB /dev/disk/by-path/pci-0000:00:1f.2-scsi-4:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw
```
usb-devices:
```
T:  Bus=02 Lev=01 Prnt=01 Port=06 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=0000 Rev=00.00
S:  Manufacturer=USBModem
S:  Product=HSPA Data Card
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
```
ls -al /dev/serial/by-id:
```
total 0
drwxr-xr-x 2 root root 100 2011-10-16 21:44 .
drwxr-xr-x 4 root root  80 2011-10-16 21:44 ..
lrwxrwxrwx 1 root root  13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2
```
nm-tool
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

Thank you for your time so far :)  I am very thankful.

---

### Post by alexfish on 2011-10-16
hi LordVeovis

the modem is configuring
but need to rule out if a problem with udev

have prepared this script / this will trace the udev /dev/serial/by-id

copy and paste this code into gedit (text editor)
```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"

proc udevadm-tty {bit} {
    if { [catch {set udevadm_tty [exec udevadm info -a path -n /dev/$bit]} fid] } {
        puts $fid
        return
    } else {
        puts $udevadm_tty\n
        }
        unset udevadm_tty
    return
}
set dolist 1
#exec ls -l /dev/serial/by-id]
    if { [catch {set List [exec ls -l /dev/serial/by-id]} fid] } {
        puts "$fid\n"
        return
    } else {
        puts "/dev/serial/by-id:\n\n$List\n"
        }
    #########################
    # parse device : ttys
    if {$dolist == 1} {
        set len [llength $List]
    foreach bit $List {
        set usb [string first {usb} $bit]
            if {$usb > -1} {
                puts "--------- Udevadm device info-------\n\n"
                puts "--$bit: "
            }

        set tty [string first {tty} $bit]
            if {$tty > -1} {
            set bit [string range $bit $tty end]
            set udevtty "/dev/$bit"
            puts "$udevtty\n"
## for each tty get the udev info
            udevadm-tty $bit

            }
    }
}
```
save it in your home directory as "udevadm-usbserial-tty.tcl", then from the terminal 

```
tclsh `pwd`/udev-tcl/udevadm-usbserial-tty.tcl
```can also try killing modem manager see if the device will register under Network Manager
```
sudo killall modem-manager
```post the results

regards alexfish

---

### Post by LordVeovis on 2011-10-16
> **alexfish said:**
> hi LordVeovis
(...)
can also try killing modem manager see if the device will register under Network Manager
```
sudo killall modem-manager
```post the results

regards alexfish

```
/dev/serial/by-id:

total 0
lrwxrwxrwx 1 root root 13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-10-16 21:44 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2

--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if00-port0: 
/dev/ttyUSB0


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.0':
    KERNELS=="2-7:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7':
    KERNELS=="2-7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="390494"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="7"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="85"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if01-port0: 
/dev/ttyUSB1


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.1/ttyUSB1/tty/ttyUSB1':
    KERNEL=="ttyUSB1"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.1/ttyUSB1':
    KERNELS=="ttyUSB1"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.1':
    KERNELS=="2-7:1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7':
    KERNELS=="2-7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="390494"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="7"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="85"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if03-port0: 
/dev/ttyUSB2


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.3/ttyUSB2/tty/ttyUSB2':
    KERNEL=="ttyUSB2"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.3/ttyUSB2':
    KERNELS=="ttyUSB2"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.3':
    KERNELS=="2-7:1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7':
    KERNELS=="2-7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="390494"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="7"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="85"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

I also tried to kill the modem-manager, it did not help.  I know the above is more info than is needed, but I did not want to cut something needed out.

---

### Post by iamnotthemessiah on 2011-10-16
adding 'nmcli nm wwan on' to the startup apps solved the problem for me, completely, procedure is as follows:
add 'nmcli nm wwan on' to startup apps
reboot
click on 'enable mobile broadband' in the nm indicator
edit my connection and enable 'connect automaticly'
rebooting again and im connected when the desktop is loaded :)

---

### Post by pdc on 2011-10-17
well done;

what led you to 

> adding 'nmcli nm wwan on' to the startup apps solved the problem for me

---

### Post by LordVeovis on 2011-10-17
> **iamnotthemessiah said:**
> adding 'nmcli nm wwan on' to the startup apps solved the problem for me, completely, procedure is as follows:
add 'nmcli nm wwan on' to startup apps
reboot
click on 'enable mobile broadband' in the nm indicator
edit my connection and enable 'connect automaticly'
rebooting again and im connected when the desktop is loaded :)

I tried your suggestion and it did not work.  Thanks tho :)

---

### Post by iamnotthemessiah on 2011-10-17
thats a shame lord, after multiple reboots i can confirm that this works 100% here...u added the command without the '' didnt you? 
what happens if u, when the mobile broadband entry is not present in the nm applet menu, put "nmcli nm wwan on" in a terminal? does it appear in the menu after a few seconds?

---

### Post by LordVeovis on 2011-10-17
> **iamnotthemessiah said:**
> thats a shame lord, after multiple reboots i can confirm that this works 100% here...u added the command without the '' didnt you? 
what happens if u, when the mobile broadband entry is not present in the nm applet menu, put "nmcli nm wwan on" in a terminal? does it appear in the menu after a few seconds?

No it doesn't.  I did not have quotes in my line either.  The command executes fine, does not print anything in the terminal window, returns me to a prompt and nothing changes.  I tried executing it as root (sudo) as well, same results.

I know the modem works as I can still boot to the live CD and connect or use Saki3g and connect.  As pointed out before Saki3g is not acceptable tho as Ubuntu does not realize it is online.

---

### Post by alexfish on 2011-10-18
Hi LordVeovis

the udev seems to be ok IE the correct bits are there for modem managers to pickup

still not sure what the problem is

can go to this old thread:**Re: Natty, known bugs, fixes and work arounds post** :  #[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

first look at the :" testing modem-manager : need to download mm-test.py"

use sakis3g for the download (hope the wget is on the system) if not can use the url in the web page and save file to home directory, then python ./path to 

run the test see what it shows up

also look at how to debug modem manager and network manager

can also suggest , if all else is failing , try reinstall modem-manager and possible network manager, 

regards

alexfish

---

### Post by zayustman on 2011-10-20
My dmesg | grep tty looks like this :
 ```

[    0.000000] console [tty0] enabled
[   42.673991] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[   42.674068] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[   53.139204] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   58.708070] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   58.877504] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[   58.877633] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[   68.130964] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   74.883177] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   75.052777] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[   75.052978] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[   84.122085] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   91.066154] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   91.235357] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[   91.235536] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  102.112144] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  107.241349] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  107.418585] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  107.418724] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  117.103849] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  123.424375] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  123.593805] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  123.594263] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  133.095063] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  139.611457] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  139.783376] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  139.783884] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1

```

looks like modem continue disconnect or disable by network manager

---

### Post by zayustman on 2011-10-20
there's also something strange happen when I plug my modem..random freeze occurs after i'm typing 5 word..every things freeze for 5 second and then getting back! but when i unplug modem..every things normal again!! it never happen on maverick. 

could someone explain this?

thx

---

### Post by lphilp00 on 2011-10-20
I've been getting this problem too since I upgraded to 11.10. The core of it seems to be an error in the option driver. If you have a look at your full dmesg output (without the |grep tty) you'll see a lot of errors like:

"option_instat_callback: error -108".

There are a few old bugs over at launchpad that claim to have fixed this problem in earlier kernel versions. But either they didn't fix it, or there has been a regression on the way to the version 3.0 kernel. I'm seeing the freezing too, with my machine not even accepting mouse input for around 5 seconds at a time. I have a Huawei E160 broadband modem.

I have found a workaround though.

Rather than using Network Manager, I tried to connect to my provider using pppd and pon as per the instructions contained here: 

[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

Try following these - and don't worry that these are for a specific Irish mobile broadband provider - you won't actually be using pon to connect. I found that if I followed these instructions and tried to connect using "sudo pon" at the end, I got an error from pon, but my modem started working through the Network Manager Applet again.

You might have to run "sudo pon" a couple of times, but once you get the SIG_HUP error and a message about ttyUSB0 looping, your Network Manager Applet should work again. 

I'm not sure what's going on here, but I suspect that the "AT" commands in /etc/chatscripts/pap might be helping in some way. What I've noticed is that when you check dmesg after it starts working again, the device is now using ttyUSB1 and ttyUSB2 instead of ttyUSB0 and ttyUSB1. That seems to get it going again. 

Obviously this is just a workaround, but hopefully it will give somebody who knows more than me a clue as to where the problem lies.

---

### Post by LordVeovis on 2011-10-21
> **alexfish said:**
> Hi LordVeovis

the udev seems to be ok IE the correct bits are there for modem managers to pickup

still not sure what the problem is

can go to this old thread:**Re: Natty, known bugs, fixes and work arounds post** :  #[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

first look at the :" testing modem-manager : need to download mm-test.py"

use sakis3g for the download (hope the wget is on the system) if not can use the url in the web page and save file to home directory, then python ./path to 

run the test see what it shows up

also look at how to debug modem manager and network manager

can also suggest , if all else is failing , try reinstall modem-manager and possible network manager, 

regards

alexfish

Sorry for the delay, was diving the great barrier reef.

I ran the script and recieved a 'No modems found' reply then back to the command prompt.

---

### Post by zayustman on 2011-10-21
> **lphilp00 said:**
> I've been getting this problem too since I upgraded to 11.10. The core of it seems to be an error in the option driver. If you have a look at your full dmesg output (without the |grep tty) you'll see a lot of errors like:

"option_instat_callback: error -108".

There are a few old bugs over at launchpad that claim to have fixed this problem in earlier kernel versions. But either they didn't fix it, or there has been a regression on the way to the version 3.0 kernel. I'm seeing the freezing too, with my machine not even accepting mouse input for around 5 seconds at a time. I have a Huawei E160 broadband modem.

I have found a workaround though.

Rather than using Network Manager, I tried to connect to my provider using pppd and pon as per the instructions contained here: 

[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

Try following these - and don't worry that these are for a specific Irish mobile broadband provider - you won't actually be using pon to connect. I found that if I followed these instructions and tried to connect using "sudo pon" at the end, I got an error from pon, but my modem started working through the Network Manager Applet again.

You might have to run "sudo pon" a couple of times, but once you get the SIG_HUP error and a message about ttyUSB0 looping, your Network Manager Applet should work again. 

I'm not sure what's going on here, but I suspect that the "AT" commands in /etc/chatscripts/pap might be helping in some way. What I've noticed is that when you check dmesg after it starts working again, the device is now using ttyUSB1 and ttyUSB2 instead of ttyUSB0 and ttyUSB1. That seems to get it going again. 

Obviously this is just a workaround, but hopefully it will give somebody who knows more than me a clue as to where the problem lies.

are the freeze still there?? it's really annoying with the freeze things. hope new kernell will fix it lol

---

### Post by alexfish on 2011-10-21
> **LordVeovis said:**
> Sorry for the delay, was diving the great barrier reef.

I ran the script and recieved a 'No modems found' reply then back to the command prompt.

only thing notice in the post is this [FONT=monospace]

[/FONT]> looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-7/2-7:1.0/ttyUSB0':     KERNELS=="ttyUSB0"     SUBSYSTEMS=="usb-serial"     DRIVERS=="option1"     ATTRS{port_number}=="0" I could be wrong, on 11.04 my modems usually show up in "usb1"  ,have done configuration scripts in the past which only look at this directory, so am asking the question ::is modem-manager only looking at usb1 , personally I don't know, could possibly look to modem-manager to find out.. 

did know of having a problem of connecting with network manager with some laptops (though did not check at the time which usb directory the device resided)
but could connect with ppp and sakis3g, is your system a lapotop or desktop?

[FONT=monospace]the problem is this "software center not working" re network manager needs to be connect , have never found this to be an issue when using other methods of connecting , the below command should have worked. if sofware center relies on NM been connected
[/FONT]```
sudo su
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces

```so possible need to look at this later or possible look through the forum if others are having problems with the software center

can you post the full results of " usb-devices" command

```
usb-devices
```and if laptop howmany usb ports does it have and also  post which sides the ports reside on ,rightside leftside,and rear,

can you also run the script > udevadm-usbserial-tty.tclwith the live cd and post the results , and can confirm the sofware center works in the live cd.

regards

alexfish

---

### Post by lphilp00 on 2011-10-22
> **zayustman said:**
> are the freeze still there?? it's really annoying with the freeze things. hope new kernell will fix it lol

No. The freezes are gone once the modem starts working again. It's well worth trying this as a workaround. Once you have it set up, you just have to run "sudo pon" and then you can work normally.

---

### Post by jtarin on 2011-10-22
I needed to add the module usbserial to my loaded modules before my ZTE 180 would show in NM. Now it connects straight away.```
sudo modprobe usbserial
```

---

### Post by LordVeovis on 2011-10-23
@Alexfish

I am using a laptop with 4 USB ports.  I have tried the modem in at least 3 of them, possibly all 4.  I will post the results of the script from the Live CD, but until I reboot and edit it in, here is the full

usb-devices:```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0c9a Rev=01.00
S:  Manufacturer=HTC
S:  Product=Android Phone
S:  SerialNumber=HT038HF00208
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=256mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=42 Prot=01 Driver=(none)

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=046d ProdID=09b8 Rev=60.51
S:  Product=HP Webcam 
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=01 Prnt=01 Port=06 Cnt=03 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=0000 Rev=00.00
S:  Manufacturer=USBModem
S:  Product=HSPA Data Card
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

Live CD script results:```

/dev/serial/by-id:

total 0
lrwxrwxrwx 1 root root 13 2011-10-24 13:21 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-10-24 13:21 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-10-24 13:21 usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2

--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if00-port0: 
/dev/ttyUSB0


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0':
    KERNELS=="2-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="9326"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="123"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if01-port0: 
/dev/ttyUSB1


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/ttyUSB1/tty/ttyUSB1':
    KERNEL=="ttyUSB1"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/ttyUSB1':
    KERNELS=="ttyUSB1"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1':
    KERNELS=="2-2:1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="9326"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="123"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


--------- Udevadm device info-------


--usb-USBModem_HSPA_Data_Card_1234567890ABCDEF-if03-port0: 
/dev/ttyUSB2


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.3/ttyUSB2/tty/ttyUSB2':
    KERNEL=="ttyUSB2"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.3/ttyUSB2':
    KERNELS=="ttyUSB2"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.3':
    KERNELS=="2-2:1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceNumber}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USBModem Configuration"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="9326"
    ATTRS{idVendor}=="1bbb"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x10"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="USBModem"
    ATTRS{product}=="HSPA Data Card"
    ATTRS{serial}=="1234567890ABCDEF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="123"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-12-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30f4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

---

### Post by jtarin on 2011-10-24
My keeps disconnecting and I think this line is the culprit.
```
If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 **_Driver=usb-storage_**
```Now to keep that driver from loading and test my theory.

---

### Post by alexfish on 2011-10-25
@LordVeovis

don't see anything of the obvious. from the udev

now time to take a look at modem-manager activities , use this command
```
cat /var/log/syslog.1 | grep modem-manager
``` hope this is the correct file for your system
if not can open up logfile viewer to find file

test on live cd and also on the installed

Added:
 can test the script " mm-test.py" on the live cd

alexfish

---

### Post by LordVeovis on 2011-11-02
> **alexfish said:**
> @LordVeovis

don't see anything of the obvious. from the udev

now time to take a look at modem-manager activities , use this command
```
cat /var/log/syslog.1 | grep modem-manager
``` hope this is the correct file for your system
if not can open up logfile viewer to find file

test on live cd and also on the installed

Added:
 can test the script " mm-test.py" on the live cd

alexfish

I am not able to work on this anymore as I have now gone back to the US and no longer am using a USB modem.  I no longer am the owner of the modem either.  Thanks tho.

---

### Post by xlearner on 2011-11-28
@Alexfish,

I recently came across this thread. I found this very interesting. Even I am going through somewhat similar problem. 

I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. I created a new mobile broadband connection. When I try to plug-in the device, it is not showing a new network connection.

So on looking at another thread, I downloaded Sakis 3G utility. Unfortunately, it did not work as well. It is failing after when "switching to the modem". I was getting the error message, "Failed to Connect".
Then I looked into 'more options'. There when I click on 'Only switch modem' option, it returns successfully with the message "Modem switched to 1c9e:f000". But when I click on 'Only setup modem (Switch + Load Module + Setup tty)', it fails with the message "Failed to setup modem". I posted this message on this thread as well: [http://ubuntuforums.org/showthread.php?t=1695102&highlight=3g+modem](http://ubuntuforums.org/showthread.php?t=1695102&highlight=3g+modem)


I was wondering if I update to the latest ubuntu version, if it solve my problem? So can anyone help me or give me some advice?

Thanks!

---

### Post by alexfish on 2011-11-28
> **xlearner said:**
> @Alexfish,

I recently came across this thread. I found this very interesting. Even I am going through somewhat similar problem. 

I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. I created a new mobile broadband connection. When I try to plug-in the device, it is not showing a new network connection.

So on looking at another thread, I downloaded Sakis 3G utility. Unfortunately, it did not work as well. It is failing after when "switching to the modem". I was getting the error message, "Failed to Connect".
Then I looked into 'more options'. There when I click on 'Only switch modem' option, it returns successfully with the message "Modem switched to 1c9e:f000". But when I click on 'Only setup modem (Switch + Load Module + Setup tty)', it fails with the message "Failed to setup modem". I posted this message on this thread as well: [http://ubuntuforums.org/showthread.php?t=1695102&highlight=3g+modem](http://ubuntuforums.org/showthread.php?t=1695102&highlight=3g+modem)




I was wondering if I update to the latest ubuntu version, if it solve my problem? So can anyone help me or give me some advice?

Thanks!
hi

can post details of this command from the terminal
```
usb-devices
```

alexfish

---

