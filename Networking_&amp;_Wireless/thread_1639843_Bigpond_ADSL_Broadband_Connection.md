---
title: "Bigpond ADSL Broadband Connection"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by TopEnder on 2010-12-07
G'Day Forum Members, and Thanks in advance.
My grand daughter gave me an Telstra/Bigpond ADSL Modem.  Had no problems in connecting it and useing it with Microsoft. The more I read through the forum the more I got confused
First problem was with the instruction in the Ubuntu 10.10 (Meerkat) Help & Support (top Panel), under Internet and Networks/DSL it said right click on the Network Manager icon in system notificatin area and Edit Connection (could not find it), click DSL & click Add.  Is the Network Manager the same as System/Preference/Network Connections if so, next problem in Network Connections / Editing DSL connection, in the field Service - what do I put in this field?
Do I nedd to fill in anything else under Wired, PPP settings, or IPv4 Settings?
Do I need to install any Packages from either Synapic Manager or Ubuntu Software Centre?   Thanks TopEnder
P.S. it use to be so easy when I had my two tin cans and a length of string!

---

### Post by dineshs on 2010-12-07
Please try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
> Service - what do I put in this field?
Anything say the name of your ISP
> Do I nedd to fill in anything else under Wired, PPP settings, or IPv4 Settings?
Do I need to install any Packages from either Synapic Manager or Ubuntu Software Centre?no

---

### Post by TopEnder on 2010-12-07
Followed your instructions ( Step 1, Step II and Step III. The problem I have is as I have no NM icon (in either top or bottom panel), how can I restore the NM icon and connect to DSL?

Thanks for the help so far, TopEnder

---

### Post by dineshs on 2010-12-08
Try 
1)Rightclick top panel-click add to panel - select [COLOR="Blue"]Notifiction area[/COLOR] and add
If the icon is not still there, try
2)```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set ```
managed=true
```then restart
Note:Hope your /etc/network/interfaces contain only the following lines
auto lo
iface lo inet loopback

---

### Post by TopEnder on 2010-12-08
[COLOR="Blue"]> **dineshs said:**
> [/COLOR]Try 
1)Rightclick top panel-click add to panel - select [COLOR="Blue"]Notifiction area[/COLOR] and add
If the icon is not still there, try
2)```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set ```
managed=true
```then restart
Note:Hope your /etc/network/interfaces contain only the following lines
auto lo
iface lo inet loopback[/COLOR]

dineshs, I have my NM icon back and have setup as per your posts, things I have noticed are:
When I click on the NM icon and select DSL Conection 1, the NM icon becomes active then after a short while a pop-up appears saying> "Wired network  Disconnected - you are now off line"


I have included the following as in might help in resolving my network problem:
nm-settings.config

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file: 
# 
# /etc/default/NetworkManager 
# 

[main] 
plugins=ifupdown,keyfile 

[ifupdown] 
managed=true


sudo lshw -c network

TopEnder@experimential:~$ sudo lshw -c network 
  *-network               
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: b 
       bus info: pci@0000:01:0b.0 
       logical name: eth0 
       version: 10 
       serial: 00:0d:61:79:26:2d 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s 
       resources: irq:16 ioport:c000(size=256) memory:ee000000-ee0000ff 


/etc/network/interfaces

auto lo 
iface lo inet loopback 

PS can not remember how to put it in pretty code boxes

Thanks, TopEnder

---

### Post by dineshs on 2010-12-09
> When I click on the NM icon and select DSL Conection 1, the NM icon becomes active then after a short while a pop-up appears saying> "Wired network Disconnected - you are now off line"
Dont worry about this message.Ensure that it says [COLOR="Blue"]DSL[/COLOR] connection established.Then see if pages are loading.If not please post the result of```
ping -c3 4.2.2.1
```
Note:All the command results look normal

---

### Post by TopEnder on 2010-12-09
> **dineshs said:**
> Dont worry about this message.Ensure that it says [COLOR="Blue"]DSL[/COLOR] connection established.Then see if pages are loading.If not please post the result of```
ping -c3 4.2.2.1
```
Note:All the command results look normal
dineshs, Don't understand what you mean: > Dont worry about this message.Ensure that it says [COLOR="Blue"]DSL[/COLOR] connection established.Then see if pages are loading.
Code:  ping -c3 4.2.2.1   Returned  Network is unreachable

When I start the PC with the Broadband modem switch on and operational?  All the lights are on (Power, Ethernet, DSL & Internet) except USB  (not cable is installed between the modem and the PC.
Whem I click on the NM Icon a drop down menu appears, showing the following:
Wired Network disconnected (*greyed out)*
-------available --------
DSL Connection 1
------------------------
VPN Connection >  configure VPN....
(disconnected VPN *greyed out)*

If I click on NM Icon the Icon becomes active then after awhile returns to how it was when the PC was started.

Over night I did a clean install of Mayerick Meerkat (10.10) did not change any setting and no updates (no Internet connection Ha! Ha!)  I do have them backed up.

Thanks again, TopEnder

---

### Post by dineshs on 2010-12-09
Can you give the following details?
> Had no problems in connecting it and useing it with Microsoft
1)You mean you have only one machine and the connection is OK in windows? How do you connect to internet in windows?Do you use a PPPoE dialler with username and password given by ISP (Modem in bridge mode)?
if your answer is yes
2)What happens when you click on NM then DSL connection in ubuntu?Does it say connection established?If yes
3)do you get reply for ping 4.2.2.1 -c3 ?
4)What is the output of ```
ipconfig /all
``` [COLOR="Red"]on windows[/COLOR]

---

### Post by TopEnder on 2010-12-09
> **dineshs said:**
> Can you give the following details?

1)You mean you have only one machine and the connection is OK in windows? How do you connect to internet in windows?Do you use a PPPoE dialler with username and password given by ISP (Modem in bridge mode)?
if your answer is yes
2)What happens when you click on NM then DSL connection in ubuntu?Does it say connection established?If yes
3)do you get reply for ping 4.2.2.1 -c3 ?
4)What is the output of ```
ipconfig /all
``` [COLOR="Red"]on windows[/COLOR]
dineshs,
Had no problems in connecting it and useing it with Microsoft **[COLOR=Blue]NO[/COLOR]**
2 PCs both dual boot:
Intel core 2 Duo; Windows Vista Home & 10.04 (Main PC)
AMD Athlon XP 1800+; Windows XP Pro & 10.10 (Experimential PC)

1)  ISP supplied the CD & modem, I used auto install to install the Broadband, believe it is setup to use PPPoE.
2)  No only after a period of time a Pop-Up Wired Network Disconnected - you are now off line (as per my post #7).
Since that post I did another clean install on the AMD Athlon XP 1800+ except I used a seperate /home partition on another HD.
I thought I did see a connection when I was fiddling with System/Administration/Network Tools but so far I havenot been able to duplicate what I did.

Will try **ipconfig /all** tomorrow.

---

### Post by TopEnder on 2010-12-11
G'Day  Forum Members,

With the help of  dineshs (posts above) and three clean installallations (tries) I now have theTelstra/Bigpond Broadband modem working on Ubuntu 10.04 & 10.10.   
Before starting I connected the ADSL modem and Ethernet cable to the PC waited until all lights were steady green then started the installation.   Both versions of Ubuntu automatically connected the PC to the internet via the Wired network connection 'Auto eth0', thanks again tor the help.  TopEnder

---

