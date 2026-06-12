---
title: "Configuring Huawei E173 on Natty"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-04-28
Where can I find details of how to set up a Huawei E173 on Natty?

The network interface's status icon shows first "waiting for authorization" then it goes to "not connected"

The modem hardware is showing up when it is plugged in:
```

$ ls -la /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-04-28 19:18 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2011-04-28 19:18 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 20$ lsusb|grep Huawei

Bus 001 Device 013: ID 12d1:1436 Huawei Technologies Co., Ltd. 
11-04-28 19:18 /dev/ttyUSB2

```

What needs to be done to get it working?

---

### Post by Lars Noodén on 2011-04-30
Except for a brief time, once so far, the network interface icon always shows the modem being 'not connected'  The modem connects ok in OS X. In kubuntu, it gets as far as 'preparing to connect' and the drops back to being 'not connected'

---

### Post by alexfish on 2011-04-30
Hi

I have not upgraded to Natty so not sure if all commands to list the device will work

but can start by looking up the device with the usb-devices command
```
usb-devices
```post the results

of note from the listings
> [FONT=monospace]$ ls -la /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-04-28 19:18 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2011-04-28 19:18 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 20$ lsusb|grep Huawei

Bus 001 Device 013: ID 12d1:1436 Huawei Technologies Co., Ltd. 
11-04-28 19:18 /dev/ttyUSB2[/FONT] Need to ask if at any stage, did you disconnect the device whilst issuing the commands

can see if the nm-tool command works
```
nm-tool
```only post the results applicable to the device

alexfish

---

### Post by Lars Noodén on 2011-04-30
$ usb-devices
...
 T:  Bus=02 Lev=03 Prnt=05 Port=03 Cnt=02 Dev#= 34 Spd=480 MxCh= 0
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
...

$ lsusb
...
Bus 002 Device 036: ID 12d1:1436 Huawei Technologies Co., Ltd. 
...

$ nm-tool
...
- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:
...

---

### Post by alexfish on 2011-04-30
Hi

everything seem ok at kernel level (with exeption of other ports . it seems to have alternate interface ) does it have wifi connection abilities.
looks as if Network Manager is selecting the correct port 
I am assuming the Network Manager details are correct (double check ) 
if the details are correct, then so not sure  problem with modem-manager or the pppd

can monitor the syslog to see if any thing shows (with reference to the message "waiting for authorization"). can check the the authentication (in NM ,PPP settings)
can post the results of
```
egrep -v '#|^ *$' /etc/ppp/options
```can suggest installing Sakis3g 

