---
title: "Cannot Use Alcatel One Touch X090S 3G modem in ubuntu 12.04"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by arjei1226 on 2012-05-17
Hi guys, hope you could help me... I've been searching for existing threads about this problem but can't seem to find any.

Anyway, here's what I see upon **lsusb**:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 004: ID 13d3:5710 IMC Networks 
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 008: ID 1bbb:0000 T & A Mobile Phones

With **usb-devices**, here's how it looks like:

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
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

Thanks much in advance!

---

### Post by Script Warlock on 2012-05-17
check [this]("http://ubuntuforums.org/showthread.php?t=1199646") if it can help

---

### Post by arjei1226 on 2012-05-17
Hi Script Warlock,
 
I tried the first three steps but I still don't see this one after **usb_modeswitch**: 
.....  Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2 
Any idea what I should do next?
 
Thanks! I appreciate your help.

---

### Post by Tecuhtli on 2012-06-13
I have the same problem with the Alcatel One Touch 918D (dual SIM) ... I can't modeswitch the phone ...

'lsusb' says:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0bda:58ea Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 005: ID 1bbb:0001 T & A Mobile Phones 

and 'sudo mode_switch -v 1bbb -p 0001' says:
sudo usb_modeswitch -v 1bbb -p 0001

Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x02 (out) and 0x82 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Alcatel 
   Model String: Alcatel MS      
Revision String: 0100
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Alcatel
     Product: Alcatel Android phone
  Serial No.: 0123456789ABCDEF
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

Does anyone have a hint how to solve this problem? I am not very familiar with this stuff ... I read somewhere that the usb device should have product id '0000'. nevertheless 'sudo usb_modeswitch -v 1bbb -p 0001 -V1bbb -P 0000' doesn't work either.

Any help would be appreciated!
Thx, Tecuhtli

---

### Post by quiricada on 2012-07-12
1
for easier setup, plug it in a windows 7 system, it will automatically install everything, then do the install, (i forgot the exact menu item here) anyway, look for the modem setup menu and select "3G" instead of "Auto" or "2G", this will set the modem on "3G" mode (blue led color); if you don't do this step, the modem is set to "Auto" and you'll connect to either 2G (green led color) or 3G; well, if you don't mind "2G" then you can skip this and take your chance

from here on, it's ubuntu 12.04

2
plug the modem, do a lsusb, you should get 1bbb:0000, this indicate your modem is hot and ready.
if you poke in /var/log/syslog, you'll see the usb_modeswitch is doing it's thing, hence lsusb is showing 1bbb:0000

3
install wvdial <sudo apt-get install wvdial> or do it in synaptic

4
open /etc/wvdial.conf <sudo gedit /etc/wvdial.conf>
change the Modem line to "Modem = /dev/ttyUSB2"
save it

5
open a terminal <Ctrl-Alt-T>
type <sudo wvdial>

have a bit of patience while you watch the messages
you'll see bunch of messages like:
Carrier detected. Waiting for prompt.
Using interface ppp0
local IP address xx.xx.xx.xx
secondary DNS address xx.xx.xx.xx

when you see the abovementioned last line, you got yourself a connection, just leave the terminal as is

modem led, blue is 3G, green is for patience (2G)

open your browser and start wasting your time :)

6
when you are done, just go back to the terminal and do a <Control-C> to terminate the connection.


CAVEAT
this works for me, it may or may  not work for you.
ttyUSB2 may not work for you, you'll have to look in syslog and look at which ones the modem is using, it'll take 3, mine are ttyUSB0, ttyUSB1, ttyUSB2; why 3 and why such a pain in the behind to get this thing to work, beats me, you'll have to go ask the french and the chinese.
note that network manager is not used at all, so none of those nice gui thing here; you can see in syslog that modem-manager is trying to do something but is not succeeding.

---

### Post by morphet on 2012-09-20
Before messing with /dev, try this:
open /etc/modules and add these two lines at the end:

usbserial
option

reboot, and enjoy. I'm writing from a Bouygues Alcatel onetouch X230L, linux mint. The distros usually have the right drivers, it's just a matter of telling linux to expect dual devices (modem/storage). I found this at: [http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04](http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04)

You'll then have to go to "networks", and follow the "broadband connections"-> "add new connection" wizard. On my system it takes about 20 seconds after I plug the modem in to recognize it.
Let me know how it went...

---

### Post by mustaculous on 2012-12-11
Thank you man, it worked... you rock!


> **morphet said:**
> Before messing with /dev, try this:
open /etc/modules and add these two lines at the end:

usbserial
option

reboot, and enjoy. I'm writing from a Bouygues Alcatel onetouch X230L, linux mint. The distros usually have the right drivers, it's just a matter of telling linux to expect dual devices (modem/storage). I found this at: [http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04](http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04)

You'll then have to go to "networks", and follow the "broadband connections"-> "add new connection" wizard. On my system it takes about 20 seconds after I plug the modem in to recognize it.
Let me know how it went...

---

