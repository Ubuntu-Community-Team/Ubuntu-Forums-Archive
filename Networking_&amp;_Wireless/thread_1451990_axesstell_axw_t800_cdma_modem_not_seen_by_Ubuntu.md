---
title: "axesstell axw t800 cdma modem not seen by Ubuntu"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by raydux on 2010-04-11
After spending months trying to get this modem to work by reading everything I can find remotely similar to my situation, I have finally decided to pester someone else with this..
 I am in Belize using an Axesstel AXW-T800 (CDMA wireless) connected to my serial port (com1 in xp, ttyS0 in linux speak). It works fine in XP, I do have to add the extra command "AT+CRM=1" for it to work in XP. Right now I am using Dual-boot with XP, the only way I can get online right now.. The ISP says they have no clue about Linux... The modem has a tiny sticker on it saying  "CDMA by Qualcomm" So I asummed it would be a qualcomm chipset. I am running Ubuntu 6.06.1 I will update when I can get it online, I installed from the LiveCD.
 This is the only option I have as a modem since there are no wire-lines in my part of the jungle. 
 HELP!!!! I need to get away from Microsoft op systems as I can no longer keep up with the endless security updates.Ten or so Malware files found each day, Windows downloading continuously on my slow connection, hogging the little bandwidth I already have, etc.,..:(
 Anybody out there can steer me in the right direction, please do.

---

### Post by alexfish on 2010-04-11
Hi

Don't know this modem however lets see if the modem is seen on the system, if it is recognised then it may be possible to us gnomeppp or wvdial to make the connection

From the terminal enter this command and post the results 

Code:

dmesg | grep -e "modem" -e "tty" 

this will just give you the lines including **modem**. and may also show if any drivers have been loaded

also to monitor what is happening from a separate terminal

tail -f /var/log/syslog

thanks in advance

alexfish

---

### Post by raydux on 2010-04-11
Thanks a bunch Alexfish, I tried what you suggested and this is what I got:
dmesg | grep -e "modem" -e "tty" 

$ dmesg | grep -e "modem" -e "tty"
[17179575.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.588000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.592000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.592000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

tail -f /var/log/syslog

PPP generic driver version 2.4.2
Apr 11 14:41:14 localhost pppd[19930]: pppd 2.4.4b1 started by root, uid 0
Apr 11 14:41:15 localhost chat[20021]: timeout set to 60 seconds
Apr 11 14:41:15 localhost chat[20021]: abort on (ERROR)
Apr 11 14:41:15 localhost chat[20021]: abort on (BUSY)
Apr 11 14:41:15 localhost chat[20021]: abort on (VOICE)
Apr 11 14:41:15 localhost chat[20021]: abort on (NO CARRIER)
Apr 11 14:41:15 localhost chat[20021]: abort on (NO DIALTONE)
Apr 11 14:41:15 localhost chat[20021]: abort on (NO DIAL TONE)
Apr 11 14:41:15 localhost chat[20021]: abort on (NO ANSWER)
Apr 11 14:41:15 localhost chat[20021]: send (ATZ^M)
Apr 11 14:41:16 localhost chat[20021]: send (AT&FH0L3^M)
Apr 11 14:41:16 localhost chat[20021]: expect (OK)
Apr 11 14:41:16 localhost chat[20021]: ^M
Apr 11 14:41:16 localhost chat[20021]: OK
Apr 11 14:41:16 localhost chat[20021]:  -- got it
Apr 11 14:41:16 localhost chat[20021]: send (ATDT#777^M)
Apr 11 14:41:16 localhost chat[20021]: timeout set to 75 seconds
Apr 11 14:41:16 localhost chat[20021]: expect (CONNECT)
Apr 11 14:41:16 localhost chat[20021]: ^M
Apr 11 14:42:31 localhost chat[20021]: alarm
Apr 11 14:42:31 localhost chat[20021]: Failed
Apr 11 14:42:31 localhost pppd[19930]: Connect script failed




Apr 11 15:20:43 localhost pppd[14871]: Device ttyS0 is locked by pid 2084
Apr 11 15:20:49 localhost pppd[3003]: Device ttyS0 is locked by pid 2084
Apr 11 15:21:13 localhost pppd[14871]: Device ttyS0 is locked by pid 2084
Apr 11 15:21:19 localhost pppd[3003]: Device ttyS0 is locked by pid 2084
Apr 11 15:21:29 localhost chat[13701]: alarm
Apr 11 15:21:29 localhost chat[13701]: Failed
Apr 11 15:21:29 localhost pppd[2084]: Connect script failed
Apr 11 15:21:44 localhost chat[17202]: timeout set to 60 seconds
Apr 11 15:21:44 localhost chat[17202]: abort on (ERROR)
Apr 11 15:21:44 localhost chat[17202]: abort on (BUSY)
Apr 11 15:21:44 localhost chat[17202]: abort on (VOICE)
Apr 11 15:21:44 localhost chat[17202]: abort on (NO CARRIER)
Apr 11 15:21:44 localhost chat[17202]: abort on (NO DIALTONE)
Apr 11 15:21:44 localhost chat[17202]: abort on (NO DIAL TONE)
Apr 11 15:21:44 localhost chat[17202]: abort on (NO ANSWER)
Apr 11 15:21:44 localhost chat[17202]: send (ATZ^M)
Apr 11 15:21:44 localhost chat[17202]: send (AT&FH0L3^M)
Apr 11 15:21:45 localhost chat[17202]: expect (OK)
Apr 11 15:21:45 localhost chat[17202]: ATZ^M^M
Apr 11 15:21:45 localhost chat[17202]: ERROR
Apr 11 15:21:45 localhost chat[17202]:  -- failed
Apr 11 15:21:45 localhost chat[17202]: Failed (ERROR)
Apr 11 15:21:45 localhost pppd[14871]: Connect script failed
Apr 11 15:21:50 localhost chat[17396]: timeout set to 60 seconds
Apr 11 15:21:50 localhost chat[17396]: abort on (ERROR)
Apr 11 15:21:50 localhost chat[17396]: abort on (BUSY)
Apr 11 15:21:50 localhost chat[17396]: abort on (VOICE)
Apr 11 15:21:50 localhost chat[17396]: abort on (NO CARRIER)
Apr 11 15:21:50 localhost chat[17396]: abort on (NO DIALTONE)
Apr 11 15:21:50 localhost chat[17396]: abort on (NO DIAL TONE)
Apr 11 15:21:50 localhost chat[17396]: abort on (NO ANSWER)
Apr 11 15:21:50 localhost chat[17396]: send (ATZ^M)
Apr 11 15:21:50 localhost chat[17396]: send (AT&FH0L3^M)
Apr 11 15:21:50 localhost chat[17396]: expect (OK)
Apr 11 15:21:50 localhost chat[17396]: ATZ^M^M
Apr 11 15:21:50 localhost chat[17396]: OK
Apr 11 15:21:50 localhost chat[17396]:  -- got it
Apr 11 15:21:50 localhost chat[17396]: send (ATDT#777^M)
Apr 11 15:21:51 localhost chat[17396]: timeout set to 75 seconds
Apr 11 15:21:51 localhost chat[17396]: expect (CONNECT)
Apr 11 15:21:51 localhost chat[17396]: ^M
Apr 11 15:22:00 localhost pppd[2084]: Device ttyS0 is locked by pid 3003



All of this is pretty much like reading Chinese to me, but I do notice that there is no mention of anything resembling a modem anywhere... And I thought having a serial port modem would make things easy:(
 I do know that the ISP that sells these modems also supplies them with usb cables for other cusomers.. Would it be easier to use a usb cable for this?
 Alexfish, thanks again for your help.

---

### Post by alexfish on 2010-04-11
Hi

It is possible USB may provide more info , or better configuration with Ubuntu, but can't say

if you use the usb connection the device ID's may show up with this code from the terminal

Code:

lsusb

then follow the above again, also from the info above the system is seeing some device attached to the serial port. and has received a response from it,  , also ensure to kill the ppp as from part of the messages indicates some process is still holding onto the modem. may be the dialup needs configuring to suit your service provider but will looked at this later, time for some zzzzz.

in the meantime have a browse through this site, it has some basic info about dial up and permissions 

[PPP  Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")[The gnome-ppp  dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][User  Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")
[*][Permissions  for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")
[/LIST]

bye for now 

alexfish

---

### Post by raydux on 2010-04-11
OK, Thanks again for taking a look at this for me, I will see if I can borrow a usb cable later this week. Who knows what will happen then. 
Sweet dreams.

---

### Post by pdc on 2010-04-11
do tell us what

> lsusb

in a terminal says:

........ may be useful to know what device ID is ........

---

### Post by raydux on 2010-04-12
Haven't been able to get the USB cable as yet, none are available right now.
 If I look in the device manager I don't see anything attached to any of the serial ports. So not sure how to find an ID for the unit. Running lsusb only gives me :
 Bus 001 Device 001 : ID 0000 : 0000
 Nothing connected at this time. I got the following from in XP Windows IP configuration (dunno if it will help):
Host name : w-99f9cfbc39264
Node type: unknown
PPP adapter: Smart Internet   (this is the name of the ISP)
description : WAN (PPP/SLIP) interface
physical address: 00-53-45-00-00-00
Dhcp enabled: no
IP address: 10.25.5.130
Subnet mask : 255.255.255.255
default gateway: 10.25.5.130
dns servers: 200.32.218.132
             200.32.218.1
Net Bios over TcPip: diabled  
 

 I dunno if any of this helps but....

---

### Post by alexfish on 2010-04-16
hi

lsusb command will not give any output unless the usb cable is connected

how ever I suggest downloading the wvdial from here  
 [http://packages.debian.org/lenny/wvdial](http://packages.debian.org/lenny/wvdial)
 

 save the file to hd or usbstick (best way ) also check for dependencies
 

 then when in ubuntu click on the files , and they should self install
 

 wvdial will give you an easier route to configure ppp
 

 a typical cdma connection is shown below
 

 to setup automaticaly

from the terminal 

Code:

sudo su



Code:


wvdialconf /etc/wvdial.conf

this hopefully will detect your modem and other info
 

 a typical cdma connection looks like this but edit your own wvdial.conf to suite

 [FONT=monospace]# /etc/wvdial.conf below[/FONT]

 Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800 
Modem = /dev/ttyS0 
ISDN = 0
;Phone = #777 
; Username =
 ; Password =  

################# or try ttyS1

to dial ; from the terminal

wvdial


 

 to use use the last 3 lines remove the " ; " , also if required enter Username and Password after the =  
 
regards

alexfish

---

### Post by raydux on 2010-04-18
I am still in shock, it worked after using gnome-ppp, I am online in Uuntu!! This is the log from the connection:

Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.55
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Sending: ATM1L3DP#777
--> Waiting for carrier.
ATM1L3DP#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Apr 18 07:18:24 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6204
--> Using interface ppp0
--> local  IP address 10.25.5.71
--> remote IP address 10.25.1.226
--> primary   DNS address 200.32.218.132
--> secondary DNS address 200.32.248.1


 I somehow got this connection to work (sort of) But it takes a while to work each time I try to connect, anybody have clues as to how to tweak the settings to maybe help it connect easier? 
 A large "Thank You " to all who replied trying to help, and a special Thanks to Alexfish, Thank you. It was really appreciated.

---

### Post by alexfish on 2010-04-18
looking at the above " permisions denied " may be this will help
From the terminal

Code:

gksudo nautilus


Ignore any warnings



You then navigate to folder  /etc/ppp and right click on pap-secrets -> Properties ->  Permissions tab then select dip from the drop down menu for Group and  and then select read and write under Access. Repeat for chap-secrets.  The annoying warning messages should now disappear.

for other you could try adding this line to the wvdial

stupid mode = 1

forgot



have you tried a USB cable yet it may improve your connection speed , but can't say for sure, if you do then wvdial will have to be reconfigured to use the ports

to find them just use the command as mentioned in post #2

Added,  could you post the details of the [FONT=monospace]/etc/wvdial.conf file as this may help others [ thanks in advance ]

regards

alexfish
[/FONT]

---

### Post by raydux on 2010-06-06
A quick note to all who helped me in this endeavor so far, I was out of the country for a while and am just gettting caught up with all the backlog of stuff to do. I am still fiddling with my connection, running gnomeppp to get online. Sometimes it takes a half dozen attempts, some times it never works, I really have nothing new to add to this that could help anyone. But if anyone needs any specific info, I would be more than happy to provide. As for usb cables, I haven't located one yet. Anyway, thanks again to all. It is really appreciated.

---

