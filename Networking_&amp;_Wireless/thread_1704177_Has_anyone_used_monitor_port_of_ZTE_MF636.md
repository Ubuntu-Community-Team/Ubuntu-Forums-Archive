---
title: "Has anyone used monitor port of ZTE MF636"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by gagaxj on 2011-03-10
Hi,

Has anyone used ZTE MF636 monitor port? I tried it both on ubuntu 10.04 and 10.10, but both failed.

The default driver option can bring up 3 ports
/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2

where, /dev/ttyUSB2 is the data port that I can establish ppp connection on. I also need to send AT commands to the modem while ppp is active, but the monitor port neither /dev/ttyUSB1 nor /dev/ttyUSB0 can answer any AT commands.

The following information is from usb-devices

 T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

Please help me. Thanks.

---

### Post by An Sanct on 2011-03-10
Welcome to the forums!

Please, see [this thread]("http://ubuntuforums.org/showthread.php?t=1005910") on how to configure the dialer for this 3G modem...

---

### Post by GeorgeVita on 2011-03-10
Hi **gagaxj** and **An Sanct**!

@gagaxj: read also [this procedure]("http://ubuntuforums.org/showpost.php?p=7443556&postcount=24") to get some ideas. At this time I cannot use my ZTE MF636 with Ubuntu 10.04 (I tried it hardly just now) as [bug#408555]("https://bugs.launchpad.net/bugs/408555") still exists for my modem (I am not sure if this appears to newer versions of MF636).

You must also consider that network-manager and modem-manager are using both serial ports (data & control). If you want to take control of any port you must stop network-manager and killall modem manager ...

I will do some more tests with a newer version (10.10 or 11.04) and inform you if any better result!

Regards,
George

---

### Post by gagaxj on 2011-03-10
Thanks GeorgeVita and An sanct for your reply.

@GeorgeVita: Actually, I have read most of your pages before posting this new thread. I have been struggling with the modem for several months. There is no problem to use usb_modeswitch to switch it from cdrom device to 3g modem, and establish ppp connection on ttyUSB2. The only problem is to use another port to monitor the modem by sending AT commands, such as AT+CSQ to get signal strength.

Most of my test is done in a text mode Ubuntu (version 10.04) without x-windows and any network-manger or modem manager. 
I wrote my own network scripts to set up ppp connections on /dev/ttyUSB2, and it works. So I am quite sure that there is no other processes using the modem and the port.
I also tried minicom -s to test ttyUSB0 and ttyUSB1 followed your procedures in [http://ubuntuforums.org/showpost.php?p=7443556&postcount=24](http://ubuntuforums.org/showpost.php?p=7443556&postcount=24)
But it just stuck in the stage of initializing the modem. In addition, I tried "screen /dev/ttyUSB1 115200", but there was even no echo of AT commands I typed. 

Yesterday, I tried the latest 10.10 LTS version with x-windows, it has the same problem to use /dev/ttyUSB1 even I disable the network-manager. 

By the way, I have not seen the problem in my case as your bug#408555 in [https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/408555](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/408555)

Regarding the hardware, I tried the modem on my Mac machine. It can show up two ports, both ports can answer AT commands at the same time. So I guess the problem is the driver for MF636 in Ubuntu. But I have not seen anyone reported this problem.

---

### Post by GeorgeVita on 2011-03-10
> **gagaxj said:**
> ...Most of my test is done in a text mode Ubuntu (version 10.04) without x-windows and any network-manger or modem manager.
Can you point me the .iso of your Ubuntu release to test it?
Is it ubuntu-10.04.2-server-i386.iso from [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) ?
G

---

### Post by gagaxj on 2011-03-10
Thanks GeorgeVita.

Actually, we customized a version from Ubuntu 10.04 LTS desktop Edition, and made our own iso file without x-windows etc. 
"uname -a" shows
2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

As I said, I also tested in the latest 10.10 32-bit Desktop Edition with the iso name: ubuntu-10.10-desktop-i386.iso. It has the same problem to communicate with /dev/ttyUSB1.

---

### Post by GeorgeVita on 2011-03-11
Hi **gagaxj**, I just upgraded my ZTE MF636 to firmware version V1.0.4B11 (from V1.0.2B01) and I got control of ttyUSB1 (AT commands working fine). Update found at the web site of my 3G provider.

My OS Ubuntu 10.04 installation (fully updated), network-manager stopped, modem-manager killed, connection via single line pppd commaaaaand:

```
g@gPC:~$ uname -a
Linux gPC 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
g@gPC:~$ sudo stop network-manager
[sudo] password for g: 
network-manager stop/waiting
g@gPC:~$ sudo killall modem-manager
g@gPC:~$ sudo pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 172.1...
remote IP address 10.64.64.64
primary   DNS address 212.1...
secondary DNS address 212.1...

```

From a second terminal window:
minicom -s
serial port setup
A
change to /dev/ttyUSB1 & press <enter>
press <enter>
press <esc>
INITIALIZING MODEM (defaults I did not change anything, will be better to remove all init strings)
and then:

```
g@gPC:~$ minicom -s


Welcome to minicom 2.4

OPTIONS: I18n                                                                
Compiled on Jan 25 2010, 06:49:09.                                           
Port /dev/ttyUSB1                                                            
                                                                             
Press CTRL-A Z for help on special keys                                                    
                                                                                           
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0                                                           
OK                                                                                         
at                                                                                         
OK                                                                           
at+csq                                                                       
+CSQ: 8,99                              
                                        
OK                                      
at+cgdcont?                             
+CGDCONT: 1,"IP","gint.b-online.gr","0.0.0.0",0,0
                                        
OK



```

usb_devices listed as:
```
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF662_ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

```

Serial# shows MF662 but this is an MF636 bought before 3 years. Possibly this 'logo' changed after recent upgrade. Later I will check if my bug gone now!

This message written connected using above method with minicom working in parallel. Command at&v shows:
```
OK
at&v
&C: 1; &D: 2; &E: 0; &F: 0; &S: 0; &W: 0; E: 1; L: 1; M: 0; Q: 0; V: 1;
X: 4; Z: 0; \Q: 3; \S: 0; \V: 0; S0: 0; S2: 43; S3: 13; S4: 10; S5: 8;
S6: 2; S7: 45; S8: 2; S9: 6; S10: 14; S11: 95; S30: 0; S103: 1; S104: 1;
+FCLASS: 0; +ICF: 3,3; +IFC: 2,2; +IPR: 115200; +DR: 0; +DS: 0,0,2048,6;
+WS46: 12; +CBST: 0,0,1;
+CRLP: (61,61,48,6,0),(61,61,48,6,1),(240,240,52,6,2);
+CV120: 1,1,1,0,0,0; +CHSN: 0,0,0,0; +CSSN: 0,0; +CREG: 0; +CGREG: 0;
+CFUN:; +CSCS: "IRA"; +CSTA: 129; +CR: 0; +CRC: 0; +CMEE: 2; +CGDCONT: (1,"IP","gint.b-online.gr","0.0.0.0",0,0)
; +CGDSCONT: ; +CGTFT: ; +CGEQREQ: ; +CGEQMIN: ; +CGQREQ: ; +CGQMIN: ;
+CGEREP: 0,0; +CGDATA: "PPP"; +CGCLASS: "A"; +CGSMS: 1; +CSMS: 0;
+CMGF: 0; +CSAS: 0; +CRES: 0; +CSCA: "+3069xxxxxxx",145; +CSMP: ,,0,0;
+CSDH: 0; +CSCB: 0,"",""; +FDD: 0; +FAR: 0; +FCL: 0; +FIT: 0,0; +ES: ,,;
+ESA: 0,,,,0,0,255,; +CMOD: 0; +CVHU: 1; +CPIN: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;
+CMEC: 0,0,0; +CKPD: 1,1; +CIND: 0,1,1,1,0,0,1,0; +CMER: 0,0,0,0,0;
+CGATT: 1; +CGACT: 0; +CPBS: "SM"; +CPMS: "ME","ME","ME"; 
+CNMI: 3,1,0,2,0; +CMMS: 0; +FTS: 0; +FRS: 0; +FTH: 3; +FRH: 3; +FTM: 96;
+FRM: 96; +CCUG: 0,0,0; +COPS: 0,0,""; +CUSD: 0; +CAOC: 1; +CCWA: 1;
+CCLK: ""; +CLVL: 2; +CMUT: 0; +CPOL: 0,2,"",0,0,0; +CPLS: 0; +CTZR: 0;
+CTZU: 0; +CLIP: 1; +COLP: 0; +CDIP: 0; +CLIR: 0; +ZSNT: 0,0,0;
+ZOPRT: 0; +CMVL: 0

OK

```

**[SIZE="3"]edit:[/SIZE]** this firmware update solve [bug#408555]("https://bugs.launchpad.net/bugs/408555"), thanks for forcing me to do new tests!
I can take control of /dev/ttyUSB1 using **minicom** from terminal
Alternatively you can use the command: **screen /dev/ttyUSB1**
Read about screen from terminal: **man screen**
If the port 'stucks' for any reason check if any 'screen' is running: **ps -A | grep screen**
and stop it: **killall screen**

**[SIZE="3"]2nd edit:[/SIZE]** Using latest daily-live build of Ubuntu 11.04 I cannot access /dev/ttyUSB1 using screen command as it is locked by NM+MM. NM icon now shows the signal level!

**[SIZE="3"]3rd edit:[/SIZE]** Best source for the firmware update is your 3G data provider as some 'customization' may included. 
**ZTE firmware:** [http://www.zte.com.cn](http://www.zte.com.cn) from top menu choose **Support > Handset Services >** choose **country** and read carefully the description/model/instructions before updating!

Regards,
George

---

### Post by gagaxj on 2011-03-11
Thanks GeorgeVita for your great help!

I will find a way to upgrade the firmware from my provider and post the results as soon as I can.

Have a nice weekend!



[B]edit: 
[/B]

I have updated the firmware, and it works correctly by now. Thank you so much George.

---

