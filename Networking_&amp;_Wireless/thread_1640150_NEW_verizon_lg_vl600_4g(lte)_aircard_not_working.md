---
title: "NEW verizon lg vl600 4g(lte) aircard not working"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2010-12-07
I realize this is probably a little early to start a discussion for.  I have a few of the new Verizon lte aircards and have had NO success in getting either wvdial to dial up to it or to have network manager do anything.  Network manager recognizes it as eth1.  When it tries to get a connection via dhcp, it spins for a while and I assume just times out.  I assume there are going to be some sort of updates/extras to get these new sim card based aircards to make a connection through Linux.  

As I find out any new information, I will update this thread for any future searchers.

---

### Post by alexfish on 2010-12-07
hi

don't know much about these devices

if usb can see how it lists with this code if system 10.04 , 10.10 


Code:

usb-devices

locate the lines which indicate the device

hopefully it will show the drivers involved, and may point as to where to look
for possible areas as to how to connect - IE scan network - or configure and connect
via AT commands. also looking for the actual Manufacture

if system lower than mentioned can try

Code:

lsusb -t

or

lsusb -v

with the -v look for the lines wich would point to the drivers of the devices

once got info , may look up manufacturing detail , and look at the actual drivers which

are loading , and look up the source at , they may possibly fall into two areas

usb (class and serial ) and net, + need kernel version used