[http://www.sakis3g.org/](http://www.sakis3g.org/)

see what happens

alexfish

---

### Post by Lars Noodén on 2011-04-30
$ egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
lcp-echo-interval 30
lcp-echo-failure 4
noipx

---

### Post by Lars Noodén on 2011-04-30
There's a lot happening in syslog when the networking manager tries to connect, about 100 lines worth.

```

Apr 30 18:23:17 kubuntu NetworkManager[890]: <warn> GSM connection failed: (32) Unknown registration status response

```

---

### Post by alexfish on 2011-04-30
Hi

going to try and connect this device  via the terminal, but first require some info about the modem 

allow time for the system to settle (let modem manager finish it's probing)

open up a terminal and enter the follow code 

```
tr -s "\n" < /dev/ttyUSB0
```

open up the second terminal and enter the following commands , the results should appear in the first terminal

```
echo -e "ATZ\r" > /dev/ttyUSB0

echo -e "AT+CREG?\r" > /dev/ttyUSB0

echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0

echo -e "AT+COPS=0,2\r" > /dev/ttyUSB0

echo -e "AT+COPS?\r" > /dev/ttyUSB0

```post the results from the first terminal

alexfish

---

### Post by Lars Noodén on 2011-04-30
> **alexfish said:**
> post the results from the first terminal

I added  **echo -e "ATI\r" > /dev/ttyUSB0**

```

OK
AT+CREG?
ERROR
AT+CGDCONT?
ERROR
AT+COPS=0,2
ERROR
ATI
Manufacturer: huawei
Model: E173
Revision: 11.126.83.00.00
IMEI: 352215049114778
+GCAP: +CGSM,+DS,+ES


```

It's been a long time since I worked with modems.

---

### Post by alexfish on 2011-04-30
Does the modem have a pin code

check the sim pin stat

```
echo -e "AT+CPIN?\r" > /dev/ttyUSB1
```

---

### Post by Lars Noodén on 2011-04-30
> **alexfish said:**
> Does the modem have a pin code

check the sim pin stat

```
echo -e "AT+CPIN?\r" > /dev/ttyUSB1
```

No response initially, then 

bash: /dev/ttyUSB0: Device or resource busy

---

### Post by alexfish on 2011-04-30
Possible modem manager is still accessing the device or not releasing the device

open up first terminal and enter the following code
```
tail -f /var/log/syslog
```open up the second terminal then
```
sudo killall modem-manager
```wait until modem- manager completes its probing (note from first terinal)

in second terminal
```
tr -s "\n" < /dev/ttyUSB0
```open up third terminal and enter
```
echo -e "AT+CPIN?\r" > /dev/ttyUSB0
```

also note if anything of the obvious appears in the syslog (first terminal)

alexfish

---

### Post by Lars Noodén on 2011-04-30
> **alexfish said:**
> 
also note if anything of the obvious appears in the syslog (first terminal)

Apr 30 19:50:45 kubuntu kernel: [  601.137520] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

---

### Post by Lars Noodén on 2011-04-30
echo -e "AT+CSQ\r" > /dev/ttyUSB0

OK

+CSQ: 8,99


echo -e "ATD*99#\r" > /dev/ttyUSB0

OK

CONNECT 7200000

---

### Post by alexfish on 2011-05-01
you seem to be doing fine with the modem commands , 

the modem responds to the dial command

so can suggest trying ppp directly , to configure ppp try

```
sudo pppconfig
```There is one thing of note as regards  Huawie E173 , have been to usb_modeswitch site
and the ID's show up different to yours , can you remember if the Ids in Natty are same as earlier versions of Ubuntu ,

The "CONNECT 7200000" shows this to be a fast modem , was the option driver loading in  earlier versions of ubuntu for this device , or possible doing a modprobe <driver module> , reason 
> [drm:drm_mode_getfb] *ERROR* invalid framebuffer idcan also check though the log files as to the originator of the error IE : modem-manager


ADDED: the signal strength of +CSQ: 8,99 : 8 is very low , try moving the modem to at least 10+ : even 15 . 8 will almost surely produce errors , especially if it operates at   7200000 .
this is twice as fast as a standard 3g connection

had been on a other thread with a reference to this device, the usb_modeswitch.d files

> ################################################## #####
# Huawei E173s

DefaultVendor= 0x12d1
DefaultProduct=0x1c0b

TargetVendor= 0x12d1
TargetProduct= 0x1c05

MessageContent="5553424312345678000000000000001106 2000000100000000000000000000"

CheckSuccess=20

alexfish

---

### Post by alexfish on 2011-05-01
It would interesting to find out the modalias for this device
the modalias may indicate the type of driver  for certain usb devices

the file normally found in : /sys/bus/usb/devices/usb1/1:*/1:*/modalias

alexfish

---

### Post by Lars Noodén on 2011-05-01
```

$ ls /sys/bus/usb/devices/
1-0:1.0  1-1.1:1.0    1-1.1.3:1.2  1-1.2:1.1  1-1.3:1.1  1-2:1.0  2-1        2-1.2        2-1.2.4      2-1.2.4:1.3  3-0:1.0  usb3
1-1      1-1.1.3      1-1.1.3:1.3  1-1.2:1.2  1-1.3:1.2  1-2:1.1  2-1.1      2-1.2.1      2-1.2.4:1.0  2-1.2.4:1.4  4-0:1.0  usb4
1-1.1    1-1.1.3:1.0  1-1.2        1-1.3      1-1.3:1.3  1-2:1.2  2-1:1.0    2-1.2:1.0    2-1.2.4:1.1  2-1.2.4:1.5  usb1
1-1:1.0  1-1.1.3:1.1  1-1.2:1.0    1-1.3:1.0  1-2        2-0:1.0  2-1.1:1.0  2-1.2.1:1.0  2-1.2.4:1.2  2-1.2.4:1.6  usb2

```

---

### Post by Lars Noodén on 2011-05-01
> **alexfish said:**
> It would interesting to find out the modalias for this device
the modalias may indicate the type of driver  for certain usb devices

the file normally found in : /sys/bus/usb/devices/usb1/1:*/1:*/modalias

alexfish

```

$ cat /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2.4/2-1.2.4:1.6/host10/target10:0:0/10:0:0:0/modalias
scsi:t-0x00

```

---

### Post by alexfish on 2011-05-01
Hi

have written a tcl script , need to see other info , not sure if lsub -v will give all the info

this device mystifies me ,
> I: If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=(none)
I: If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)

if by reason 
"Cls=02(commc)" and "Cls=0a(data )"

these would indicate another device type interface similar to a wifi or usb net 
the usb net may be similar to ethernet interface

the other reason is the listed speed of the device , most modems which have greater speeds usually have an alternate usb net interface

so not sure if the option driver is suitable for this device / option driver will not allocate a usb net type interface , 

any how can try this script and see what info it shows
```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"
# for device 12d1:1436
    ################################
    # NO PROCS
    #   Set ids and paths
    global exist
    set exist            0
    set Vendor "12d1"
    set Product "1436"
    set Device "$Vendor:$Product"     
    set dir "/sys/bus/usb/devices/"
    puts "Searching Dir $dir"
    set devices [ glob -nocomplain -directory $dir *]
    ###############################
    # check vendor exist infile + check ids
    #-*
    foreach device $devices {
        #puts $device
        set count 0
        set more [ glob -nocomplain -directory $device *]
        #--*
        foreach mdevice $more {
            incr count
            set checkvendor [string first {idVendor} $mdevice]
            #---*
            if {$checkvendor > -1 } {
                set vend [open $mdevice r]
                set idVendor [read $vend]
                set idVendor [string trim $idVendor]
                close $vend
                #----*                                
                if {$idVendor == $Vendor } {
                    set prodpath "$device/idProduct"
                    set prod [open $prodpath r]
                    set idProduct [read $prod]
                    set idProduct [string trim $idProduct]
                    set deviceVend "$idVendor:$idProduct"
                    close $prod
                    #-----*
                    if {$Device == $deviceVend} {
                        set exist             1
                        set wild [string trim $device $dir]
                        set dirs_inf [ glob -nocomplain -directory $dir $wild*]
                        puts "Start Stats"
                        foreach inf $dirs_inf {
                            set dirs_inf [ glob -nocomplain -directory $inf *]
                            foreach infos $dirs_inf {
###################################################################
# File Quirks just incase
                            set avoid 1
                            set subsystem [string first subsystem $infos]
                            set remove [string first remove $infos]
                            set power [string first power $infos]
                            set driver [string first driver $infos]
                            set descriptors [string first descriptors $infos]
                             if {$descriptors > -1} {set avoid 0}
                             if {$driver > -1} {set avoid 0}
                             if {$power > -1 } {set avoid 0}
                             if {$subsystem > -1 } {set avoid 0}
                             if {$remove > -1 } {set avoid 0}
####################################################################
# get the bits
                            
                             if {$avoid} {
                                set isfile [file isdirectory $infos]
                             if {! $isfile } {
                                set devinfo [open $infos r]
                                set a [read $devinfo]
                                set b [split $a "\n"]
                                puts "------- $infos --------"
                            foreach bit $b {puts "  $bit"}
                            close $devinfo}
                            }
                            
##############################################################
                            }
                        }                        
                    }
                }
            }
        }
    }
#-----*
############################################
# if exist then get the bits
############################################
# just get out
if {$exist} {
    puts "DONE"
    } else {
    puts "Device $Device does not exist"
    }
#############################################
```
copy and paste into gedit . save it + give it a name . then sh from the terminal

alexfish

---

### Post by Lars Noodén on 2011-05-02
```

Searching Dir /sys/bus/usb/devices/
Start Stats
------- /sys/bus/usb/devices/2-1.2.4/uevent --------
  MAJOR=189
  MINOR=133
  DEVNAME=bus/usb/002/006
  DEVTYPE=usb_device
  DRIVER=usb
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  BUSNUM=002
  DEVNUM=006
  
------- /sys/bus/usb/devices/2-1.2.4/dev --------
  189:133
  
------- /sys/bus/usb/devices/2-1.2.4/configuration --------
  Huawei   Configuration
  
------- /sys/bus/usb/devices/2-1.2.4/bNumInterfaces --------
   7
  
------- /sys/bus/usb/devices/2-1.2.4/bConfigurationValue --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4/bmAttributes --------
  e0
  
------- /sys/bus/usb/devices/2-1.2.4/bMaxPower --------
  500mA
  
------- /sys/bus/usb/devices/2-1.2.4/urbnum --------
  22228
  
------- /sys/bus/usb/devices/2-1.2.4/idVendor --------
  12d1
  
------- /sys/bus/usb/devices/2-1.2.4/idProduct --------
  1436
  
------- /sys/bus/usb/devices/2-1.2.4/bcdDevice --------
  0000
  
------- /sys/bus/usb/devices/2-1.2.4/bDeviceClass --------
  ef
  
------- /sys/bus/usb/devices/2-1.2.4/bDeviceSubClass --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4/bDeviceProtocol --------
  01
  
------- /sys/bus/usb/devices/2-1.2.4/bNumConfigurations --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4/bMaxPacketSize0 --------
  64
  
------- /sys/bus/usb/devices/2-1.2.4/speed --------
  480
  
------- /sys/bus/usb/devices/2-1.2.4/busnum --------
  2
  
------- /sys/bus/usb/devices/2-1.2.4/devnum --------
  6
  
------- /sys/bus/usb/devices/2-1.2.4/devpath --------
  1.2.4
  
------- /sys/bus/usb/devices/2-1.2.4/version --------
   2.00
  
------- /sys/bus/usb/devices/2-1.2.4/maxchild --------
  0
  
------- /sys/bus/usb/devices/2-1.2.4/quirks --------
  0x0
  
------- /sys/bus/usb/devices/2-1.2.4/avoid_reset_quirk --------
  0
  
------- /sys/bus/usb/devices/2-1.2.4/authorized --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4/manufacturer --------
  HUAWEI Technology
  
------- /sys/bus/usb/devices/2-1.2.4/product --------
  HUAWEI Mobile
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/uevent --------
  DEVTYPE=usb_interface
  DRIVER=option
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=255/255/255
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bInterfaceNumber --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bNumEndpoints --------
  03
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bInterfaceClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bInterfaceSubClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/bInterfaceProtocol --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.0/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/uevent --------
  DEVTYPE=usb_interface
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=2/6/255
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01ic02isc06ipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bInterfaceNumber --------
  01
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bNumEndpoints --------
  01
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bInterfaceClass --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bInterfaceSubClass --------
  06
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/bInterfaceProtocol --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01ic02isc06ipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/iad_bFirstInterface --------
  01
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/iad_bInterfaceCount --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/iad_bFunctionClass --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/iad_bFunctionSubClass --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.1/iad_bFunctionProtocol --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/uevent --------
  DEVTYPE=usb_interface
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=10/0/0
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01ic0Aisc00ip00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bInterfaceNumber --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bNumEndpoints --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bInterfaceClass --------
  0a
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bInterfaceSubClass --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/bInterfaceProtocol --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01ic0Aisc00ip00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/iad_bFirstInterface --------
  01
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/iad_bInterfaceCount --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/iad_bFunctionClass --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/iad_bFunctionSubClass --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.2/iad_bFunctionProtocol --------
  00
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/uevent --------
  DEVTYPE=usb_interface
  DRIVER=option
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=255/255/255
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bInterfaceNumber --------
  03
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bNumEndpoints --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bInterfaceClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bInterfaceSubClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/bInterfaceProtocol --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.3/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/uevent --------
  DEVTYPE=usb_interface
  DRIVER=option
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=255/255/255
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bInterfaceNumber --------
  04
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bNumEndpoints --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bInterfaceClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bInterfaceSubClass --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/bInterfaceProtocol --------
  ff
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01icFFiscFFipFF
  
------- /sys/bus/usb/devices/2-1.2.4:1.4/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/uevent --------
  DEVTYPE=usb_interface
  DRIVER=usb-storage
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=8/6/80
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01ic08isc06ip50
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bInterfaceNumber --------
  05
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bNumEndpoints --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bInterfaceClass --------
  08
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bInterfaceSubClass --------
  06
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/bInterfaceProtocol --------
  50
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01ic08isc06ip50
  
------- /sys/bus/usb/devices/2-1.2.4:1.5/supports_autosuspend --------
  1
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/uevent --------
  DEVTYPE=usb_interface
  DRIVER=usb-storage
  PRODUCT=12d1/1436/0
  TYPE=239/2/1
  INTERFACE=8/6/80
  MODALIAS=usb:v12D1p1436d0000dcEFdsc02dp01ic08isc06ip50
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bInterfaceNumber --------
  06
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bAlternateSetting --------
   0
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bNumEndpoints --------
  02
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bInterfaceClass --------
  08
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bInterfaceSubClass --------
  06
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/bInterfaceProtocol --------
  50
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/modalias --------
  usb:v12D1p1436d0000dcEFdsc02dp01ic08isc06ip50
  
------- /sys/bus/usb/devices/2-1.2.4:1.6/supports_autosuspend --------
  1
  
DONE

```

---

### Post by Lars Noodén on 2011-05-02
The modem worked again today for a few hours with no intervention on my part.  It stopped working after I went back to Ethernet and would not reconnect.

Added: right now it's working again

---

### Post by alexfish on 2011-05-02
> **Lars Noodén said:**
> The modem worked again today for a few hours with no intervention on my part.  It stopped working after I went back to Ethernet and would not reconnect.

Added: right now it's working again

Hi that a good sign / you need to monitor the drivers etc look at the logfiles to see what it is showing
```
tail -f /var/log/syslog
```

also monitor the udev events
udevadm monitor (hotplugging monitor) IE use the command then connect the device
```
udevadm monitor
```
can filter the fields with grep *
examples
udevadm monitor -e | grep DRIVER
udevadm monitor -e | grep INTERFACE
udevadm monitor -e | grep modem
udevadm monitor -e | grep tty
udevadm monitor -e | grep /dev/
udevadm monitor -e | grep MODALIAS

Have you recently used this device in windows or are you duel booting

Looks if this device may have problem with the interfaces or it's mode of operation

have done some searching as regards the modalias
all indicators for this device show to have a cdc_ether or zaurus interface (zaurus depends on cdc_ether)

noted from
usb:v12D1p1436 d0000 dcEF dsc02 dp01 ic02 isc06 ipFF
ic02 isc06
grep -i ic02isc06 /lib/modules/`uname -r`/modules.alias
but if linked with a cdc_acm the device proticols are different
can do a   
```
grep -i ic02isc06 /lib/modules/`uname -r`/modules.alias
```
or
```
grep -i ic02isc06 /lib/modules/*/modules.alias
```

alexfish

only problem with this is the device protocols but can look into this later

---

### Post by Lars Noodén on 2011-05-03
> **alexfish said:**
> Hi that a good sign / you need to monitor the drivers etc look at the logfiles to see what it is showing
...

also monitor the udev events
udevadm monitor (hotplugging monitor) IE use the command then connect the device

Both provide an overwhelming flood of information.  How are the relevant bits identified?

---

### Post by EduardoAB on 2011-06-06
Hey guys. Is there anybody upthere either in the net or in Ubuntu who is able to properly guide me trough the required steps to connect my Modem Huawei E173 with Ubuntu 11.04. If so, please be kind and respond "loud and clear" with a minimum of thecnicalities.
Thanks in advance
Eduardo

---

### Post by Lars Noodén on 2011-06-07
I'm still stumped.  The modem has functioned about five times as it should in 11.04.  The rest of the time it won't connect: it will say "preparing to connect" then drop back to "not connected"  I've not figured a way around that.

---

### Post by nbound on 2011-06-07
> **Lars Noodén said:**
> I'm still stumped.  The modem has functioned about five times as it should in 11.04.  The rest of the time it won't connect: it will say "preparing to connect" then drop back to "not connected"  I've not figured a way around that.

May be stating the obvious, but - have you tried this device in another location, that is unless your dual booting with OSX from ur first post.

---

### Post by Lars Noodén on 2011-06-07
> **nbound said:**
> May be stating the obvious, but - have you tried this device in another location, that is unless your dual booting with OSX from ur first post.

The same device on the same computer works more often than not in OS X.

---

