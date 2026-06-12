---
title: "Huawei E5832 and Ubuntu 12.04"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by wojcianiu on 2012-02-18
Hello
Recently I bought a new mobile broadband modem, Huawei E5832, with built-in battery and an availability of making Wi-Fi hotspot. There'll be no problem if I connect through Wi-Fi, but unfortunately I must do this through USB. Network manager doesn't recognise it, but when I type *lsusb* there's an entry
```
12d1:142d Huawei Technologies Co., Ltd.
```It works fine on Windows. Huawei E156G works on Ubuntu very well. My Ubuntu version is 12.04.
I know there were many topics about it, but they didn't help me. Huawei office doesn't response.
Thanks

---

### Post by alexfish on 2012-02-18
hi

have look through usb_modeswitch data , can't see a listing for

this device , 

some of these devices have different switching modes ,

suggest look at

ModeSwitchForum

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

alexfish

---

### Post by wojcianiu on 2012-02-18
I don't know anything about that, so I'll just write what I found out:
Modem is now connected to computer in Ethernet Mode. (12d1:142d)
In Windows, in Device Manager, there are some entries with Huawei in name:
HUAWEI Mobile Connect - 3G Network Card - USB\VID_12D1&PID_1401&MI_03
HUAWEI Mobile Connect - 3G Application Interface - USB\VID_12D1&PID_1401&MI_00
HUAWEI Mobile Connect - 3G PC UI Interface - USB\VID_12D1&PID_1401&MI_02
HUAWEI Mass storage USB Device - USB\VID_12D1&PID_1401&MI_01
Which one should I choose? What should I type with usb_modeswitch command?

---

### Post by alexfish on 2012-02-18
the device manager will not show necessary info

from the terminal use this command , locate the lines which indicate the device and only those lines
```

usb-devices 
```Then will look at possible options

alexfish

---

### Post by wojcianiu on 2012-02-18
Response from *usb-devices* command about Huawei
```
T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=142d Rev=01.00
S:  Manufacturer=Huawei Incorporated
S:  Product=HUAWEI Mobile Connect
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=cdc_ether
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether

```

---

### Post by alexfish on 2012-02-19
Hi

the device has configured

with option driver + cdc_ether interface

the device may or may not work {reports show possible failure using cdc-ether on certain Huawie devices }

but lets see what shows up

from the info

```
1) I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
2) I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
3) I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
4) I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=cdc_ether
5) I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
```At 1) indicates ctrl port (for sending or requesting info from the device "Modem")
At 3) indicates network port (or dial up port + for sending or requesting info from the device "Modem")
At 4) and 5) indicate the ethernet type interface ) usualy shows on the system in usb 0

Can try and see what info is on the device via the the modem ports

need some info of what ports are listed

open up a terminal and enter this command and post the results

```
ls -al /dev/serial/by-id
```also need to see how modem-manager sees the device

goto 

 [How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") POST              #[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62") <- **Click this bit**

post the info from the script (if any)

if unsure about what to do with the script , post back here

alexfish

---

### Post by wojcianiu on 2012-02-19
Response from *ls -al /dev/serial/by-id*:
```
total 0
drwxr-xr-x 2 root root 80 lut 19 13:52 .
drwxr-xr-x 4 root root 80 lut 19 13:39 ..
lrwxrwxrwx 1 root root 13 lut 19 13:39 usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 lut 19 13:39 usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if02-port0 -> ../../ttyUSB1
```There was no response from ./mm-dbus-test from E5832. I tried the same with E156G, and it gave some text.

---

### Post by alexfish on 2012-02-19
need to go to first post at the link given above "**How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]**

on the first post look below [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]IF 3g Connection: Require correct APN and {username and password if required }relevant to Your Pay Plan Check with your ISP
Note: For New Devices Ask If the Device Dial Method is <CID>

[/B][/SIZE][/FONT]it shows how to get info from the modem using two Terminals , so need to see if can get any info from
the device. . the port  [SIZE=2]/dev/ttyUSB2 first also try [/SIZE] [SIZE=2]/dev/ttyUSB1[/SIZE]
post the results if any

also post the results of this command from the terminal
```
grep v12D1 /sys/bus/usb/devices/*/modalias
```alexfish

---

