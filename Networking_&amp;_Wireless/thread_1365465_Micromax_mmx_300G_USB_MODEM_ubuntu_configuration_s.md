---
title: "Micromax mmx 300G USB MODEM ubuntu configuration solved"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by uttam_kumar on 2009-12-27
Hi Dear Readers

      I have taken a new micromax usb HSPA modem.  But i was unable to use Internet through this becz its driver of Linux version was till now not launched.But reading a lot 
of blog n doing a lot of try i manage to work it.
                                   Here is the solution...............................
1.First go to this [COLOR=Red]www.draisberghof.de/usb_[/COLOR]**[COLOR=Red]modeswitch[/COLOR] **site n install  USB_MODESWITCH accordingly.
2.Edit   /etc/usb_modeswitch.conf (sudo gedit /etc/usb_modeswitch.conf) like below for Micromax MMX 300G

[COLOR=Black]######################################################## 
# MobiData MBD-200HU (aka 4G XS Stick W10/W14, aka Micromax MMX 300G,
# aka ChinaBird CBCPL68)
# 
# Contributor: Chris

DefaultVendor=  0x1c9e 
DefaultProduct= 0xf000

TargetVendor=   0x1c9e
TargetProduct=  0x9603

MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"



3.Setting o[/COLOR]f etc/wvdial.conf is
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","gprseast.cellone.in"<...........replace by ur APN
Password =                                                         <............ur password.
Phone = *99***#                                            <........u can also try *99#,*99***1# etc 
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 9600
New PPD = yes
Dial Attempts = 1
Modem = /dev/ttyUSB2
ISDN = 0
Username =                                                        <................ur username

4[COLOR=DarkOrange].Serial wise use commands
[/COLOR][COLOR=Lime][COLOR=DarkOrange]1.......root@uttam-deepi:~# lsusb
Bus 002 Device 003: ID 1c9e:f000 ...................................default vendor:product IDS
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[/COLOR]
2..m[COLOR=DarkOrange]odprobe usbserial vendor=0x1c9e product=0x9603[/COLOR]....................Target product ID

3.[COLOR=DarkOrange]root@uttam-deepi:~# sudo usb_modeswitch

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: USBModem
   Model String: Disk            
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 000000000000
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.


4...root@uttam-deepi:~# lsusb
Bus 002 Device 004: ID 1c9e:9603....................[COLOR=Black]Product ID changed. [/COLOR] 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

5.Now open a new terminal from root.( every command try from Root.)

root@uttam-deepi:~# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATS7=60 S30=0 S0=0
ATS7=60 S30=0 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","gprseast.cellone.in"
AT+CGDCONT=1,"IP","gprseast.cellone.in"
OK
--> Modem initialized.
--> Sending: ATDT*99***#
--> Waiting for carrier.
ATDT*99***#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Dec 27 09:17:27 2009
--> Pid of pppd: 4872
--> Using interface ppp0
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> local  IP address 10.64.6.234
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> remote IP address 10.64.64.64
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> primary   DNS address 218.248.255.161
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 
--> secondary DNS address 218.248.240.180
--> pppd: &#65533;[0f]&#65533;&#65533;[08]&#65533;&#65533; &#65533;&#65533;&#65533; 

[COLOR=Black]Now its got  connected once u got the IP  n DNS.


Thanks to all.
[/COLOR]
[/COLOR]

---

### Post by gaigoleb2 on 2011-07-02
Well explained post. Can also also refer another url for more explanation
[http://hashprompt.blogspot.com](http://hashprompt.blogspot.com)

---

