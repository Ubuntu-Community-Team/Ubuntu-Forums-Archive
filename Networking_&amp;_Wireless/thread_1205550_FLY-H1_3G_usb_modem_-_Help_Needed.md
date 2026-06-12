---
title: "FLY-H1 3G usb modem - Help Needed"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by wolfpret on 2009-07-06
[B][SIZE=3]Hi there,

I am a new Ubuntu 9.04 user (total newbie), and am having trouble getting my FLY-H1 usb modem to work. The Ubuntu installation is stand alone on a pc, no other os on the hard drive. Here is a diagnostic report gotten under windows on a diferent pc for the modem:[/SIZE][/B]

------------------------------------------------------------------------------
Modem Information
Modem name : MTC HSDPA USB Modem
At port : COM 13
Firmware version : LQA0011.1.1_M531C
IMEI : 35###########24
IMSI : 64###########26
------------------------------------------------------------------------------
Operator Information
PIN code status : READY
Network code : 64901
Network selection mode : Manual
Network mode : GSM
Signal strength : 59
------------------------------------------------------------------------------
Network Status
CS network registration : Registered,Home PLMN
PS network registration : Registered,Home PLMN
PS network attachment : Attached

**[SIZE=3]On the web I found the following information regarding the modem:[/SIZE]**

Item         Description 
Model     FLY-H1 HSDPA USB Modem    "A portable and high speed internet access mode for office and home;
CD-free auto installation and Multi freqbands"
Technical Standard    HSDPA    3GPP R5, up to 3.6 Mbps DL and 384 Kbps UL, category 5/6
    UMTS    up to 384 Kbps DL and UL
    EDGE    3GPP Release4, class 12, up to 237 Kbps DL and 118Kbps UL
    GPRS    up to 85, 6 Kbps DL and 42, 8 Kbps UL
Frequency  Band     GSM/GPRS/EDGE    900/1800/1900 MHz
    UMTS    850 only or 1900 only or 2100 only or 850/2100 or 850/1900 or 900/2100 
External Interface    Antenna    Internal antenna
    USB     Standard USB interface: supporting USB 2.0 Full Speed
    Power    Powered via the USB interface
    SIM/USIM Card    standard 6 PIN SIM card interface, compaliant with 3GPP 31.101 and 31.102
    AT Interface     support 3GPP TS27.005/3GPP TS27.007
Main Features    Zero-CDROM autoinstallation    support 
    Dimension (mm)     64.7(D)×25.5(W)×10.6(H)(USB Head not included)
    Weight (g)     30
    One RGB LED    RGB LED indicates different state.
    SIM/USIM Pin lock    enable/disable
    SMS and Data service simultaneously Operation    support
    _Operate system    Win2000 / XP/ VISTA, MAC, Linux_      <---
    Languages support    English, Simple Chinese, Traditional Chinese, more languages could be support upon requested
    Memory    Built-in flash, up to 4G; 
    _Hardware Platform    Qualcomm MSM6260_                     <---
Phone Book    Phone Book Capability     100 in Modem
    vCard version    2.1/3.0
    new contacts    support 
    edit contacts    support 
    delete contacts    support 
    send SMS    support 
    move between Modem, SIM card and PC    support 
SMS    SMS Capability    255 in Modem
    Group messages    support
    new SMS    support
    send SMS    support
    save SMS to drafts    support
    reply SMS    support
    forward SMS    support
    delete SMS    support
    import from SIM/Modem to PC    support

**[SIZE=3]I have installed usb_modeswitch, configured it, and when I just plug in the modem the computer sees it as a storage device, and when I do a lsusb I get the following :[/SIZE]**

wynand@Desktop:~$ lsusb

Bus 002 Device 002: ID 08ec:0845 M-Systems Flash Disk Pioneers 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 1c9e:1001                                               <-- My Modem
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**[SIZE=3]Then I run usb_modeswitch:[/SIZE]**

wynand@Desktop:~$ sudo /usr/sbin/usb_modeswitch  /etc/usb_modeswitch.conf

 
* usb_modeswitch: tool for controlling "flip flop" mode USB devices * Version 1.0.2 (C) 
Josua Dietze 2009 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found

Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 007 ...
Using endpoints 0x05 (out) and 0x84 (in)

