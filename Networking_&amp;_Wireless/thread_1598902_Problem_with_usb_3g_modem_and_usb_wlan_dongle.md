---
title: "Problem with usb 3g modem and usb wlan dongle"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by duuso on 2010-10-17
I have two computers, desktop and a laptop. Desktop acts as a server, I control it with VNC, it's powered down pretty much every night. Desktop is connected to internet with Huawei E169 3g modem (lsusb says it's E620) and I'm currently sharing internet to laptop with wired network. I wanted to share network connection from desktop to laptop over wifi, so I plugged A-link wlan dongle (lsusb: zydas wla-54l 802.11bg) and played around with settings. I never got sharing over wlan to work, not even ping. But the bigger problem is that if I boot the desktop with both 3g and wlan plugged in, Ubuntu's network manager can't recognize 3g modem at all (even though I can see 3g's Mobile Partner partition mounted in the desktop/in the media folder). In this case if I disable wireless networking, unplug the wlan dongle and then plug in the 3g, 3g works again. So wonder what's the problem if they are simultaneously plugged in? I'm running Ubuntu 10.04 x64 with latest updates (atm kernel 2.6.32-25-generic) on the desktop.

---

### Post by alexfish on 2010-10-17
hi

within your own post , the solution to the problem ,

connect the mobile modem , later

---

### Post by duuso on 2010-10-17
Well in my opinion that's far away from correct solution. 3g modem and wlan dongle should work simultaneously and without any repluggin. Desktop acts as a (media)server (I shutdown it every night and boot for usage) and I'd like to have automatically working network as it does now with wired connection. I'm using display to control the desktop as little as possible - currently very rarely, only when I'm trying to get that wlan working - and instead use VNC from laptop.

---

### Post by alexfish on 2010-10-17
"But the bigger problem is that if I boot the desktop with both 3g and wlan plugged in, Ubuntu's network manager can't recognize 3g modem at all"

when this happens can post details of these commands from the terminal

Code:

[COLOR=Blue]usb-devices[/COLOR]

find the parts which are relevent to  3g modem and only those parts


Code:


[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]


Code:

[COLOR=Blue]ifconfig[/COLOR]

---

### Post by duuso on 2010-10-17
#### usb devices (when network manager couldn't recognize 3g)
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0ace ProdID=1215 Rev=48.10
S:  Manufacturer=ZyDAS
S:  Product=USB2.0 WLAN
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=zd1211rw

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

#### usb devices (only 3g modem plugged in, in same port I believe)
T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


#### ls -al /dev/serial/by-id/usb*
There's no directory "serial" if I boot both plugged in, but directory exists when only 3g is plugged in / wlan is plugged after boot.

This is what it when only 3g is in:
lrwxrwxrwx 1 root root 13 2010-10-18 00:46 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-10-18 00:46 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-10-18 00:46 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0 -> ../../ttyUSB2


#### ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:71:c0:46  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe71:c046/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:6462 (6.4 KB)  TX bytes:4275 (4.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10272 (10.2 KB)  TX bytes:10272 (10.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:9f:90:49:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by alexfish on 2010-10-17
going to take this a step at a time

when in this state : going to do a modprobe:

#### usb devices (when network manager couldn't recognize
T: Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#= 4 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs= 1
P: Vendor=0ace ProdID=1215 Rev=48.10
S: Manufacturer=ZyDAS
S: Product=USB2.0 WLAN
C: #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=zd1211rw

T: Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 3 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1001 Rev=00.00
S: Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S: Product=HUAWEI Mobile
S: SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C: #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


From the terminal

Code:

[COLOR=Blue]sudo modprobe option[/COLOR]

recheck with the "usb-devices"

Also need to know if usb_modeswitch is installed


Code:

[COLOR=Blue]which usb_modeswitch[/COLOR]

---

### Post by duuso on 2010-10-18
Sudo modprobe option does the trick, thanks! After that it takes few seconds and ubuntu auto-connects 3g normally. One more: how to make it permanent? Where to report bug(?) / what's next in order to someone fix this for others?

And yes, I installed usb_modeswitch to get 3g.

#### After modprobing: usd-devices
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0ace ProdID=1215 Rev=48.10
S:  Manufacturer=ZyDAS
S:  Product=USB2.0 WLAN
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=zd1211rw

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2010-10-18
Decide if usb_modeswitch is required on the system, is there a reason

First try this 

Code:

[COLOR=Blue]sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules[/COLOR]

scroll down to the line which shows the id's of the device

EXAMPLE:

# Huawei E169
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

disable the line with a # . Add a line so it looks like the below . also double check the ID's prior to saving

# Huawei E169
#ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="/sbin/modprobe option"


this will hopefully do two things

1. device should no longer appear on the desktop
2. load the option driver

try this on, boot with the device , and boot first then insert the device

if this does not work then will look at the etc/rules

Once this is resolved will go to the next step as different options you have mentioned, one step at a time

---

### Post by duuso on 2010-10-19
> **alexfish said:**
> Decide if usb_modeswitch is required on the system, is there a reason

First try this 
Code:
[COLOR=Blue]sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules[/COLOR]

scroll down to the line which shows the id's of the device
EXAMPLE:
# Huawei E169
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

disable the line with a # . Add a line so it looks like the below . also double check the ID's prior to saving

# Huawei E169
#ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="/sbin/modprobe option"

this will hopefully do two things
1. device should no longer appear on the desktop
2. load the option driver

try this on, boot with the device , and boot first then insert the device
Mobile Partner partition still appears on the desktop but that doesn't matter. Tried
1) boot both plugged
2) boot 3g plugged and wlan plugged after reached ubuntu desktop
3) boot wlan plugged and 3g plugged after reached ubuntu desktop
and both worked with each setup. I think I installed usb-modeswitch in first place because 3g modem didn't show up in network manager's device list (add new mobile connection > device). Thanks again!

---

### Post by alexfish on 2010-10-19
OK : next
 

 also suggest try sakis3g (modeswitch embedded ) (can see you want to use VPN) this will broaden your options
 
**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=ENC9TKPhEobU4gbs5O3vAQ&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**


 Reason for Sakis3g ,  can modeswitch and load drivers independent of the system settings : IE if sakis3g works then the system usb_modeswitch could be removed if desired.
 

 As regards the &#8220;USB2.0 WLAN&#8221;  does it work  
 

 if not suggest starting new thread , give the thread title heading &#8220; type or make &#8220;, someone with experience of that device may spot the thread ,
 

 as regards the networking side ,if both device are working
 

 can try looking here first  
 

 [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
 

 see what you think
 

 alexfish

---

### Post by duuso on 2010-10-20
This should be marked as solved (at least I couldn't find option to do that while editing first post)!

---

### Post by alexfish on 2010-10-20
hi

use the thread tools at top of page

alexfish

---

