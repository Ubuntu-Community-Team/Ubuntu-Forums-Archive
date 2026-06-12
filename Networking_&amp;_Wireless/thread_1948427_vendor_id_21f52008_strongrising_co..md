---
title: "vendor id 21f5:2008 strongrising co."
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by bijendrab on 2012-03-28
I recently get success on strong rising co usb modem.
DefaultVendor= 0x21f5 
DefaultProduct= 0x1000 
TargetVendor= 0x21f5 
TargetProduct= 0x2008 
MessageEndpoint=0x05 
MessageContent="555342430850e782c000000080000671010000000000000000000000000000" 
CheckSuccess=20

please  make /etc/usb_modeswitch.d/21f5:1000
issue command
sudo usb_modeswitch -c /etc/usb_modeswitch.d/21f5:1000
modprobe -v option 
#new_id file is now permissible 
sudo chmod 774 /sys/bus/usb-serial/drivers/option1/new_id 
# echo "21f5 2008" > /sys/bus/usb-serial/drivers/option1/new_id 
dmesg
My work around
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=808&]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=808&postdays=0&postorder=asc&start=0") 
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5492](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5492)

this is my pppconfig to connect isp here in nepal
sudo pppconfig 
1. Is my ISP dynamic or static- dynamic 
2. Enter the IP number for primary dns - 115.187.17.50 
3. Enter the IP number for your secondary dns-8.8.4.4 
4. Authentication Method for provider (PAP, Chat, Chap?)- CHAP 
5. Enter your modem port speed (e.g. 9600, 19200, 38400, 57600, 115200) -115,200 
6. Select method of dialing. Touch tone or pulse. -tone 
7. Enter the number to dial-#777 
8. The port your modem is on identified automatically or enter the port  your modem is on (example /dev/ttyS0 is COM1 in DOS.) - ttyUSB0 
10. Password, Username- [email]XXXXXXXXXXX@utlnepal.com[/email],XXXXXXXXXXX 
11.local ip 172.18..........(varies)( dynamic) 
12. remote ip 172.17.28.100 
13. ayncmap - 0X00 or 0X01 

below are files on respective directory
i)
/etc/chatscripts/utlnepal.com
TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
ABORT 'NO CARRIER'

'' 'ATZ'
'OK' 'ATE1'
'OK' 'AT+CGDCONT=1,"IP","172.17.28.100","0.0.0.0",0,0'
'OK' 'ATDT#777
'CONNECT' '\c'
-------------------
ii)file /etc/ppp/peers/provider

 /etc/ppp/peers/utlnepal.com

Inside my peers file I will place following code:

hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/utlnepal.com"
debug
/dev/ttyUSB0
115200
defaultroute
replacedefaultroute
noipdefault
usepeerdns
crtscts
lock
local

# Redial and interval
persist
holdoff 5

# No compression
novj
novjccomp
nopcomp
nodeflate

# CHAP authentication
user "9721230967@utlnepal.com"
remotename "97xxxxxx@utlnepal.com" "utlnepal.com" "97xxxxxx"
refuse-PAP
refuse-eap

# LCP echo messages settings
lcp-echo-failure 4
lcp-echo-interval 65535
---------
iii) /etc/ppp/resolv
# resolv.conf created by pppconfig for provider /etc/ppp/resolv
nameserver 115.187.17.50
nameserver 8.8.4.4
iv)/etc/ppp/chap-secrets file
"97xxxxx@utlnepal.com" "utlnepal.com" "97xxxxxx"

now to connect this must be command
#pppd call provider.
This is basic configuration to get you online. To dial your connection you would use sudo pon ispname and to disconnect you would use sudo poff ispname where “ispname” is you peers file name.
# sudo pon utlnepal.com

---

### Post by bijendrab on 2012-03-28
here is
/etc/wvdial.conf

Modem = /dev/ttyUSB0
Baud = 115200
Init1 =
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Carrier Check = no
Dial Command = ATDT
Phone = #777
Username = XXXXXXXX
Password = XXXXXXXX
Stupid Mode = yes
Auto Reconnect = yes

---

### Post by bijendrab on 2012-04-02
sudo modprobe usbmon 
but usbmon in ubuntu is on /sys/kernel/debug/usb/usbmon 
 
sudo ls /sys/kernel/debug/usb/usbmon 
0s  0u	1s  1t	1u  2s	2t  2u	3s  3t	3u  4s	4t  4u 
 
as lsusb shows bus 004 devic3 002 i am concentrating on -4s 4t  4u 
these are 0u ,4t,4u 
sudo cat /sys/kernel/debug/usb/usbmon/0u |grep " ">0u.txt 
[http://pastebin.com/Sbm56uBU](http://pastebin.com/Sbm56uBU) 
sudo cat /sys/kernel/debug/usb/usbmon/4t|grep " ">4t.txt 
[http://pastebin.com/ZPf0iPWE](http://pastebin.com/ZPf0iPWE) 
sudo cat /sys/kernel/debug/usb/usbmon/4u|grep " ">4u.txt 
[http://pastebin.com/tHzsEG0Q](http://pastebin.com/tHzsEG0Q) 
 can we get message content this way ?

---