### Post by wojcianiu on 2012-02-19
Results from the first terminal:
```
^RSSI:6
^WIFINOTY:1
^MODE:5,6
^MODE:5,7
^RSSI:6
^RSSI:6
^MODE:5,5
^MODE:5,4
OK
+COPS: 0,2,"26006",2
OK
+COPS: (2,"","","26006",2),,(0,1,2,3,4),(0,1,2)
OK
^RSSI:6
^RSSI:6
^RSSI:6
^MODE:5,6
^MODE:5,7
^RSSI:6
^MODE:5,5
^MODE:5,4
^RSSI:6
^RSSI:6
^MODE:5,6
^MODE:5,7
^MODE:5,5
^MODE:5,4
^MODE:5,6
^MODE:5,7
^RSSI:6
^MODE:5,5
^MODE:5,4

```
260-06 network is Play, Poland
Response from *grep* command:
```
/sys/bus/usb/devices/2-1.4:1.0/modalias:usb:v12D1p142Dd0100dcEFdsc02dp01icFFiscFFipFF
/sys/bus/usb/devices/2-1.4:1.1/modalias:usb:v12D1p142Dd0100dcEFdsc02dp01ic08isc06ip50
/sys/bus/usb/devices/2-1.4:1.2/modalias:usb:v12D1p142Dd0100dcEFdsc02dp01icFFiscFFipFF
/sys/bus/usb/devices/2-1.4:1.3/modalias:usb:v12D1p142Dd0100dcEFdsc02dp01ic02isc06ipFF
/sys/bus/usb/devices/2-1.4:1.4/modalias:usb:v12D1p142Dd0100dcEFdsc02dp01ic0Aisc00ip00

```

---

### Post by alexfish on 2012-02-20
looking at the results could indicate probing on the wrong port

have been googling with regards these new devices , two knows are 

1 , the MODE , which is showing in the resultshave seen posts where the mode has to be set

2 , to get the device into modem mode then need to send AT^******* / which may represent on  NDIS**

can have a look here for now see what you think
```
http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/0418976c06587d80
```if  necessary use google translate 

so at this stage can try probe the registers of the device, it may reveal the actual MODE and NDIS** state

if the device is still spewing out random data try using ATZ to the port to reset the modem  then AT&V to get the registers 
EG: 
```
echo -e "ATZ\r" > /dev/ttyUSB2
``````
echo -e "AT&V\r" > /dev/ttyUSB2
```alexfish

---

### Post by alexfish on 2012-02-20
had a look here re Huawiei mobile partner

