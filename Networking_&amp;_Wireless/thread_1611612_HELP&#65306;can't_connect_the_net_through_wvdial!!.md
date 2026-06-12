---
title: "HELP&#65306;can't connect the net through wvdial!!!!"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by yyyoabc on 2010-11-02
My kernel is 2.6.16 in Ubuntu 8.04, the 3G card is ec169. and there are ttyUSB0/1/2 when i plug in the card.

But again ,it seems that my problem turns to wvdial cause each time i dial, it may setup a link "ppp0" (sometime even a "ppp0" can't be setup) ,but just no sending or receiving data . It could not be the problem of the card since it can work fine on Windows. Could anybody check the dialing message for me ? Thank  you  much. 
 
> root@lee1-desktop:~/deskstop/usb# wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
^MODE: 8 
^RSSILVL:20 
^HRSSILVL:40 
CONNECT 
--> Carrier detected.  Waiting for prompt. 
^HRSSILVL:40 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Starting pppd at Tue Nov  2 15:11:25 2010 
--> Pid of pppd: 15211 
--> Using interface ppp0 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> local  IP address 118.115.177.112 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> remote IP address 172.22.212.124 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> primary   DNS address 61.139.2.69 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> secondary DNS address 202.98.96.68 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> Connect time 5.5 minutes. 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> Disconnecting at Tue Nov  2 15:17:01 2010 
--> The PPP daemon has died: A modem hung up the phone (exit code = 16) 
--> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 5 seconds 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
^MODE: 2 
^RSSILVL:20 
^HRSSILVL:0 
CONNECT 
--> Carrier detected.  Waiting for prompt. 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Starting pppd at Tue Nov  2 15:17:49 2010 
--> Pid of pppd: 15313 
--> Using interface ppp0 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> local  IP address 118.115.177.112 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> remote IP address 172.22.212.124 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> primary   DNS address 61.139.2.69 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08] 
--> secondary DNS address 202.98.96.68 
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]  
 
And it just stop there ,no moving forward until i cut it down.The pre DNS and sec DNS are written by me in /etc/resolv.conf cause if not so ,it can't even set up a "pppd" . 
I believe that it was not the problem of signal cause it connect quite well on Windows.
These are info in /var/log/messages:, any help or advice is warmly welcome.
 
> 
Nov  2 15:11:25 lee1-desktop pppd[15211]: pppd 2.4.4 started by root, uid 0 
Nov  2 15:11:25 lee1-desktop pppd[15211]: Using interface ppp0 
Nov  2 15:11:25 lee1-desktop pppd[15211]: Connect: ppp0 <--> /dev/ttyUSB0 
Nov  2 15:11:25 lee1-desktop pppd[15211]: CHAP authentication succeeded 
Nov  2 15:11:25 lee1-desktop pppd[15211]: CHAP authentication succeeded 
Nov  2 15:11:25 lee1-desktop pppd[15211]: local  IP address 118.115.177.112 
Nov  2 15:11:25 lee1-desktop pppd[15211]: remote IP address 172.22.212.124 
Nov  2 15:11:25 lee1-desktop pppd[15211]: primary   DNS address 61.139.2.69 
Nov  2 15:11:25 lee1-desktop pppd[15211]: secondary DNS address 202.98.96.68 
Nov  2 15:16:55 lee1-desktop pppd[15211]: No response to 4 echo-requests 
Nov  2 15:16:55 lee1-desktop pppd[15211]: Serial link appears to be disconnected. 
Nov  2 15:16:55 lee1-desktop pppd[15211]: Connect time 5.5 minutes. 
Nov  2 15:16:55 lee1-desktop pppd[15211]: Sent 0 bytes, received 0 bytes. 
Nov  2 15:17:01 lee1-desktop pppd[15211]: Connection terminated. 
Nov  2 15:17:01 lee1-desktop pppd[15211]: Modem hangup 
Nov  2 15:17:01 lee1-desktop pppd[15211]: Exit. 
Nov  2 15:17:49 lee1-desktop pppd[15313]: pppd 2.4.4 started by root, uid 0 
Nov  2 15:17:49 lee1-desktop pppd[15313]: Using interface ppp0 
Nov  2 15:17:49 lee1-desktop pppd[15313]: Connect: ppp0 <--> /dev/ttyUSB0 
Nov  2 15:17:50 lee1-desktop pppd[15313]: CHAP authentication succeeded 
Nov  2 15:17:50 lee1-desktop pppd[15313]: CHAP authentication succeeded 
Nov  2 15:17:50 lee1-desktop pppd[15313]: local  IP address 118.115.177.112 
Nov  2 15:17:50 lee1-desktop pppd[15313]: remote IP address 172.22.212.124 
Nov  2 15:17:50 lee1-desktop pppd[15313]: primary   DNS address 61.139.2.69 
Nov  2 15:17:50 lee1-desktop pppd[15313]: secondary DNS address 202.98.96.68 
Nov  2 15:26:29 lee1-desktop pppd[15313]: Terminating on signal 15 
Nov  2 15:26:29 lee1-desktop pppd[15313]: Connect time 8.7 minutes. 
Nov  2 15:26:29 lee1-desktop pppd[15313]: Sent 0 bytes, received 0 bytes.