Inquiring device details; 
driver will be detached ...
Looking for active driver ...
 OK, 
driver found ("usb-storage")
 OK, driver "usb-storage" detached


Received inquiry data 
(detailed identification)
-------------------------
 Vendor String: USBModem
 Product String: Disk   
 Revision String: 1.00
-------------------------


Device description data (identification)
-------------------------
Manufacturer: USB Modem
Product: USB MMC Storage 
Serial No.: 000000000002
-------------------------

Setting up communication with interface 0 ...

Trying to send the message to endpoint 0x05 ...
 OK, 
message successfully sent
-> Run lsusb to note any changes. Bye.


**[SIZE=3]Then I run lsusb again :[/SIZE]**

wynand@Desktop:~$ lsusb

Bus 002 Device 002: ID 08ec:0845 M-Systems Flash Disk Pioneers 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 1c9e:6061                                    <-- Switched Modem
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[SIZE=3]
[B]The modem now regesters itself on the network (led goes from red to purple) but network manager doesn't see the modem, I don't get an automated "found wireless connection" and even when I set up one manually, I don't get anything.

Now, my question is, how do I get Ubuntu to see and use my modem? 

This is the usb_modeswitch.conf file :[/B][/SIZE]

DefaultVendor=  0x1c9e
DefaultProduct= 0x1001

TargetVendor=   0x1c9e
TargetProduct=  0x6061

MessageEndpoint=0x05

MessageContent="55534243123456780000000000000606f50402527000000000000000000000"


**[SIZE=3]I also attempted to automate the usb_modeswitch with the folowing rule:[/SIZE]**

90-Fly.rules

SUBSYSTEM=="usb", SYSFS{idProduct}=="1001", SYSFS{idVendor}=="1c9e"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

[B][SIZE=3]I have tried to give as much information as possible, but if anyone need more, please ask and I will do my best to comply. I realy am scratching my head untill it bleeds, but can find no answer. Is there maybe a tutorial I do not know of that can be followed? 

After some tinkering, I have the automation working, when I plug in the modem it switches automatically, and in dmesg it states that "generic serial attached to ttyUSB0, 1, 2. Is that good or not? 
[/SIZE][/B]

---

### Post by wolfpret on 2009-07-07
Quick update, I updated Ubuntu with update manager using a wired lan connection to my windows pc, after update finished, restarted the pc, and tried again to use the modem, no luck. Then installed GnomePPP, but still no success... This is must be sovleable, many people use usb modems on there ubuntu boxes, so mine must be able to work!!!! Just need a helping hand to guide me in the right direction.......

---

### Post by Rhubarb on 2009-07-07
I'm not too familiar with that model usb 3G modem.
I'm currently using a Huawei 160G modem and it's working beautifully.

Last year before the network manager had USB 3G support in Ubuntu, I used to use KPPP to do it all.
Check your log files as it may help you ascertain the problem (if you haven't already done so).
System --> Administration --> Log File Viewer.

I can't help you much more than that I'm afraid.

---

### Post by Charles Verrall on 2009-09-28
Hi there.
 
I've got the same problem as you!
I've installed ubuntu ultimate edition 2.2 on my spare hard drive and also have a Flycard FLY-H1 modem. It works 100% on my windows installation, but won't work on my ubuntu. When I plug it in, ubuntu registers it as a cd-rom disc with the name "MODEM". If I right-click on it and choose to open it with the "wine-doors windows program loader", then I can install the modem's built-it software on a "virtual C Drive" that is created by the wine doors application. Once the installation has finished, wine doors runs the modem's software, but a message that reads "drivers load FAILED" appears. The Flycard application then runs as it would on a windows machine, but the status window reads "no device".
 
I have been informed that the modem WIll NOT WORK using "wine doors" because any software installed using wine doors cannot communicate directly with it's associated hardware. I must try use linux software (if any available) to make the modem work properly.
 
If I find any useful information or resolutions regarding this, I will be sure to pass it on to you.:)

---

### Post by wolfpret on 2009-09-29
Thank you very much Charles, any and all help is extremely appreciated... Still haven't gotten mine to work either...

---

