---
title: "Vodaphone dongle non connection"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Shenachie on 2011-05-12
I am seriously struggling here with a Vodaphone mobile dongle. a K3570-Z with the latest edition of Ubuntu. 11.04

I have used the Network manager to create a connection but when I click on it I get a message saying GSM Network Disconnected you are now offline. 

I am very much a newbie with Ubuntu so please be gentle. 

No one able to offer assistance?

Shenachie

---

### Post by Shenachie on 2011-05-13
Anyone please?

---

### Post by alexfish on 2011-05-13
confirm if the device is recognized by Network Manager
post details of APN used by Network Manager
and which Country and  Plan your supposed to use

---

### Post by Shenachie on 2011-05-13
confirm if the device is recognized by Network Manager yes
post details of APN used by Network Manager not a clue sorry.
and which Country and  Plan your supposed to use UK and pre paid as far as I am aware

Shenachie

---

### Post by alexfish on 2011-05-13
Hi
cant help much if you don't know which plan you are on

here are the listing from the database

settings vodafone UK

Contract:
APN internet
username web
password web
IPV4 settings: Automatic (PPP) address only
dns1 10.206.65.68
dns2 10.203.65.68

Prepaid:
APN pp.vodafone.co.uk
username wap
password wap
IPV4 settings: Automatic (PPP) address only
dns1 172.29.1.11
dns2 172.29.1.11

TopUp and go:
APN ppbundle.internet
username web
password web
settings for
IPV4 settings: Automatic (PPP) address only
dns1 10.203.129.68
dns2 10.203.129.68

There is also a listing for TopUp and go
TopUp and go:
APN pp.internet
username (leave blank)
password (leave blank)
IPV4 settings: Automatic PPP

goto Network Manager right click and select Edit Connections

you will have to make the Choice,

see what happens

alexfish

---

### Post by Shenachie on 2011-05-13
Thanks for that. 

I am on Prepaid, and altered the settings in the connection manager but no joy. The connection shows up as Vodaphone but it also says mobile broadband is not enabled?

Any further thoughts please?

Shenachie

---

### Post by alexfish on 2011-05-13
Can ensure the Pre Paid is Paid

some devices need to be registered in windows (can check, also need to know if working in windows)
can also post the results of these commands from the terminal
```
nm-tool
```
```
usb-devices
```locate the lines which indicate the device and post only those lines
```
ls -al /dev/serial/by-id
```

---

### Post by Shenachie on 2011-05-15
Update. 

I have now got the dongle actually working. First fault was the sim card not located properly, and the 2nd no signal at my house. Hmm... makes things a bit tricky that. 

So I took the lappie for a drive and have just proved it can get a signal, it came up with a light blue light which the bumph tells me is a 3g signal, so that is good. 

When I click the Vodaphone connection in the connection manager it gives me noting but in the list of connections there is now a "Vodaphone gprs" appeared. However it is "greyed out". 

any suggestions please?

Shenachie.

---

### Post by Shenachie on 2011-05-17
bump

---

### Post by alexfish on 2011-05-17
> **Shenachie said:**
> bump

replying to requested info helps

---

### Post by Shenachie on 2011-05-18
I thought I had explained. 

I cannot get a windows check as it has no signal here at home. 

I cannot copy and past the results of the requested info as for obvious reasons the net is not working on the lappie. 

Not being awkward, just in an awkward situation here. 

Shenachie

---

### Post by Mattallyc on 2011-05-25
I'm on holiday and over the last couple of nights I've managed to get mine to work.
I think if the dongle is recognised in network manager then it's just a matter of getting the APN and password right. As I dual-boot with windows I was able to see what the settings were there and use the same info in Ubuntu. The only way I could see the info in Windows was to go into manage connections and start to create a new one. I noted the defaults it came up with and then went back to Ubuntu. I then edited the mobile broadband connection so the info is the same.
Here's what worked for me and I'm on Vodafone prepaid:
APN: pp.internet
username: web
password: web

Hope this helps,
Matt

---

### Post by Shenachie on 2011-05-25
Ok am now on a connection although not the dongle. 

T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1008 Rev=00.00
S:  Manufacturer=Vodafone (ZTE)
S:  Product=Vodafone Mobile Broadband K3570-Z
S:  SerialNumber=P680A8VDFD000000
C:  #Ifs= 5 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 140 2011-05-25 13:41 .
drwxr-xr-x 4 root root  80 2011-05-25 13:41 ..
lrwxrwxrwx 1 root root  13 2011-05-25 13:41 usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-05-25 13:41 usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-05-25 13:41 usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 2011-05-25 13:41 usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root  13 2011-05-25 13:41 usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if04-port0 -> ../../ttyUSB4


 Device: ttyUSB3 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:



[FONT=monospace]
[/FONT]

---

### Post by Shenachie on 2011-05-27
Bump...

---

### Post by rvchari on 2011-05-27
> **Shenachie said:**
> confirm if the device is recognized by Network Manager yes
post details of APN used by Network Manager not a clue sorry.
and which Country and  Plan your supposed to use UK and pre paid as far as I am aware

Shenachie

right click on the nm icon in panel and go to edit connections. choose mobile broadband and choose your country and plan. i tried it using the united kingdom as country and vodafone (not the airtel vodafone). chose prepaid and connection was complete. when i went to check the settings, user name was wap and password (3 dots, presumably wap) access point is chosen by itself. it configures by itself unfortunately i cant test as i am located in india.

i connect using my mobile broadband like this, connection and configuration is a breeze... let the config take place by itself and you dont set any settings... may be you will find your answer.

---