Another odd thing is that when i just plug in and wait a while, there is no ttyUSB*, but when i run the code below , ttyUSB0/1/2 showed up although the running results show that it was unsuccessful. I am curious that whether the manual code just spur the auto-switching process. [IMG]http://www.draisberghof.de/usb_modeswitch/bb/images/smiles/icon_question.gif[/IMG] 
 
> root@lee1-desktop:~/deskstop/usb# usb_modeswitch -W -c /etc/usb_modeswitch.setup 
Reading config file: /etc/usb_modeswitch.setup 
 * usb_modeswitch: handle USB devices with multiple modes 
 * Version 1.1.4 (C) Josua Dietze 2010 
 * Based on libusb0 (0.1.12 and above) 
 
 ! PLEASE REPORT NEW CONFIGURATIONS ! 
 
DefaultVendor=  0x12d1 
DefaultProduct= 0x1001 
TargetVendor=   not set 
TargetProduct=  not set 
TargetClass=    0xff 
TargetProductList="" 
 
DetachStorageOnly=0 
HuaweiMode=1 
SierraMode=0 
SonyMode=0 
GCTMode=0 
MessageEndpoint=  not set 
MessageContent="" 
NeedResponse=0 
ResponseEndpoint= not set 
Interface=0x00 
 
InquireDevice enabled (default) 
Success check disabled 
System integration mode disabled 
 
usb_set_debug: Setting debugging level to 15 (on) 
usb_os_find_busses: Found 002 
usb_os_find_busses: Found 001 
usb_os_find_devices: Found 001 on 002 
usb_os_find_devices: Found 018 on 001 
usb_os_find_devices: Found 002 on 001 
usb_os_find_devices: Found 001 on 001 
error obtaining child information: Inappropriate ioctl for device 
 
Looking for target devices ... 
  searching devices, found USB ID 0000:0000 
  searching devices, found USB ID 12d1:1001 
   found matching vendor ID 
   found matching product ID 
   target class ff not matching 
  searching devices, found USB ID 0e0f:0002 
  searching devices, found USB ID 0000:0000 
 No devices in target mode or class found 
Looking for default devices ... 
  searching devices, found USB ID 0000:0000 
  searching devices, found USB ID 12d1:1001 
   found matching vendor ID 
   found matching product ID 
   target class ff not matching 
   adding device as default 
  searching devices, found USB ID 0e0f:0002 
  searching devices, found USB ID 0000:0000 
 Found devices in default mode or class (1) 
Accessing device 018 on bus 001 ... 
Using endpoints 0x08 (out) and 0x87 (in) 
Using endpoints 0x08 (out) and 0x87 (in) 
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
Manufacturer: HUA&#65533;WEI TECHNOLOGIES 
     Product: HUAWEI Mobile 
  Serial No.: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 
------------------------- 
Sending Huawei control message ... 
USB error: error sending control message: Invalid or incomplete multibyte or wide character 
Error: sending Huawei control message failed (error -84). Aborting.


---