[http://blog.brightpointuk.co.uk/configuring-huawei-e5832-e5830-imo](http://blog.brightpointuk.co.uk/configuring-huawei-e5832-e5830-imo)

---

### Post by wojcianiu on 2012-02-20
There's no driver for Linux on that site. There was one at *groups.google.com*, but when I tried to install it,
```
Install NDIS driver failed.
The compiling environment is not all ready.
Please check gcc, make and kernel buid(/lib/modules/3.2.0-2-generic/build) to be all installed?
Now please enter any key to finish other installations.
```
Everything is installed, so I don't know what's wrong.
There's an output from these 2 commands
```
^RSSI:0
^WIFINOTY:1
^RSSI:4
^RSSI:4
^MODE:5,5
^RSSI:4
^RSSI:1
^MODE:5,4
^RSSI:4
OK
AT&V
&C: 2; &D: 2; &E: 1; &F: 0; &S: 0; &W: 0; E: 1; L: 0; M: 0; Q: 0; V: 1;
X: 0; Z: 0; \Q: 3; \S: 0; \V: 0; S0: 0; S3: 13; S4: 10; S5: 8; S6: 2;
S7: 50; S8: 2; S9: 6; S10: 14; S11: 95; S30: 0; S103: 1; S104: 1;
+FCLASS: 0; +ICF: 3,3; +IFC: 2,2; +IPR: 115200; +DR: 0; +DS: 0,0,2048,6;
+WS46: 12; +CBST: 0,0,1;
+CRLP: (61,61,48,6,0),(61,61,48,6,1),(240,240,52,6,2);
+CV120: 1,1,1,0,0,0; +CHSN: 0,0,0,0; +CSSN: 0,0; +CREG: 0; +CGREG: 0;
+CFUN:; +CSCS: "IRA"; +CSTA: 129; +CR: 0; +CRC: 0; +CMEE: 1; +CGDCONT: (1,"IP","","0.0.0.0",0,0)
; +CGDSCONT: ; +CGTFT: ; +CGEQREQ: ; +CGEQMIN: ; +CGQREQ: ; +CGQMIN: ;
+CGEREP: 0,0; +CGDATA: "PPP"; +CGCLASS: "A"; +CGSMS: 1; +CSMS: 0;
+CMGF: 0; +CSAS: 0; +CRES: 0; +CSCA: "+48790998250",145; +CSMP: ,,0,0;
+CSDH: 0; +CSCB: 0,"",""; +FDD: 0; +FAR: 0; +FCL: 0; +FIT: 0,0; +ES: ,,;
+ESA: 0,,,,0,0,255,; +CMOD: 0; +CVHU: 1; +CPIN: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;
+CMEC: 0,0,0; +CKPD: 1,1; +CIND: 0,1,1,1,0,0,1,0; +CMER: 0,0,0,0,0;
+CGATT: 1; +CGACT: 0; +CPBS: "SM"; +CPMS: "SM","SM","SM";
+CNMI: 0,0,0,0,0;  +CMMS: 2; +FTS: 0; +FRS: 0; +FTH: 3; +FRH: 3; +FTM: 96;
+FRM: 96; +CCUG: 0,0,0; +COPS: 0,2,""; +CUSD: 0; +CAOC: 1; +CCWA: 0;
+CCLK: ""; +CLVL: 2; +CMUT: 1; +CPOL: 0,2,"",0,0,0; +CPLS: 0; +CTZR: 0;
+CTZU: 0; +CLIP: 0; +COLP: 0; +CDIP: 0; +CLIR: 0; ^PORTSEL: 0;
^CPIN: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;; ^ATRECORD: 0; ^FREQLOCK: 49643948,0; ^CMSR: 1
OK
^RSSI:4

```

---

### Post by alexfish on 2012-02-20
from the info ,do not see anything of the obvious , will look at the site mentioned as regards the AT commands used

from what it said at the site
> and I looked at the Mobile Partner software that accompanied it.so presume there maybe a cd if have cd have a look at it ,or possibly the connect-manager is on the device

does anything show on your [COLOR=Blue]desktop[/COLOR] which may indicate the device
if not can use [COLOR=Blue]disk utility[/COLOR] see if can be mounted , if so see what is on the device

if can find the files on the device copy them to the home directory ,  save in a folder for now , post any info or screen shot of what is there

if nothing shows then possible to disable mode_switching
```
sudo gedit /etc/usb_modeswitch.conf
```change line to
```
DisableSwitching=1
```remove the device and plug back in , see if can find the device

once done change the line back to
```
DisableSwitching=0
``` don't install anything further"" than what is done

but can look searching system /usr/bin usr/sbin /bin sbinor or look at readme files that came with the device , need to find the application name ,

if found , can call it from the terminal by its name .

---

### Post by wojcianiu on 2012-02-20
My device, unfortunately, doesn't have Linux drivers, but I can send the contents of its flash drive. (Sorry for Polish :D) It hasn't had worked on Linux, so will it be a problem if I use Windows...? :smile:
[IMG]http://img819.imageshack.us/img819/985/20120220215135.png[/IMG]
[IMG]http://img812.imageshack.us/img812/3356/20120220215148.png[/IMG]

[IMG]http://img685.imageshack.us/img685/2920/20120220215203.png[/IMG]

[IMG]http://img560.imageshack.us/img560/2305/20120220215358.png[/IMG]
[IMG]http://img94.imageshack.us/img94/4483/20120220215417.png[/IMG]
Contents of a folder
[IMG]http://img543.imageshack.us/img543/2445/20120220215655.png[/IMG]
There's file in the attachment, I think it's not interesting, but...? It has some info about used programs
If more detailed info is needed, write. I can send a full data.bin file, it can be opened with 7-Zip
Instructions which came with device don't have any information about Linux

---

### Post by wojcianiu on 2012-02-21
YEEES!! IT WORKS!!
I installed Huawei Driver from Huawei site and it now recognises my device as Wired Network. Thx alexfish for everything. 
Here is the link: [HTML]http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=[/HTML]unpack and cd to the right directory
type sudo ./install
restart the computer
plug off and plug in the device
That's everything. (I'm so happy... :D Goodbye, Windows!)

---

### Post by alexfish on 2012-02-21
Hi

Pleased to see the device connects , and you are Happy .;)

You say thanks , me thinks also Huawei need thanks  ...:KS

I will also say , Thanks to you for your Patience at arriving at the Solution , not many have the determination to which you have shown , Thanks again.

**may the Ubuntu be with you**

regards

alexfish

PS: is there an auto run in the folder

ADDED : if  Mobile Parter Fails to init when device is connect try this command from the terminal
```
startMobilePartner
```

---

### Post by alexfish on 2012-03-12
> **wojcianiu said:**
> YEEES!! IT WORKS!!
I installed Huawei Driver from Huawei site and it now recognises my device as Wired Network. Thx alexfish for everything. 
Here is the link: [HTML]http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=[/HTML]unpack and cd to the right directory
type sudo ./install
restart the computer
plug off and plug in the device
That's everything. (I'm so happy... :D Goodbye, Windows!)

**Hi all **

have done follow up of Huawie device : to use Huawei Mobile Partner

at the**How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]** post  			#[**64**]("http://ubuntuforums.org/showpost.php?p=11709821&postcount=64") 

as always said, use at own risk

alexfish

---

