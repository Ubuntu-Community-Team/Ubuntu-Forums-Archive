---
title: "&quot;GSM network disconnected&quot; on 3g USB modem"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by nikhilbuwa on 2011-03-25
I have a vodafone (zte) 3G USB stick(modem). it got connected & worked fine earlier but now theres a prob. it gets connected but after some time it disconnects automatically & m unable 2 connect it back...
network manager shows msg "GSM network disconnected"
i think the modem is detected since i can see the network names in the n/w manager applet.but every time it shows same msg & does not connect, i tried removing & reinserting the device also tried disabling & enabling network but no success. i have to restart to get it back working. but thats a pain.....
i tried the network manager(default), a s/w Betavine Connection Manager (BCM) which can handles vodafone connection, but same thing. i have the zte s/w (dashboard) "join air" but unable to connect thru it. it gives error "DNS invalid"....
ya & also the device continuously shifts between 2G & 3G networks... this does not happen in windows... in windows i get 3g with good speed & no disconnects...
can anyone help me solve this...
thnx

---

### Post by alexfish on 2011-03-26
Hi

need to find out if apn has changed ,
first run the device in windows (double check for updates), also check the dialup number in the dialup connections (make a note and post result)

back in ubuntu
open up first terminal and enter the following
```
tr -s "\n" < /dev/ttyUSB2
```
open up second terminal and the following codes and post the results from the first terminal
```
echo -e "AT+COPS=3,2\r" > /dev/ttyUSB2
```
```
echo -e "AT+COPS?\r" > /dev/ttyUSB2
```
```
echo -e "AT+CGDCONT?\r" > /dev/ttyUSB2
```

---

### Post by nikhilbuwa on 2011-03-27
first of all thnx for a quick reply...
the apn & all is fine... its"www" for vodafone india & dial no is "*99#"
i also tried *99***1# & *99***2# but both dint work...
& both r same(apn & dial no) no update or change.
the prob is wired coz i cant figure out what exactly the prob is...
i might sound confused... yes i am.
actually the net works fine sometimes for hours(even the whole night)
but sometimes disconnects in 10-15min or even earlier, with no reason..
& after that it does not connect till restart.

the op of the commands

>  tr -s "\n" < /dev/ttyUSB2

+CMTI: "ME",5
+CMTI: "ME",6
+CMTI: "ME",7


& then it got stuck (the net was working at that time)
what exactly do this commands do... do i have to run them when net is not connected & the device is??
what is "/dev/ttyUSB2" , i think the device is detected as /dev/USB1

---

### Post by nikhilbuwa on 2011-03-27
forgot to read the line in betn two codes :P
the o/p is:
> nikhil@HP:~$ tr -s "\n" < /dev/ttyUSB2
AT+COPS=3,2
OK
AT+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+COPS=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=T+CO=
+COPS: 0,2,"40420",2
OK
AT+CGDCONT?
+CGDCONT: 1,"IP","www","0.0.0.0",0,0
+CGDCONT: 2,"IP","www","0.0.0.0",0,0
+CGDCONT: 3,"IP","portalnmms","0.0.0.0",0,0
+CGDCONT: 4,"IP","airtelgprs.com","0.0.0.0",0,0
+CGDCONT: 5,"IP","aircelgprs","0.0.0.0",0,0
OK
AT+CG0,0
ERROR
NO CARRIER

this was when the net got disconnected...(had 2 restart)

---

### Post by alexfish on 2011-03-27
hi

from first post , mentioned tried BCM and also failed

need to know if the disconnection started when you tried this software or

also mentione zte (dash board) , and are they still installed

is there any information indicating which /dev/tty* been used for the connection

there appears to be either a daemon or software accessing the device ( messaging part of the device ), depending on the ports been accessed , this may be the problem, but not sure

can also post the results of these commands from the terminal

```
ls -al /dev/serial/by-id/*
```
```
usb-devices
```

alexfish

---

### Post by nikhilbuwa on 2011-03-28
hi.
regarding the softwares, i have BCM & joinair (by zte). i can connect through the ubuntu network manager (applet) or BCM but could not connect thru joinair. i get error DNS invalid...

but any way if i get connected through any method, then i dont do anything else just surf & download.
the problem is that it gets disconnected suddenly.

when i was typing this post it got disconnected. i dint do anything else.
& i even executing the code u posted but it got disconnected after quite some time(not immediately).

i am new to linux so dont know much of the commands & all to find devices & could not get a device manager like that in windows..

1 thing i was thinking of is, does ubuntu have problems with networking? coz i saw in many forums & even here...

i heard that open-suse is good for laptops... (by the way i use laptop)
coz it has a good network manager.


output of the codes
> lrwxrwxrwx 1 root root 13 2011-03-28 18:25 /dev/serial/by-id/usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-03-28 18:25 /dev/serial/by-id/usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-03-28 18:25 /dev/serial/by-id/usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2011-03-28 18:25 /dev/serial/by-id/usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root 13 2011-03-28 18:25 /dev/serial/by-id/usb-Vodafone__ZTE__Vodafone_Mobile_Broadband_K3570-Z_P680A8VDFD000000-if04-port0 -> ../../ttyUSB4


> T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-28-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
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
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0158 Rev=51.95
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20060413092100000
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b057 Rev=08.18
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=CNF7041
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by alexfish on 2011-03-31
Hi

have had time to read through some of the data in BCM regarding this device
(the sim card has a unique problem if accessed in a certain way (BCM should be able to handle this) doubt if zte s/w (dashboard) can

one thing of note is that the device uses WCDMA , BCM has a WCDMA wrapper specific for this device , Note you will now have wader core on the system
this replaces the modem-manager as installed on the system at default , assume will find in same instance in any other linux distro , nothing ventured nothing gained
maybe worth trying the device on any other system with default modem-manager installed (depends on version)

to look further into this device as regards Ubuntu 

did the device work before you installed BCM (as previously requested)
need to know if the disconnection started when you tried this software or

also mentioned zte (dash board) , and are they still installed

If the device worked (or partially work) before the above (need reason why you installed other software)

If did not work prior to installing other software (was it recognized in Ubuntu )


can also suggest to remove zte s/w (dashboard) "join air"

Next need other info

can post the details of the codes used for the mentioned connection
> i even executing the code u posted but it got disconnected after quite some time(not immediately).and the specific /dev/ttyUSB* port been used for the connection , this is important ,
may be relevant to what is shown by the info from usb-devices command

then will look further at the problem

alexfish

---

### Post by nikhilbuwa on 2011-04-07
hi
was busy, so could not check the forum... 
u asked if the prob (of disconnect) was before installing BCM.. ya it was & that was the only reason for me to search something & find it(BCM).
ya the device was detected in ubuntu & i could connect directly by creating a network in mobile broadband. but then disconnects were there.
Now i installed the joinair (zte software) earlier. i used other SIM card (airtel) India, it worked.
but the vodafone did not work.. it gave error DNS invalid.. now i dont know why is it so, but any way i dont use it now(but have it). will unstall it & see.
but 1 thing i observed is the disconnects are less these days.
so i still dont know what is causing the prob is.

---