[http://lxr.linux.no/#linux+v2.6.36/drivers](http://lxr.linux.no/#linux+v2.6.36/drivers)

also can see how it lists in the devs , if tty allocated / the drivers may give a clue
to the appended to tty , IE ttyXXXX

Code:

ls -al /dev/tty

and look through the list

another area look is in the log file viewer

Added :since drivers of some description are loading and NM is trying to connect ; Can't imagine that your far away from getting this device to work

Also have a look at ifconfig / and the default files , maybe it will show the type of interface, and other info/ if nothing shows then possible assume , may need software or user space to kick it in
if got a serial port terminal see if it responds to AT commands ,could also try AT Command "ATI" it may list the bands it operates on
alexfish

---

### Post by senor_smile on 2010-12-07
> **alexfish said:**
> hi

don't know much about these devices

if usb can see how it lists with this code if system 10.04 , 10.10 


Code:

usb-devices

locate the lines which indicate the device

hopefully it will show the drivers involved, and may point as to where to look
for possible areas as to how to connect - IE scan network - or configure and connect
via AT commands. also looking for the actual Manufacture

if system lower than mentioned can try

Code:

lsusb -t

or

lsusb -v

with the -v look for the lines wich would point to the drivers of the devices

once got info , may look up manufacturing detail , and look at the actual drivers which

are loading , and look up the source at , they may possibly fall into two areas

usb (class and serial ) and net, + need kernel version used

[http://lxr.linux.no/#linux+v2.6.36/drivers](http://lxr.linux.no/#linux+v2.6.36/drivers)

also can see how it lists in the devs , if tty allocated / the drivers may give a clue
to the appended to tty , IE ttyXXXX

Code:

ls -al /dev/tty

and look through the list

another area look is in the log file viewer

alexfish

Thanks!  That was quite a bit of information.  I am running 10.10 64-bit.  usb-devices yielded the following: 

> 
T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1004 ProdID=61aa Rev=01.00
S:  Manufacturer=LG ELECTRONICSInc
S:  Product=LG UDC-AHB Subsystem
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=400mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm



I see the first two cdc_ether entries.  That must be its loading as ether1, although it can't pick up an address.  Everything else in that entry is greek to me. 

I catch it appearing as ttyACM0 under dev when plugged in.  My previous working wvdial.conf file fails however:

```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```

Here's my wvdial.conf:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
#Baud = 460800
Baud = 240000000
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>
Carrier Check = no
Dial Command = atdt
Username = 2065555555@vzw3g.com
Password = vzw
Phone = #777
Stupid Mode = 1

```

---

### Post by alexfish on 2010-12-07
hi

ADDED: 11 DEC 2010: PDF documentation Worth reading : Please note this is direct  download Link

[CDC Ethernet model Communications class]("http://www.usb.org/developers/devclass_docs/usbcdc11.pdf")
[SIZE=-1](many Cable Modems and networked devices)[/SIZE]Experimental/2.4,  Working/2.6

The Kernel Module:
looking up first part / cdc_ether.c

[http://lxr.linux.no/#linux+v2.6.36/drivers/net/usb/cdc_ether.c](http://lxr.linux.no/#linux+v2.6.36/drivers/net/usb/cdc_ether.c)



here it lists the device ID's and the listing 

have you found a listing in the devs for ttyXXX

then possible try for AT command response on the cdc-acm : ACMxxx ports if listing

try each port:

Also search for any dev ports on the cdc_ether.c / 

if you can't find the ports

look in /sys/bus/devices/usb1/

or usb2/ try 1 first
or usb0/ if this one exits then look in here as well

look in each of the folders that list like 1-2 ; 1-3 and so on

in each folder look at the file "manufacturer"  your looking for  "LG ELECTRONICSInc"
when got look at the folders at top of page ;

each folder will hold other info , then in each folder holds more folders

some  don't get listed by the usb-device command , any how , look for a folder
which would list as ttyXXX , or a file not listing as "driver,ep_x,power,subsystem"

---

### Post by alexfish on 2010-12-07
If you don't have Serial port terminal
and found the ttyACMx

Try this 

edit the ttyACMx to suite or what evever shows from the devs

if you have no serial port terminal try this

open up first terminal and enter this command

Code:

[COLOR=Blue]tr -s "\n" < /dev/ttyACMx[/COLOR]

this will show any responses from the device if any

to send commands open up a second terminal

send the commands like so this is on port [COLOR=Blue]ttyACM0 [COLOR=Black]as said , have to edit ports to suit[/COLOR][/COLOR]
something like [COLOR=Blue]ttyACM1[/COLOR] : according to the drivers it should have a data port

 [B]/* a data interface altsetting does the real i/o */
[ 215]("http://lxr.linux.no/linux+*/drivers/net/usb/cdc_ether.c#L215")[/B] [B]                        [d]("http://lxr.linux.no/linux+*/+code=d") = &[info]("http://lxr.linux.no/linux+*/+code=info")->[data]("http://lxr.linux.no/linux+*/+code=data")->[cur_altsetting]("http://lxr.linux.no/linux+*/+code=cur_altsetting")->[desc]("http://lxr.linux.no/linux+*/+code=desc");
[ 216]("http://lxr.linux.no/linux+*/drivers/net/usb/cdc_ether.c#L216")[/B] [B]                        if ([d]("http://lxr.linux.no/linux+*/+code=d")->[bInterfaceClass]("http://lxr.linux.no/linux+*/+code=bInterfaceClass") != [USB_CLASS_CDC_DATA]("http://lxr.linux.no/linux+*/+code=USB_CLASS_CDC_DATA")) {
[ 217]("http://lxr.linux.no/linux+*/drivers/net/usb/cdc_ether.c#L217")[/B] [B]                                [dev_dbg]("http://lxr.linux.no/linux+*/+code=dev_dbg")(&[intf]("http://lxr.linux.no/linux+*/+code=intf")->[dev]("http://lxr.linux.no/linux+*/+code=dev"), "slave class %u\n",
[ 218]("http://lxr.linux.no/linux+*/drivers/net/usb/cdc_ether.c#L218")[/B] **                                        [d]("http://lxr.linux.no/linux+*/+code=d")->[bInterfaceClass]("http://lxr.linux.no/linux+*/+code=bInterfaceClass")**

Code:

[COLOR=Blue]echo -e "[/COLOR][COLOR=Red]AT[/COLOR][COLOR=Blue]\r" > /dev/[/COLOR][COLOR=Blue]ttyACM0

[COLOR=Black]Added don't forget to try other ports associate with the device , IE, ones not listing as ttyXXX, it may be worth a try

Updated some info

here are some option to look at

The device may work as a standard cdma connection with the wvdial
if the correct port is found

but know it can connect as CDC Ethernet interface (assumed by looking at the drivers)

to get the Ethernet up and running (4g ), possible  need to send the correct command

one know sequence is

sending the correct at command to set the function IE: some known ones are AT+FUN=* where the * represents the number = cdma or 4g (the [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]CDC Ethernet interface)
possible to send AT commands AT+CFUN? (to find the device setting) or AT+CFUN=? (to find the settings available): some of the bands may be revealed by the AT command " ATI "
[/COLOR][/COLOR][COLOR=Blue][COLOR=Black] 
AT+CGDCONT=1,"IP","proxy"



where the proxy is an apn or server address

these are the some known Verizon

Verizon 1
Gateway IP: 12.168.70.74
Port: 9201

Verizon 2
Gateway IP: 153.114.115.100
Port 9203
Verizon 3

APN: No configuration needed
Username for APN: No configuration needed
Password for APN: No configuration needed
WAP Gateway IP: 153.114.115.100
WAP Gateway Port: 9203

so need to find out the above {ask Verizon}

2. then need to issue a command to to start the interface this is one known AT command

AT*ENAP=1,1

to stop the interface

AT*ENAP=0

to get the interface up and running and seen on the system , I would assume need to launch dhclient

dhclient usb*

IE :

dhclient usb0

As said , I don't know the device and all the above are avenues to look at { as mention in earlier post , do you need to configure the routing tables (ifconfig, for an interface)
even may need to install a program like "resolvconf" to guide the address IE address in the /etc/resolv.conf ( Limitation of resolvconf = conflicts with wvdial , so will un-install wvdial , and also make gnomeppp useless)
[/COLOR][/COLOR]

---

### Post by PlancksCnst on 2010-12-09
I've been working on this today. I got both the LG and the Pantech devices in today.

The LG device is unresponsive. It does not give any responses to any commands on the tty port (and I tried turning echo on via ATE). Trying to bring up the ethernet interface only switches it to unknown state.



The Pantech device is responds to commands. I accedentally clobbered the pdp 1 context by trying an APN before first checking to see what it was set for. There were two other PDP contexts already configured as follows
```
+CGDCONT: 3,"IPV4V6","vzwinternet","0.0.0.0",0,0
+CGDCONT: 4,"IPV4V6","vzwapp","0.0.0.0",0,0
```

Originally, I was able to get it to connect to the vzwinternet context. pppd showed a successful authentication but then did not get any ip address or gateway.

On Windows, the LG device was able to connect using CDMA but not LTE. The Pantech device was able to connect to LTE and got 16Mb downlink and 0.9Mb uplink. My next avenue will be to use a USB analyzer to find what the Windows software is doing.

---

### Post by alexfish on 2010-12-09
> **PlancksCnst said:**
> I've been working on this today. I got both the LG and the Pantech devices in today.

The LG device is unresponsive. It does not give any responses to any commands on the tty port (and I tried turning echo on via ATE). Trying to bring up the ethernet interface only switches it to unknown state.



The Pantech device is responds to commands. I accedentally clobbered the pdp 1 context by trying an APN before first checking to see what it was set for. There were two other PDP contexts already configured as follows
```
+CGDCONT: 3,"IPV4V6","vzwinternet","0.0.0.0",0,0
+CGDCONT: 4,"IPV4V6","vzwapp","0.0.0.0",0,0
```Originally, I was able to get it to connect to the vzwinternet context. pppd showed a successful authentication but then did not get any ip address or gateway.

On Windows, the LG device was able to connect using CDMA but not LTE. The Pantech device was able to connect to LTE and got 16Mb downlink and 0.9Mb uplink. My next avenue will be to use a USB analyzer to find what the Windows software is doing.

Hi

can you post the details and sequence of the AT commands or commands send for each instance

also are you sending the commands direct , then calling the pppd

thanks in advance

alexfish

---

### Post by PlancksCnst on 2010-12-09
The LG device continues to be unresponsive on Linux. On the Pantech device, I ran through a bunch of commands, but to get it to connect, I did ```
at*99***3#
```
This was to use the 3rd pdp context definition which was already present in the device. It returned
```
CONECT 100000000
```
I'm not sure about the number of zeros, but it was a bunch. I then connected pppd to the terminal, and it authenticated and stopped.

I was able to do some USB sniffing on the LG device when talking to the Windows driver. The software did these:
```

ATE0V1
AT+CPIN?
AAT+CLCK="SC",2
AT+GCAP?
AT+CMEE=1

```

When the software actually connected, it didn't seem to be because of any AT command. I haven't tried to decode the binary data yet, but I did see 'vzwinternet' in ASCII among the data, suggesting it connected using that APN.

Attached is a capture that you can view using [TotalPhase Data Center]("http://www.totalphase.com/support/product/beagle_usb480/") (zero-cost). This was my attempt at talking to the device on Linux both using screen and echoing straight to the device.

---

### Post by mpareja on 2010-12-10
Expirencing the same behavior, I have been rendering the same results. Is there anything else that we may try? Also network manager os detecting it as a unknown wired device? 
U 10.10 64b

---

### Post by mpareja on 2010-12-10
See Items in bold. 


```
Bus 001 Device 006: ID 1004:61aa LG Electronics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
[B]  bDeviceClass            2 Communications
  bDeviceSubClass         2 Abstract (modem)
  bDeviceProtocol         1 AT-commands (v.25ter)[/B]
  bMaxPacketSize0        64
  idVendor           0x1004 LG Electronics, Inc.
  idProduct          0x61aa 
  bcdDevice            1.00
  iManufacturer           1 LG ELECTRONICSInc
  iProduct                2 LG UDC-AHB Subsystem
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          145
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              400mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass       6 Ethernet Networking
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
[B]      bInterfaceClass         2 Communications
      bInterfaceSubClass      6 Ethernet Networking[/B]
      bInterfaceProtocol      0 
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC Ethernet:
        iMacAddress                      4 64995DFA3356
        bmEthernetStatistics    0x00000000
        wMaxSegmentSize              22528
        wNumberMCFilters            0x0000
        bNumberPowerFilters              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         2
[B]      bFunctionClass          2 Communications
      bFunctionSubClass       2 Abstract (modem)
      bFunctionProtocol       1 AT-commands (v.25ter)[/B]
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
[B]      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)[/B]
      iInterface              0 
      CDC Header:
        bcdCDC               1.00
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        2
        bSlaveInterface         3 
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          3
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
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


```

Also I remember when configuring the device on windowz it did not create a PPP connection like previous usb broadband modems. Almost like there is an ethernet controller + serial Comm (configuration interface).

---

### Post by alexfish on 2010-12-10
hi mparaeja

from your info from the lsusb there is 

CDC Ethernet:
      [COLOR=Blue]  iMacAddress                      4 64995DFA3356[/COLOR]
        bmEthernetStatistics    0x00000000
        wMaxSegmentSize              22528
        wNumberMCFilters            0x0000
        bNumberPowerFilters              0


have you tried to configure Network Manager ,edit  VPN connections ,to set up this wired interface
with a mac address highlighted in blue

or tried to set the auto connect

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Link to techland.time removed 12 dec 2010

ADDED : found pdf documentation  , relating to the CDC-Ethernet : see Post #4

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Latest info 12/12/2010 Verizon**
**[SIZE=2]4G LTE Data-stick Mac/Linux/Windows-other authentication information.[/SIZE]**

**12-12-2010 10:22 AM**
[SIZE=2]
[http://community.vzw.com/t5/4G-Discussion/4G-LTE-Data-stick-Mac-Linux-Windows-other-authentication/m-p/347804](http://community.vzw.com/t5/4G-Discussion/4G-LTE-Data-stick-Mac-Linux-Windows-other-authentication/m-p/347804)

[/SIZE]The following information has been released publicly by VZW advanced support so I feel I can share this now:
If  you want to use the UML290 on the Mac/Linux/UNIX/other-platforms you  can now do so if you have the engineering knowledge or a little  know-how:
Quick Notes: Verizon 4G LTE uses the GSM APN authentication  method through a GGSN (similar to AT&T) and 3G (1X/EVDO)  traditional uses the HA CDMA method. The old CDMA authentication method  has been posted years before so I won't repost that.
You WILL NOT GET SUPPORT UNTIL THE OFFICIAL VZACCESS Software comes out on the Mac.


4G LTE GSM General Device Settings-
Phone Number: PhoneNumber
Account name: [EMAIL="PhoneNumber@vzw4g.com"]PhoneNumber@vzw4g.com[/EMAIL]
Password: vzw

Advanced Settings-
Carrier: Generic
Model: GPRS (GSM/3G)
APN: vzwinternet
CID: 1

Click OK, then connect and enjoy.

So  on the Mac connection manager (generic apple), make a profile for your  UML290 hardware, should be a modem. Make a GSM connection profile with  the above. Phone number is your data-stick phone number (fake phone  number, used for system identification, get it from VZAccess or your  account page online). Account name is "phonenumber@vzw4g.com".  (Basically add @vzw4g.com to your phonenumber. Password is "vzw", same  as 3g CDMA. In GSM/3G/4G carrier use generic (no special parameters).  Model is GPRS (GSM/3G, same as 4G). GSM APN is "vzwinternet". CID is 1  if your drivers need it.

Enjoy 4G LTE GSM technology by VZW on  your Mac! I will be running this on my Linux engineering dev machine  soon. Finally I LOVE YOU VZW!
 
Oh and if you're just  installing it without a Windows machine using it at least once, your SIM  card has to be provisioned by VZW support or a store...
 
If you want a visual Mac guide:
[http://homepage.mac.com/jrc/contrib/tzones/](http://homepage.mac.com/jrc/contrib/tzones/)
Official  VZW support (replace the inetgsm.vzw3g.com APN used for overseas  roaming with the 4g APN used domestically as listed above):
Mac: [http://support.vzw.com/clc/devices/knowledge_base.html?id=30063](http://support.vzw.com/clc/devices/knowledge_base.html?id=30063)
Windows XP/Vista/7 (If you don't want to use VZAccess): [http://support.vzw.com/clc/devices/knowledge_base.html?id=29355](http://support.vzw.com/clc/devices/knowledge_base.html?id=29355)
Username/Password/Everything as said above applies, replace as needed.
 
NO  VZAccess on Mac yet, check your data usage on vzw.com my account... The  SMS warning messages should work since it's a standard GSM 3G/4G  implementation by VZW if you can get a Mac/Linux app that watches for  SMS from the data modem driver interface.
 
Verizon will  probably add a second APN for smart-phones when they come out with LTE  chips. Example: The "vzwinternet" APN gives you a public IP address as  that's mean't for data-sticks. They will probably use something (I'm  just guessing here) like "advdevice" for smart-phones and that will give  the smart-phone a private IP address (10.x.x.x) like the current CDMA  HA's do. With APN data traffic separation VZW with 4G GSM tech. can  manage traffic volumes better with bandwidth limits, etc.  AT&T/T-Mobile are doing the same now and it has recently been  implemented on the legacy CDMA HA's also. Also firewalling, security.

Summarized for wvdial . in part may look like , all similar to any 3g connection


**Updated 13 Jan 2011** ;** ref cd usb-rndis-lite**

Although I removed : possible meanings of LTE ( possible true 4g speed ) may be on the cdc ethenet interface : this looks as if confirmed
and the comment (Summarized for wvdial . in part may look like , all similar to any 3g connection)

**Recommend : Read these links **it may indicate how to get connected on True 4g interface CDC-ETHERNET , this type of interface should allow faster speeds than the standard acm driver


[http://community.vzw.com/t5/4G-Discussion/4G-LTE-Data-stick-Mac-Linux-Windows-other-authentication/m-p/358310#M435](http://community.vzw.com/t5/4G-Discussion/4G-LTE-Data-stick-Mac-Linux-Windows-other-authentication/m-p/358310#M435)

then look at solutions on how to bring up the interface

[http://embedded.seattle.intel-research.net/wiki/index.php?title=Setting_up_USBnet](http://embedded.seattle.intel-research.net/wiki/index.php?title=Setting_up_USBnet)

[http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/)

[http://www.linux.org/docs/ldp/howto/Cable-Modem/intro.html](http://www.linux.org/docs/ldp/howto/Cable-Modem/intro.html)

  As regards the cd usb-rndis-lite/
have a look at this thread
 
[http://ubuntuforums.org/showthread.php?t=869229](http://ubuntuforums.org/showthread.php?t=869229)
 

Reason for removal of previous info ( Post #13 by willzzz) . looks as if  this info gives a standard connection of the likes of 3g ,but using the  faster speed rate of acm
this tends to make me look at some devices which are loading  option driver, but have greater baud rates available than the standard 115200
and possible reason the claimed speeds are not attained: Always check if there are Kernel Patches Available for your devices. if available, Check them out

the  linux drivers are loaded the relative to the device ID's. IE. the driver modules contain the device ID'S 
It will be interesting to find out the speeds of this type of connection (to monitor use netspeed)

Added: reading through the links , looks as if a linux connection should be easier than that of others
and that the Verizon statement of drivers only Available for * , Smacks in the face of Freedom of Use , 
Verizon Should make the sequences (Technical) Publicly Available , that's not Hard Work:

---

### Post by aport on 2010-12-13
> **PlancksCnst said:**
> The LG device continues to be unresponsive on Linux. On the Pantech device, I ran through a bunch of commands, but to get it to connect, I did ```
at*99***3#
```
This was to use the 3rd pdp context definition which was already present in the device. It returned
```
CONECT 100000000
```
I'm not sure about the number of zeros, but it was a bunch. I then connected pppd to the terminal, and it authenticated and stopped.

I was able to do some USB sniffing on the LG device when talking to the Windows driver. The software did these:
```

ATE0V1
AT+CPIN?
AAT+CLCK="SC",2
AT+GCAP?
AT+CMEE=1

```

When the software actually connected, it didn't seem to be because of any AT command. I haven't tried to decode the binary data yet, but I did see 'vzwinternet' in ASCII among the data, suggesting it connected using that APN.

Attached is a capture that you can view using [TotalPhase Data Center]("http://www.totalphase.com/support/product/beagle_usb480/") (zero-cost). This was my attempt at talking to the device on Linux both using screen and echoing straight to the device.

Here is my Beagle 480 trace on Windows while using the Verizon connection manager to bring the card online.

It looks like it's using some DM commands.

The sniff contains my ESN and MDN, so be gentle :)

---

### Post by willzzz on 2010-12-24
Hey this is willzzz88 from the Verizon forums who originally posted the details and I am also a member here so I thought I'd chip in and update you guys.
You need to do AN ADDITIONAL MINOR CHANGE in addition to the above for 3G/4G under linux on the UML290 (The VL600 uses some proprietary LG chip-set for the LTE that we can't figure out atm, get the UML290, industry standard Qualcomm Gobi stuff...):

AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0

Phone = *99#

or 

Phone = *99***3#

or 

Phone = #777

4G: Username = <phonenumber>@vzw4g.com
3G: Username = <phonenumber>@vzw3g.com
Password = vzw

Stupid Mode = 3

YOU NEED TO CHANGE THE APN connection APN to #3. If you use #1 you risk over-writing the ORIGINAL VZAccess Win/Mac APN profiles on the SIM card which has connection problems if you use the same card again in Windows/Mac and kind of screws it up.

VZAccess in Windows/Mac apparently is using APN#1 with a direct connection to VZ's IMS with IPv6 only. This hasn't been figured out. If you want a direct connection simply do a connection with the above and with a CID of #3 for the direct vzwinternet APN of #3!!!!!! (Important).

So far 4G works well, 3G may need additional tweaking for 3g/4g transitions.

---

### Post by irieblue on 2010-12-28
willzzz et al. Regarding the VL600, I think I understand what the issue is regarding getting this device to work on Linux (and MacOS X). Attached is a screen shot of how it enumerates on Windows, it's as if the Windows driver sends a vendor specific Configure command that makes the device enumerate a hidden configuration. 

On MacOS X, and I would assume Ubuntu (without a vendor specific command to re-enumerate the VL600  with this hidden configuration, the Device only enumerates with 2 Pseudo CDC interfaces). I say Pseudo interfaces since they look like CDC, but are not 100% CDC Descriptors.

From the Windows config screen this device has a boatload of interfaces that I just don't see with the device plugged into MacOS X. Also this device takes a long time to enumerate which suggests to me that it re-enumerates at least once on windows.

I really don't think it is worth the time and effort to support the VL600 especially since the Pantech has much better performance. If LG can't get their act together and write decent firmware, I say it's their loss. Verizon seems content to have all these vendors dream up their own software specification, rather than adhere to open standards for USB network devices, sheesh..

Here is how the LG looks plugged into a machine running MacOS. The one thing that seems suspect to me in the Windows enumeration, is that they might be using Mux Mode, which is essentially that the driver sends serial , diagnostic, ethernet data over a single endpoint. 

High Speed device @ 3 (0x24100000): .............................................   Communication device: "LG UDC-AHB Subsystem"
  Device Descriptor   
      Descriptor Version Number:   0x0200
      Device Class:   2   (Communication)
      Device Subclass:   2
      Device Protocol:   1
      Device MaxPacketSize:   64
      Device VendorID/ProductID:   0x1004/0x61AA   (LG Electronics Inc.)
      Device Version Number:   0x0100
      Number of Configurations:   1
      Manufacturer String:   1 "LG ELECTRONICSInc"
      Product String:   2 "LG UDC-AHB Subsystem"
      Serial Number String:   0 (none)
  Configuration Descriptor   
      Length (and contents):   145
      Number of Interfaces:   4
      Configuration Value:   1
      Attributes:   0x80 (bus-powered)
      MaxPower:   400 ma
      Interface Association   Communications-Control
      Interface #0 - Communications-Control   
      Interface #1 - Communications-Data/Unknown Comm Class Model   
      Interface Association   Communications-Control
      Interface #2 - Communications-Control   
      Interface #3 - Communications-Data/Unknown Comm Class Model   
  Device Qualifier Descriptor   
  Other Speed Configuration Descriptor

---

### Post by alexfish on 2011-01-02
> **irieblue said:**
> willzzz et al. Regarding the VL600, I think I understand what the issue is regarding getting this device to work on Linux (and MacOS X). Attached is a screen shot of how it enumerates on Windows, it's as if the Windows driver sends a vendor specific Configure command that makes the device enumerate a hidden configuration. 

On MacOS X, and I would assume Ubuntu (without a vendor specific command to re-enumerate the VL600  with this hidden configuration, the Device only enumerates with 2 Pseudo CDC interfaces). I say Pseudo interfaces since they look like CDC, but are not 100% CDC Descriptors.

From the Windows config screen this device has a boatload of interfaces that I just don't see with the device plugged into MacOS X. Also this device takes a long time to enumerate which suggests to me that it re-enumerates at least once on windows.

I really don't think it is worth the time and effort to support the VL600 especially since the Pantech has much better performance. If LG can't get their act together and write decent firmware, I say it's their loss. Verizon seems content to have all these vendors dream up their own software specification, rather than adhere to open standards for USB network devices, sheesh..

Here is how the LG looks plugged into a machine running MacOS. The one thing that seems suspect to me in the Windows enumeration, is that they might be using Mux Mode, which is essentially that the driver sends serial , diagnostic, ethernet data over a single endpoint. 

High Speed device @ 3 (0x24100000): .............................................   Communication device: "LG UDC-AHB Subsystem"
  Device Descriptor   
      Descriptor Version Number:   0x0200
      Device Class:   2   (Communication)
      Device Subclass:   2
      Device Protocol:   1
      Device MaxPacketSize:   64
      Device VendorID/ProductID:   0x1004/0x61AA   (LG Electronics Inc.)
      Device Version Number:   0x0100
      Number of Configurations:   1
      Manufacturer String:   1 "LG ELECTRONICSInc"
      Product String:   2 "LG UDC-AHB Subsystem"
      Serial Number String:   0 (none)
  Configuration Descriptor   
      Length (and contents):   145
      Number of Interfaces:   4
      Configuration Value:   1
      Attributes:   0x80 (bus-powered)
      MaxPower:   400 ma
      Interface Association   Communications-Control
      Interface #0 - Communications-Control   
      Interface #1 - Communications-Data/Unknown Comm Class Model   
      Interface Association   Communications-Control
      Interface #2 - Communications-Control   
      Interface #3 - Communications-Data/Unknown Comm Class Model   
  Device Qualifier Descriptor   
  Other Speed Configuration Descriptor

Updated post #11
see foot of / may be of help

also see post #2 on initial suggestions . athough the interface names may differ , the cdc ethernet is based in the same RNDIS , see links to the driver
[http://lxr.linux.no/#linux+v2.6.36/d...sb/cdc_ether.c]("http://lxr.linux.no/#linux+v2.6.36/drivers/net/usb/cdc_ether.c")

As regards the cd usb-rndis-lite/ (updated link at post #11)

direct to how to cdc-ethernet

[http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/)

alexfish

AS a note Pharscape have HSO connect which operates on the same principal (almost).. May be Worth Reading through the source codes

other possibility is to use the pppd endpoint ( these can be address or mac addresses)

---

### Post by alexfish on 2011-02-24
bumping

as regards these devices with cdc_ether interface and previously posted

Possibly look at How the HSO connect works 

Can have a look at this thread , it may throw some light on the subject

[http://ubuntuforums.org/showthread.php?t=1669429](http://ubuntuforums.org/showthread.php?t=1669429)

[http://ubuntuforums.org/showthread.php?p=10490373#post10490373](http://ubuntuforums.org/showthread.php?p=10490373#post10490373)

possible editing a few files in the Wader Core may get these Devices Up and running

But can't imagine this is for a novice , but it may enable these devices to run at full Bore

regards

alexfish

---

### Post by balrog-kun on 2011-03-22
Just to update this thread I had some success talking to the AT port of the device.  The USB analyzer logs posted by aport and Planck'sCnst have been very helpful in figuring it out, as well as the shopping mall where I'm using the free wifi internet before I can connect through the dongle ;)

I haven't had success accessing internet through the dongle yet, but I can send/receive AT, send the binary frames -- without understanding them -- which make the dongle connect (i.e. led starts blinking green) and I believe I also have the ethernet frames decoding/encoding although not confirmed because not knowing the gateway ip etc I couldn't get any communication going on yet.  I'll post more information when I figure this part out.

For now I have posted a dummy "terminal emulator" python script which just takes what you type and adds the header that the modem is expecting and then sends it to /dev/ttyACM0, and also strips the headers of what the modem returns so you can run AT commands.
[http://openstreetmap.pl/balrog/vl600-com.py](http://openstreetmap.pl/balrog/vl600-com.py)

The AT interface is so bad that practically no command works exactly the way it should according to the GSM specs.  Most commands are just plain broken, although there are some interesting ones.  Don't run AT%FRST, this will brick the device and you'll need the firmware reflashed (at least I hope this will fix it as I've just bricked my device and have no windows machine, so I'm hoping they can do it for me at the Verizon store)

(EDIT: Verizon said they'd replace it because they couldn't get the firmware upgrade working "because the dongle won't connect in the first place" -- I suggested connting through WiFi or cable or another dongle, they tried it and couldn't get it to work.  Since they're replacing it I didn't want to insist, the downside is it'll take until Thursday -- the other options since I just bought the dongle this week was to take it to the store where I got it, return and ask for another one but it'd take even longer.  So in the end I don't know if firmware upgrade fixes this -- bottom line is don't try AT%FRST -- that's factory reset)

The modem expects a similar encapsulation as on the CDC ACM port, on all its ethernet frames too.  Hopefully I will have it confirmed to be working these days.

---

### Post by wyretrip on 2011-03-24
> **balrog-kun said:**
> Just to update this thread I had some success talking to the AT port of the device.  The USB analyzer logs posted by aport and Planck'sCnst have been very helpful in figuring it out, as well as the shopping mall where I'm using the free wifi internet before I can connect through the dongle ;)

I haven't had success accessing internet through the dongle yet, but I can send/receive AT, send the binary frames -- without understanding them -- which make the dongle connect (i.e. led starts blinking green) and I believe I also have the ethernet frames decoding/encoding although not confirmed because not knowing the gateway ip etc I couldn't get any communication going on yet.  I'll post more information when I figure this part out.

For now I have posted a dummy "terminal emulator" python script which just takes what you type and adds the header that the modem is expecting and then sends it to /dev/ttyACM0, and also strips the headers of what the modem returns so you can run AT commands.
[http://openstreetmap.pl/balrog/vl600-com.py](http://openstreetmap.pl/balrog/vl600-com.py)

The AT interface is so bad that practically no command works exactly the way it should according to the GSM specs.  Most commands are just plain broken, although there are some interesting ones.  Don't run AT%FRST, this will brick the device and you'll need the firmware reflashed (at least I hope this will fix it as I've just bricked my device and have no windows machine, so I'm hoping they can do it for me at the Verizon store)

(EDIT: Verizon said they'd replace it because they couldn't get the firmware upgrade working "because the dongle won't connect in the first place" -- I suggested connting through WiFi or cable or another dongle, they tried it and couldn't get it to work.  Since they're replacing it I didn't want to insist, the downside is it'll take until Thursday -- the other options since I just bought the dongle this week was to take it to the store where I got it, return and ask for another one but it'd take even longer.  So in the end I don't know if firmware upgrade fixes this -- bottom line is don't try AT%FRST -- that's factory reset)

The modem expects a similar encapsulation as on the CDC ACM port, on all its ethernet frames too.  Hopefully I will have it confirmed to be working these days.

Watching with great interest!

---

### Post by balrog-kun on 2011-03-26
Ok, so now I'm actually connected from Linux with this dongle (yay, no more sitting in the mall).  The replacement from Verizon arrived yesterday (so three days after they ordered it instead of one) and I only got my hands on it today.

I've put all the things you need to connect into a github repository at
[https://github.com/balrog-kun/LG-VL600-utils](https://github.com/balrog-kun/LG-VL600-utils)

I'm running Gentoo and I've been testing download speeds from different Gentoo mirrors in USA.  Most give me about 500 KB/s but some get up to steady 900 KB/s with spikes of up to 1.2 MB/s, so not bad!

You need a kernel patch for network communication (I added a patch against 2.6.38 to the repo linked above) and you need the python scripts in there to make the dongle connect in the first place.


[LIST]
[*]vl600-attach.py makes it connect, (EDIT: ah yes, after that run the DHCP client on eth2/eth3 - whatever the new interface is named - to really get connected.  On most distros you need to run "dhdpcd eth2", although I think Ubuntu uses "dhclient" instead)
[*]vl600-detach.py makes it disconnect (for use before unplugging the modem -- not sure if that is really needed, but just in case)
[*]vl600-com.py gives you a terminal (rather useless since the modem fails at almost any AT command, and those that do work, don't comply with standards)
[*]The bandwidth usage data that I hear is displayed on Windows would also be easy to query using the sequences from the usb analyzer log posted earlier.
[/LIST]
Run these scripts as root or someone with write access to /dev/ttyACM* -- on Gentoo you just need to add yourself to the "uucp" group for that.  dhcpcd does need root.

The kernel driver still drops some received frames, most likely because it assumes every USB frame corresponds to one network frame.  I'm going to fix it when I'm annoyed enough by it and then try to send this patch upstream so you don't need a patched kernel.

Only tested with the un-upgraded original VL600 firmware.  As has been said before your SIM probably needs to be activated/provisioned first (but somone would actually have to test it with a virgin SIM to confirm).  You can probably do that activation on Windows but if you don't have a Windows/Mac machine there's a chance they can do it at the Verizon store.  I have no Windows/Mac machines and this worked.

---

### Post by wyretrip on 2011-03-28
balrog-kun,

Wow! So close here!

I was able to use your kernel patch to get the device to load on eth2.

As root, I was able to get the VL 600 to connect (green light) using the python scripts and when I was in a 4G covered area I even picked up an address.

My local machine routes adjusted and everything looked good, except I don't believe I was able to pass traffic beyond the dhclient requests. 

I tried some directed dig dns queries and pings without success. I do not have a kernel based firewall or anything, my iptables -L policies are set to accept without any rules.

Did you run into anything like this while you were building your scripts and driver?

Thanks for your efforts!

wyretrip

---

### Post by balrog-kun on 2011-03-29
Hey wyretrip, thanks for trying it out.  Turns out I had a bug in there  (well.. not just one :)) related to a structure change between 2.6.38  and 2.6.38-git18, I believe I now made it work for both versions.  I  updated the patch in the repository, would be great to know if it now  works for you.  If it does please also let me know if you have the  upgraded firmware on your modem, that would be a good data point. My  modem has the original firmware on it.

I've also fixed a couple of other things, most importantly got rid of a  big ugly hack through which I faked ARP responses (which the  modem/network doesn't do for itself) -- turns out there's a flag you can  set which takes care of ARP completely.  I've also added support for fragmented  packets across various frames, which I mentioned in the earlier post,  now there shouldn't be any dropped frames anymore.

Let me know if there are -- dmesg would occasionally show lines starting  with "eth2: " as you browse (e.g. "eth2: Frame too short" or similar)

I've not had an occasion to try connecting from outside of 4G coverage, I  hoped it would work without changes but from your report it looks like it  doesn't work. Would be good to have a usb traffic log from Windows  connecting to 3G -- there are some ways to capture a log using wireshark  I think, or if anyone has a Qemu / KVM / Virtual box running Windows I  believe you can make the VM capture usb traffic without using a hardware usb analyzer.

---

### Post by wyretrip on 2011-03-29
Hey Balrog-kun,

Looks like the usbnet.h file for ubuntu differs from your distribution for 2.6.35.28. Maybe you could take a look at the section the patch is trying to modify and make some suggestions?

The patch states..
```

diff --git a/include/linux/usb/usbnet.h b/include/linux/usb/usbnet.h
index 44842c8..201f222 100644
--- a/include/linux/usb/usbnet.h
+++ b/include/linux/usb/usbnet.h
@@ -102,6 +102,7 @@ struct driver_info {
  * Affects statistic (counters) and short packet handling.
  */
 #define FLAG_MULTI_PACKET	0x1000
+#define FLAG_RX_ASSEMBLE	0x2000	/* rx packets may span >1 frames */
 
 	/* init device ... can sleep, or cause probe() failure */
 	int	(*bind)(struct usbnet *, struct usb_interface *);
```

The 2.6.35.28 source for usbnet.h is as follows for the related section..

```
struct driver_info {
	char		*description;

	int		flags;
/* framing is CDC Ethernet, not writing ZLPs (hw issues), or optionally: */
#define FLAG_FRAMING_NC	0x0001		/* guard against device dropouts */
#define FLAG_FRAMING_GL	0x0002		/* genelink batches packets */
#define FLAG_FRAMING_Z	0x0004		/* zaurus adds a trailer */
#define FLAG_FRAMING_RN	0x0008		/* RNDIS batches, plus huge header */

#define FLAG_NO_SETINT	0x0010		/* device can't set_interface() */
#define FLAG_ETHER	0x0020		/* maybe use "eth%d" names */

#define FLAG_FRAMING_AX 0x0040		/* AX88772/178 packets */
#define FLAG_WLAN	0x0080		/* use "wlan%d" names */
#define FLAG_AVOID_UNLINK_URBS 0x0100	/* don't unlink urbs at usbnet_stop() */
#define FLAG_SEND_ZLP	0x0200		/* hw requires ZLPs are sent */
#define FLAG_WWAN	0x0400		/* use "wwan%d" names */

#define FLAG_LINK_INTR	0x0800		/* updates link (carrier) status */

	/* init device ... can sleep, or cause probe() failure */
	int	(*bind)(struct usbnet *, struct usb_interface *);

	/* cleanup device ... can sleep, but can't fail */
	void	(*unbind)(struct usbnet *, struct usb_interface *);

```

Thank you for any help you can provide..

wyretrip

---

### Post by balrog-kun on 2011-03-30
Patch was against 2.6.38, but it looks like the difference is minor from 2.6.35.28.  So apparently the FLAG_MULTI_PACKET line and the comment above it were added after 2.6.35.  You just need to add the "#define FLAG_RX_ASSEMBLE 0x2000" line (note no "+" at the beginning) anywhere in that file (usbnet.h) and it should work.

Also I'm happy to report the driver has been accepted by one of the kernel maintainers and merged into one of the upstream trees (looks like it will be the net-2.6 tree, or whatever), I'm not sure how long is the way from there to vanilla but there's a chance it'll be there by 2.6.39.

---

### Post by wyretrip on 2011-03-31
The new patch did it!

[[IMG]http://www.speedtest.net/result/1229230725.png[/IMG]](http://www.speedtest.net)

Very nice speeds using 4G. 

[[IMG]http://www.speedtest.net/result/1230189928.png[/IMG]](http://www.speedtest.net)

In the sticks with 3G!

Great job!

---

### Post by balrog-kun on 2011-04-01
Cool, happy that it works in 3G too.  I had slightly better throughput using one of those speed-test sites: 16.2Mbps/10.5Mbps, but I was testing at night.

I added a dummy utility for displaying the current signal strength.

---

### Post by bichofnrise74 on 2011-04-21
Hi Balrog-kun,

I tried to follow your instruction and re-compiled a linux 2.6.38 with your patch and ran it on Ubuntu 10.04. The compile process worked fine and I was able to boot on it. When I run this, this is what I get.

$ uname -r
2.6.38-custom-2.6.38-verizon-lg-vl600

So, I assume that the new kernel is working fine. Now, when I tried to insert the LG aircard, I get these messages in the syslog.

usb 1-7: new high speed USB device using ehci_hcd and address 7
usb 1-7: device descriptor read/64, error -110
cdc_acm 1-7:1.2: ttyACM0: USB ACM device


If I run this, I get this result:
$ lsusb | grep LG

Bus 001 Device 007: ID 1004:61aa LG Electronics, Inc.

And when I try to run this script: vl600-attach.py, the system logs don't change and it is as if nothing happens.

Also, the dongle is blinking blue.

What do you think of the following?
1. Is there a way to check if I compiled the kernel 2.6.38 with your patch properly?
2. When I connect the dongle, what should I basically see in the system log? Eg. the usb_device is recognized?
3. When I run the vl600-attach.py script, is there any indication that it 'worked'. 
4. What is the next steps after this, should I use the network manager to connect to this device or use wvdial to connect to verizon? If so, can you post the basic configuration that you used?

---

### Post by Altusanew on 2011-04-21
Is there any work going on to make this noob friendly? Maybe a bug report to make this all more plug and play? I am not the most advanced user but I can try to help where I can, submit some output from some commands, test a package update to see if it works, ect.

---

### Post by balrog-kun on 2011-04-22
> **bichofnrise74 said:**
> 
So, I assume that the new kernel is working fine. Now, when I tried to insert the LG aircard, I get these messages in the syslog.

usb 1-7: new high speed USB device using ehci_hcd and address 7
usb 1-7: device descriptor read/64, error -110
cdc_acm 1-7:1.2: ttyACM0: USB ACM device

This is what I see:

usb 1-7: new high speed USB device number 7 using ehci_hcd
usb 1-7: device descriptor read/64, error -110
lg-vl600 1-1:1.0: eth1: register 'lg-vl600' at usb-0000:00:1d.7-1, LG VL600 modem, 64:99:5d:fa:66:46
cdc_acm 1-7:1.2: ttyACM0: USB ACM device
udev: renamed network interface eth1 to eth3

So it looks like you don't have USBNET compiled in.  You'll need to select the following three options in "Device Drivers" -> "Network device support" -> "USB Network Adapters":

"Multi-purpose USB Networking Framework"
"CDC Ethernet support (...)"
"LG VL600 modem dongle"

Hopefully when distributions catch up with the new kernel, you will have this by default.

> 
If I run this, I get this result:
$ lsusb | grep LG

Bus 001 Device 007: ID 1004:61aa LG Electronics, Inc.

And when I try to run this script: vl600-attach.py, the system logs don't change and it is as if nothing happens.

The logs won't indicate any change and there will be no output if everything goes fine, but the modem LED should start blinking green instead of blue.  After that you just need to run dhcp, but the USBNET driver needs to be compiled in.

And to answer the questions...
1. It looks like the patch is applied ok, you just need to select the three more options.
2. See above.
3. The green blinking led and no output will be the indication.. in theory we could output some message like "Connected" but it'd need further analysing of the windows driver.
4. Just run dhclient or dhcpcd on the "ethN" interface indicated in your logs.

@Altusanew: someone recently started a thread on the NetworkManager / ModemManager mailing lists about this type of modems (there are various other devices that behave like this), maybe we'll see some progress at some point but I'm not into these projects.. I'd be more inclined to work on oFono support for it myself ([www.ofono.org](www.ofono.org))

---

### Post by bichofnrise74 on 2011-04-22
Hi Balrog-kun,

So, I have compiled the USBNET and my dmesg output seems better now. But still I don't get the green blinking light. See the output of the logs below.

From dmesg,
> 
[  563.012118] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  578.124219] usb 1-5: device descriptor read/64, error -110
[  578.365016] lg-vl600 1-5:1.0: eth1: register 'lg-vl600' at usb-0000:00:1d.7-5, LG VL600 modem, 64:99:5d:fd:b5:80
[  578.365861] cdc_acm 1-5:1.2: ttyACM0: USB ACM device
[  578.413016] udev: renamed network interface eth1 to eth2
[  587.424101] eth2: no IPv6 routers present


From syslog,
> 
Apr 22 15:27:13 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 22 15:27:33 ubuntu kernel: [ 1167.416236] usb 1-5: new high speed USB device using ehci_hcd and address 5
Apr 22 15:27:48 ubuntu kernel: [ 1182.528188] usb 1-5: device descriptor read/64, error -110
Apr 22 15:27:49 ubuntu kernel: [ 1182.768681] lg-vl600 1-5:1.0: eth1: register 'lg-vl600' at usb-0000:00:1d.7-5, LG VL600 modem, 64:99:5d:fd:b5:80
Apr 22 15:27:49 ubuntu kernel: [ 1182.769612] cdc_acm 1-5:1.2: ttyACM0: USB ACM device
Apr 22 15:27:49 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/eth2, iface: eth2)
Apr 22 15:27:49 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/eth2, iface: eth2): no ifupdown configuration found.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): carrier is OFF
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): new Ethernet device (driver: 'lg-vl600')
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): exported as /org/freedesktop/NetworkManager/Devices/3
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): now managed
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): device state change: 1 -> 2 (reason 2)
Apr 22 15:27:49 ubuntu kernel: [ 1182.813140] udev: renamed network interface eth1 to eth2
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): bringing up device.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): preparing device.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): deactivating device (reason: 2).
Apr 22 15:27:49 ubuntu avahi-daemon[689]: Registering new address record for fe80::6699:5dff:fefd:b580 on eth2.*.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): carrier now ON (device state 2)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): device state change: 2 -> 3 (reason 40)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) starting connection 'Auto eth2'
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): device state change: 3 -> 4 (reason 0)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): device state change: 4 -> 5 (reason 0)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) successful.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
Apr 22 15:27:49 ubuntu NetworkManager: <info>  (eth2): device state change: 5 -> 7 (reason 0)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction (timeout in 45 seconds)
Apr 22 15:27:49 ubuntu NetworkManager: <info>  dhclient started with pid 2114
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Beginning IP6 addrconf.
Apr 22 15:27:49 ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Apr 22 15:27:49 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 22 15:27:49 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 22 15:27:49 ubuntu dhclient: All rights reserved.
Apr 22 15:27:49 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 22 15:27:49 ubuntu dhclient:
Apr 22 15:27:49 ubuntu NetworkManager: <info>  DHCP: device eth2 state changed normal exit -> preinit
Apr 22 15:27:49 ubuntu dhclient: Listening on LPF/eth2/64:99:5d:fd:b5:80
Apr 22 15:27:49 ubuntu dhclient: Sending on   LPF/eth2/64:99:5d:fd:b5:80
Apr 22 15:27:49 ubuntu dhclient: Sending on   Socket/fallback
Apr 22 15:27:50 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
Apr 22 15:27:53 ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Apr 22 15:27:58 ubuntu kernel: [ 1191.824045] eth2: no IPv6 routers present
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Device 'eth2' IP6 addrconf timed out or failed.
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 22 15:27:59 ubuntu NetworkManager: <info>  (eth2): device state change: 7 -> 9 (reason 5)
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Marking connection 'Auto eth2' invalid.
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Activation (eth2) failed.
Apr 22 15:27:59 ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 22 15:27:59 ubuntu NetworkManager: <info>  (eth2): device state change: 9 -> 3 (reason 0)
Apr 22 15:27:59 ubuntu NetworkManager: <info>  (eth2): deactivating device (reason: 0).
Apr 22 15:27:59 ubuntu NetworkManager: <info>  (eth2): canceled DHCP transaction, dhcp client pid 2114

Then, I tried to run your script, then tried to run dhclient but nothing happened. I still had the blue blinking lights.

> 
root@ubuntu:/balrog-kun-LG-VL600-utils-d4f6975# python vl600-attach.py
root@ubuntu:/balrog-kun-LG-VL600-utils-d4f6975# dhclient eth2
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth2/64:99:5d:fd:b5:80
Sending on   LPF/eth2/64:99:5d:fd:b5:80
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Am I missing something obvious? Is there something that I can check?
Also, you mentioned that I should just run 'dhclient' but how would the dongle know that it will connect to Verizon 4g network? Because I used to have a 3g card and I had to configure the Network Manager for the username / password for Verizon.

Also, this aircard works fine when it connects to a Windows XP.

---

### Post by balrog-kun on 2011-04-22
Hi bichofnrise74,

so it looks like the attaching is not working.  I assume that you're in a place with coverage (i.e. it works under windows).  So it might be that the dongle is not compatible or something.. have you upgraded the firmware on your dongle?  I haven't upgraded it on mine, so maybe that's the difference.  Please let us know because it'd be an important data point, has anyone got it working on the new firmware?

If it is the case that the new firmware doesn't work with the old command then, if you have a Windows machine, we could use a usb analyzer logs (software monitor is ok too) to find out the right command for those dongles.

You shouldn't need to use any username or password, I think they might be encoded on the SIM or somewhere, but either way the dongle connects automatically to whatever network is available 3g or 4g regardless.

The dhclient needs to be executed *after* the LED starts blinking green (although from your logs it looks like you have NetworkManager running, which tries to be too smart and runs dhclient automatically, so you'd probably need to kill it ("killall dhclient") when the LED start blinking green and probably NetworkManager will re-run it automatically -- I've never used it so I don't know)

---

### Post by bichofnrise74 on 2011-04-25
Here's the firmware version: VL600ZV3. I think it was upgraded.

I tried to look for a usb log analyzer but couldn't find one that is free. Do you have something specific that I can use?

---

### Post by balrog-kun on 2011-04-25
Mine says:

Model: VL600  136
Revision:  S/W VER:  VL600ZV4

So I suppose I have a later version of the firmware than you have.  Can you try upgrading?  The process is documented somewhere on verizon's website.

As for dumping USB traffic on windows, the wireshark wiki lists some tools: [http://wiki.wireshark.org/Tools#USB_capture](http://wiki.wireshark.org/Tools#USB_capture)
Last time I've done that I think I just ran windows in a virtual machine and hacked qemu to dump usb traffic for me.

---

### Post by bichofnrise74 on 2011-04-28
I have successfully upgraded my firmware to VL600ZV4, but still nothing happens when I run the attach script.Also, I tested the aircard on Windows XP to make sure that it was still working with the new firmware.

I did notice that my model is VL600 without the 136 at the end.

---

### Post by winhtr on 2011-06-26
I am also having problems getting the attach script to work on my lg vl600.  I am running kernel 2.6.39-0, and I can see that the driver is getting loaded:

lsmod | grep lg:

lg_vl600               12663  0 
cdc_ether              13304  1 lg_vl600
usbnet                 25175  2 lg_vl600,cdc_ether

The modem just keeps blinking the blue light after I run vl600-attach.py.

I am also running the VL600ZV4 firmware, and have verified the vl600 works just fine in Windows XP.

---

### Post by Prolixium on 2011-07-09
> **winhtr said:**
> I am also having problems getting the attach script to work on my lg vl600.  I am running kernel 2.6.39-0

Although balrog-kun's patches made it into 2.6.39, I haven't had success using this kernel with the VL600, yet.  The attach script appears to error out (nulls all over the screen) and DHCP fails.  Using a patched 2.6.38 is the only thing that works for me, at this point.

Also, on another note, for those who are using 2.6.38, has anyone been able to receive an IPv6 address via SLAAC with this modem?

The VZAM software on OS X and Windows 7 appears to "activate" IPv6 functionality so that router advertisement packets are sent, which causes IPv6 autoconfiguration in the interface.  I've used rdisc6(8) (part of the ndisc6 package) to manually send router solicitation messages on Linux, but they never trigger any replies.  Manually configuring IPv6 addresses is futile because the prefix, just like the IPv4 address, seems to change for each connection.

I'm assuming that the vl600-attach.py script might need to be modified.. anyone have any ideas?

- Mark

---

### Post by Prolixium on 2011-07-25
> **Prolixium said:**
> Although balrog-kun's patches made it into 2.6.39, I haven't had success using this kernel with the VL600, yet.  The attach script appears to error out (nulls all over the screen) and DHCP fails.  Using a patched 2.6.38 is the only thing that works for me, at this point.

Turns out this is an easy fix, I've submitted a bug against 2.6.39:

[https://bugzilla.kernel.org/show_bug.cgi?id=39952](https://bugzilla.kernel.org/show_bug.cgi?id=39952)

- Mark

---

### Post by theThief on 2011-08-10
Hi balrog, 

I noticed that your patch or a version of it has been pushed to linux-2.6.39.  I downloaded the source and compiled the kernel including the lg-vl600 module.  I can connect my vl600 modem and the green light blinks as well as my wwan0 interface shows that it is up.  My only problem is that I can't get a dhcp address.  I am running Ubuntu 10.04 with linux-2.6.39 and I use dhclient.  Do you have any suggestions?  Is there a specific server I should try to use, right now it seems the dhclient is just broadcasting on 255.255.255.255.

Thanks for any help you might have.

---

### Post by Prolixium on 2011-08-10
> **theThief said:**
> Hi balrog, 

I noticed that your patch or a version of it has been pushed to linux-2.6.39.  I downloaded the source and compiled the kernel including the lg-vl600 module.  I can connect my vl600 modem and the green light blinks as well as my wwan0 interface shows that it is up.  My only problem is that I can't get a dhcp address.  I am running Ubuntu 10.04 with linux-2.6.39 and I use dhclient.  Do you have any suggestions?  Is there a specific server I should try to use, right now it seems the dhclient is just broadcasting on 255.255.255.255.

Thanks for any help you might have.

I mentioned this exact issue in the post before yours.  It's a bug that was introduced that attempts to name the LG-VL600 as wwanX by default, but ends up disassociating the LG-VL600 driver with the USB device entirely:

[https://bugzilla.kernel.org/show_bug.cgi?id=39952](https://bugzilla.kernel.org/show_bug.cgi?id=39952)

Change one line in cdc_ether.c as described in the patch, and it'll work in 2.6.39 (and newer).

- Mark

---

### Post by theThief on 2011-08-10
> **Prolixium said:**
> I mentioned this exact issue in the post before yours.  It's a bug that was introduced that attempts to name the LG-VL600 as wwanX by default, but ends up disassociating the LG-VL600 driver with the USB device entirely:

[https://bugzilla.kernel.org/show_bug.cgi?id=39952](https://bugzilla.kernel.org/show_bug.cgi?id=39952)

Change one line in cdc_ether.c as described in the patch, and it'll work in 2.6.39 (and newer).

- Mark

Thanks for the quick reply, but this isn't the same issue (I don't think, correct me if I am wrong?).  You stated that the attach script failed and that the light still blinked blue.  My attach script works and I blink green, I am just not able to get a response to my DHCPDISCOVER messages.  I tried your patch to ensure that it wouldn't solve my problem and I am having the same issue still.  I can connect to Verizon I just can't get the dhcp communication to work properly.

---

### Post by Prolixium on 2011-08-10
> **theThief said:**
> Thanks for the quick reply, but this isn't the same issue.  You stated that the attach script failed and that the light still blinked blue.  My attach script works and I blink green, I am just not able to get a response to my DHCPDISCOVER messages.  I tried your patch to ensure that it wouldn't solve my problem and I am having the same issue still.  I can connect to Verizon I just can't get the dhcp communication to work properly.

Actually, [winhtr]("http://ubuntuforums.org/member.php?u=1324979") was the one who stated that the attach script failed and the card blinked blue.  Mine blinked green after the attach script ran (correctly), but no other traffic (DHCP requests, IPv6 router solicitations, etc.) worked. This isn't a good sign that it doesn't work for you.  You're getting:

"lg-vl600 1-1:1.0: ethX: register 'lg-vl600' ... "

.. in dmesg when you first plug in the modem, right?

Also, what firmware version are you on?  I wonder if it's something newer, and LG changed some things.

- Mark

---

### Post by theThief on 2011-08-11
Mark

Thanks for the help, my dmesg wasn't reporting that, it was still reporting wwan0 through the cdc_ether.  I might have a slightly different version of the linux-2.6.39 kernel source, because the patch didn't work since that code change was on a slightly different line.  Long story short, I changed the wrong line when I did it manually, I went back and changed the correct line and it does work now!  Thanks!  Just as an FYI, I am running VL600ZV4 as my firmware on the device.  I had to look that up in my Windows VM, do you know how to find that in Ubuntu?

Cheers

---

### Post by Prolixium on 2011-08-11
Ah, glad that it's working now!

You can use the vl600-com.py script to display the version number using some GSM modem commands.  Try using the ATI3 command.  It showed this for me:

```
(evolution:9:54)% ./vl600-com.py
ATI3

Manufacturer: LG Electronics Inc.
Model: VL600  136
Revision:  S/W VER:  VL600ZV4
ESN: 0x80CC4F95
+GCAP: +CIS707-A, +CIS-856, CIS-856-A, +CGSM, +CLTE1

OK

```You can also do some other things like send and receive SMSes, lock your SIM, brick your modem, etc., so be careful.

- Mark

---

### Post by mirrorbox on 2011-08-18
Hi,

I'm trying to get vl600 working as well. I've downloaded kernel 3.0.1:

Linux 3.0.1-030001-generic x86_64

and I was able to do ./vl600-attached.py and dhclient over wwan0 device.

9: wwan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 64:99:5d:fb:07:2f brd ff:ff:ff:ff:ff:ff
    inet 169.254.6.76/16 brd 169.254.255.255 scope link wwan0:avahi
    inet6 fe80::6699:5dff:fefb:72f/64 scope link 
       valid_lft forever preferred_lft forever

However, no traffic goes through. Default route is set for this interface. What could be the problem with that and how could I fix it?

---

### Post by nhsb on 2011-08-29
> **mirrorbox said:**
> 
inet 169.254.6.76/16 brd 169.254.255.255 scope link wwan0:avahi
    
However, no traffic goes through. Default route is set for this interface. What could be the problem with that and how could I fix it?

169.*.*.* is self-assigned address. I guess it doesn't get IP address from DHCP.

---

### Post by kjkeefe on 2011-10-01
Thank you very much for doing so much work on this. I just got my VL600 and I'm really hoping to get it working on Ubuntu. Has there been any progress on making the config process a little more beginner friendly? Thanks!

---

### Post by madhava_28 on 2011-12-01
>>>Turns out this is an easy fix, I've submitted a bug against 2.6.39:
>>>[https://bugzilla.kernel.org/show_bug.cgi?id=39952](https://bugzilla.kernel.org/show_bug.cgi?id=39952)

I could not open the above link. It always fails to connect. 
Can some one share the one line fix in cdc_ether.c file

I have changes the line
.driver_info = (unsigned long)&wwan_info,  as .driver_info = 0;

When I compile the kernel and plug in the modem I see kernel panic

Please see the dmesg below
[   80.967002] WARNING: at net/sched/sch_generic.c:255 dev_watchdog+0x1e6/0x1f0()
[   80.967005] Hardware name: Vostro 3350
[   80.967008] NETDEV WATCHDOG: eth3 (lg-vl600): transmit queue 0 timed out
[   80.967010] Modules linked in: cdc_acm lg_vl600 cdc_ether usbnet binfmt_misc parport_pc ppdev snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec joydev i915 snd_hwdep arc4 usbhid snd_pcm hid iwlagn psmouse aesni_intel cryptd serio_raw snd_seq_midi snd_rawmidi drm_kms_helper snd_seq_midi_event drm aes_i586 snd_seq dell_wmi aes_generic i2c_algo_bit uvcvideo sparse_keymap snd_timer videodev snd_seq_device video lp dell_laptop xhci_hcd snd btusb dcdbas parport mac80211 cfg80211 soundcore snd_page_alloc bluetooth usb_storage uas ahci libahci r8169
[   80.967059] Pid: 0, comm: kworker/0:0 Not tainted 3.1.4-lg1 #2
[   80.967061] Call Trace:
[   80.967068]  [<c1048842>] warn_slowpath_common+0x72/0xa0
[   80.967072]  [<c1456a36>] ? dev_watchdog+0x1e6/0x1f0
[   80.967075]  [<c1456a36>] ? dev_watchdog+0x1e6/0x1f0
[   80.967079]  [<c1048913>] warn_slowpath_fmt+0x33/0x40
[   80.967083]  [<c1456a36>] dev_watchdog+0x1e6/0x1f0
[   80.967088]  [<c1056b24>] run_timer_softirq+0xf4/0x2b0
[   80.967093]  [<c10aea59>] ? __rcu_process_callbacks+0x49/0x300
[   80.967096]  [<c1456850>] ? netif_carrier_off+0x30/0x30
[   80.967100]  [<c104f352>] __do_softirq+0x82/0x170
[   80.967104]  [<c15087ad>] ? asiliantfb_pci_init+0x66/0x392
[   80.967108]  [<c10acf34>] ? irq_node_proc_open+0x14/0x20
[   80.967112]  [<c104f2d0>] ? send_remote_softirq+0x50/0x50
[   80.967114]  <IRQ>  [<c104f666>] ? irq_exit+0x76/0xa0
[   80.967121]  [<c15248c9>] ? smp_apic_timer_interrupt+0x59/0x88
[   80.967126]  [<c151db99>] ? apic_timer_interrupt+0x31/0x38
[   80.967130]  [<c104007b>] ? proc_sched_show_task+0x16cb/0x1a70
[   80.967135]  [<c12bed28>] ? intel_idle+0xb8/0x110
[   80.967140]  [<c1409f0d>] ? cpuidle_idle_call+0x9d/0x100
[   80.967144]  [<c10018d7>] ? cpu_idle+0x97/0xe0
[   80.967148]  [<c1515ca8>] ? setup_APIC_timer+0x5c/0x60
[   80.967152]  [<c151532e>] ? start_secondary+0x1e0/0x1e7
[   80.967156] ---[ end trace daf5bce0fb62e797 ]---


Please let me know if I missed anything.

---

### Post by Prolixium on 2011-12-01
> **madhava_28 said:**
> >>>Turns out this is an easy fix, I've submitted a bug against 2.6.39:
>>>[https://bugzilla.kernel.org/show_bug.cgi?id=39952](https://bugzilla.kernel.org/show_bug.cgi?id=39952)

I could not open the above link. It always fails to connect. 
Can some one share the one line fix in cdc_ether.c file

I have changes the line
.driver_info = (unsigned long)&wwan_info,  as .driver_info = 0;

When I compile the kernel and plug in the modem I see kernel panic

Please see the dmesg below
[   80.967002] WARNING: at net/sched/sch_generic.c:255 dev_watchdog+0x1e6/0x1f0()
[   80.967005] Hardware name: Vostro 3350
[   80.967008] NETDEV WATCHDOG: eth3 (lg-vl600): transmit queue 0 timed out
[   80.967010] Modules linked in: cdc_acm lg_vl600 cdc_ether usbnet binfmt_misc parport_pc ppdev snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec joydev i915 snd_hwdep arc4 usbhid snd_pcm hid iwlagn psmouse aesni_intel cryptd serio_raw snd_seq_midi snd_rawmidi drm_kms_helper snd_seq_midi_event drm aes_i586 snd_seq dell_wmi aes_generic i2c_algo_bit uvcvideo sparse_keymap snd_timer videodev snd_seq_device video lp dell_laptop xhci_hcd snd btusb dcdbas parport mac80211 cfg80211 soundcore snd_page_alloc bluetooth usb_storage uas ahci libahci r8169
[   80.967059] Pid: 0, comm: kworker/0:0 Not tainted 3.1.4-lg1 #2
[   80.967061] Call Trace:
[   80.967068]  [<c1048842>] warn_slowpath_common+0x72/0xa0
[   80.967072]  [<c1456a36>] ? dev_watchdog+0x1e6/0x1f0
[   80.967075]  [<c1456a36>] ? dev_watchdog+0x1e6/0x1f0
[   80.967079]  [<c1048913>] warn_slowpath_fmt+0x33/0x40
[   80.967083]  [<c1456a36>] dev_watchdog+0x1e6/0x1f0
[   80.967088]  [<c1056b24>] run_timer_softirq+0xf4/0x2b0
[   80.967093]  [<c10aea59>] ? __rcu_process_callbacks+0x49/0x300
[   80.967096]  [<c1456850>] ? netif_carrier_off+0x30/0x30
[   80.967100]  [<c104f352>] __do_softirq+0x82/0x170
[   80.967104]  [<c15087ad>] ? asiliantfb_pci_init+0x66/0x392
[   80.967108]  [<c10acf34>] ? irq_node_proc_open+0x14/0x20
[   80.967112]  [<c104f2d0>] ? send_remote_softirq+0x50/0x50
[   80.967114]  <IRQ>  [<c104f666>] ? irq_exit+0x76/0xa0
[   80.967121]  [<c15248c9>] ? smp_apic_timer_interrupt+0x59/0x88
[   80.967126]  [<c151db99>] ? apic_timer_interrupt+0x31/0x38
[   80.967130]  [<c104007b>] ? proc_sched_show_task+0x16cb/0x1a70
[   80.967135]  [<c12bed28>] ? intel_idle+0xb8/0x110
[   80.967140]  [<c1409f0d>] ? cpuidle_idle_call+0x9d/0x100
[   80.967144]  [<c10018d7>] ? cpu_idle+0x97/0xe0
[   80.967148]  [<c1515ca8>] ? setup_APIC_timer+0x5c/0x60
[   80.967152]  [<c151532e>] ? start_secondary+0x1e0/0x1e7
[   80.967156] ---[ end trace daf5bce0fb62e797 ]---


Please let me know if I missed anything.

Looks like bugzilla.kernel.org is hosed at the moment.  I'd recommend using the following full patches, since they contains a stability fix in the case of corrupted packets and fix the LG-VL600 being marked as wwan:

[https://lkml.org/lkml/2011/8/6/131](https://lkml.org/lkml/2011/8/6/131)
[https://lkml.org/lkml/2011/11/9/380](https://lkml.org/lkml/2011/11/9/380)

I've submitted all of the above to the Linux kernel, and they've been applied in linux-next, I believe.  Hopefully 3.2 won't require any patching!

- Mark

---

### Post by madhava_28 on 2011-12-01
Mark,

Thank you for the help.
I was able to get the modem connected with the patches using wwan interface.
However there seems to be some issue with the coexistence with Wifi.

I have done the following testing.
Connect WiFi and run ping with WiFi Interface ping [www.google.com](www.google.com) -I wlan0

Now plug in the LG modem and run the script, when the green light starts blinking, ping through the wlan0 interface stops. and I ping fails with wwan0 interface also.

When the LG modem is unplugged and replugged again ping was successful with wwan0 interface.

Is this a limitation with Modem.  Originally I had 2.6.38 kernel version, I have downloaded 3.1.4 version of kernel and applied the patches.

Thanks,
Madhava

---

### Post by Prolixium on 2011-12-02
> **madhava_28 said:**
> Mark,

Thank you for the help.
I was able to get the modem connected with the patches using wwan interface.
However there seems to be some issue with the coexistence with Wifi.

I have done the following testing.
Connect WiFi and run ping with WiFi Interface ping [www.google.com]("http://www.google.com") -I wlan0

Now plug in the LG modem and run the script, when the green light starts blinking, ping through the wlan0 interface stops. and I ping fails with wwan0 interface also.

When the LG modem is unplugged and replugged again ping was successful with wwan0 interface.

Is this a limitation with Modem.  Originally I had 2.6.38 kernel version, I have downloaded 3.1.4 version of kernel and applied the patches.

Thanks,
Madhava

Hmm, first off, I think having both Wi-Fi and the LG modem enabled w/both addressed by DHCP is not the best scenario (or Wi-Fi and wired Ethernet, etc.).  You'll have two default routes and connections that bind to the IP of one of the interfaces may send packets out the other interface in a round-robin fashion (I think), making it look like the source address is spoofed.

Although I haven't tried your exact scenario, I think I have a guess why your ping commands stop working.  Verizon's LTE service seems to immediately drop the connection if it sees a packet sourcing from an IPv4 address other than the one received by DHCP.  I hit this when testing some things with OpenVPN and I had my tun0 IP traffic routed out wwan0 by accident.  It can also happen with iptables and SNAT rules if you don't drop INVALID packets on the internal interface (some packets will leak through untranslated).

It's not specific to the LG-VL600 since it happened to me with the Pantech UML290 too.  I had the same problem on Mac OS X with the LG-VL600, as well.

Yes, it does require a replug of the USB modem, unfortunately.

I'm guessing that you've got some traffic that's leaking out wwan0 with a source IP that's bound to your wlan0 interface, most likely your ping traffic causing Verizon to terminate the connection.  With two default routes, the -I flag might not help, it'll just set the source IPv4 address to whatever's on the interface you specify, but the packets might still be sent out the wrong interface.

If you're curious about this, bring up wlan0 and wwan0, start a tcpdump on wwan0, then issue the ping commands to nuke the wwan0 connection.  Most likely you'll see some packets leaving wwan0 with the wlan0 source IP.

Hope this helps.. 

- Mark

---

### Post by jwilliams77006 on 2012-03-26
> **kjkeefe said:**
> Thank you very much for doing so much work on this. I just got my VL600 and I'm really hoping to get it working on Ubuntu. Has there been any progress on making the config process a little more beginner friendly? Thanks!

I have taken the plunge away from Windows, and have been following this thread carefully.  As a noob, I would love a bit more info on the procedure for getting the VL600 to work on Ubuntu 10.0

---

