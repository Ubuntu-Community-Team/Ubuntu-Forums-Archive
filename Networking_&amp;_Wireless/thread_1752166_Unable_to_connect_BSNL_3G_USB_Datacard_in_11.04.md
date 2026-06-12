---
title: "Unable to connect BSNL 3G USB Datacard in 11.04"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by rawfool on 2011-05-07
Ubuntu 11.04 isn't detecting BSNL 3G USB Datacard. I was using 10.04 earlier & could easily install it then. But now 11.04 isn't detecting the USB datacard, so I'm unable to connect to internet for updates. Please help me with this. Thank you.

---

### Post by alexfish on 2011-05-07
need to know if the system was an up-grade or clean install
try these commands from the terminal
```
nm-tool
```
```
usb-devices
```locate the lines indicating the device and post only those lines

---

### Post by rawfool on 2011-05-10
It's a clean install with dual-boot, dude. Earlier I was using 10.04 which I installed through Wubi. I thought of trying 11.04, so I uninstalled, then installed 11.04 through Wubi again. All in **F:\** partition.

// -----

Now fearing that I cannot to internet, I uninstalled 11.04 also and tried to install 10.04 back. But after installation, when I try to login, it's showing the same login screen again. After that I tried to install manually by using CD, but it's saying that **Reboot Error**.

So now I'm thinking to reinstall my Vista(only on **C:\**), as there might be some dependencies with the current log files, so might be the error. Do you have any suggestions please?
Thanks for ur reply.

---

### Post by alexfish on 2011-05-10
For instalation problems can try looking here or start new thread
 [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")
 

 also look here ,  
 [Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312")
 have post with reference to usb-modeswitch Post #**[30]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")**

---

### Post by desaivarun_104lts on 2011-05-14
@alexfish

Hi,I am also facing the same issue.The provider is BSNL 3G.The data card is teracom..I am attaching the output of the two commands you mentioned..

Please help me in this issue.

-------------------------------------------------------------------


varun@varun-AO532h:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        70:5A:B6:CD:D5:4F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        F0:7B:CB:7C:61:F5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: ttyACM3 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:


varun@varun-AO532h:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  3
P:  Vendor=230d ProdID=0001 Rev=00.00
S:  Manufacturer=HSPADataCard
S:  Product=HSPADataCard
S:  SerialNumber=8444311594054030
C:  #Ifs=10 Cfg#= 3 Atr=e0 MxPwr=20mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=09 Prot=01 Driver=cdc_wdm
I:  If#= 6 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 7 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=064e ProdID=a102 Rev=03.10
S:  Manufacturer=SuYin
S:  Product=WebCam
S:  SerialNumber=CN0316-S30C-OV11-VA-R03.01.00
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

-----------------------------------------------------------------

---

### Post by alexfish on 2011-05-14
Hi

first time seen a device with this driver set up , 
> I: If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I: If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I: If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I: If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=09 Prot=01 Driver=cdc_wdmintial "thoughts" , for each of the cdc_acm then there will be a ttyACM* , 0 been the first in the list
normally the device would connect on a Cls=02(commc) port

looking at the nm-tool listing shows ttyACM3

if the numerical listing be correct then looks as if this port could be a data port , but not sure
have you configured Network Manager with the details , and tried the connection

also need some more info , can post results of
```
ls -al /dev/serial/by-id
```will then look further / also it may be wise to install wvdial just incase NM is not linking to the correct port, but as said I am not sure of this.

alexfish

---

### Post by desaivarun_104lts on 2011-05-15
varun@varun-AO532h:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-05-15 08:41 .
drwxr-xr-x 4 root root 80 2011-05-15 08:41 ..
lrwxrwxrwx 1 root root 13 2011-05-15 08:41 usb-HSPADataCard_HSPADataCard_8444311594054030-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-05-15 08:41 usb-HSPADataCard_HSPADataCard_8444311594054030-if03 -> ../../ttyACM1

-------------------------------------------------------------------------
Apart that,i am also posting the output of lsusb,where there is number,but it not recongized
--------------------------------------------------------------------------

varun@varun-AO532h:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 230d:0001  
Bus 001 Device 002: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
--------------------------------------------------------------------------the 230d:0001 is my 3g data card..

---

### Post by alexfish on 2011-05-15
Hi

shows two ports ttyACM0 and ttyACM1.

again these are thoughts, since I do not have such a device.

this device may have two modes of operation since only part of the device is listing in the " /dev/serial". so leaning towards ttyACM0 for the dial up and ttyACM0 as a data port for getting other info or sending commands. the other part of the device may have a usb net interface , these usually show on the system as usb0, but not sure about this device. so need to find where it is on the system, first going to look at network interfaces can post the results of "ifconfig" command
```
ifconfig -a 
```
also can try get info from the device
post the results of
open up first terminal to monitor the modem, then enter this command
```
tr -s "\n" < /dev/ttyACM0
```
open up second terminal and enter the following commands , they may or may not work
```
echo -e "AT\r" > /dev/ttyACM0 
```if there is a responce , continue
```
echo -e "ATI\r" > /dev/ttyACM0 
```if there is a responce , continue
```
echo -e "AT+CSQ\r" > /dev/ttyACM0
``` signal strenth
```
echo -e "AT+CGDCONT?\r" > ttyACM0
``` find APN or locations for cid dialing
can also try default dial command
```
echo -e "ATDT*99#\r" > ttyACM0 
```if there is a CONNECT message then a ppp conection may work
can try this command from the terminal
```
sudo pppd debug ttyACM0 nodetach defaultroute dump noipdefault usepeerdns usehostname ktune logfd 2 noauth name user maxfail 3 
```

as previously mentioned try wvdial, if the above works. to configure wvdial
```
sudo wvdialconf
```
see what happens

---

### Post by desaivarun_104lts on 2011-05-15
@Alexfish,

Thanks for you work towards the device..I kept the device in windows and extracted the linux installation .deb file which is given in the device,and installed the deb file.

After installing,after few attempts the device started connecting,now the device is working properly,without using the netwrok manager,BSNL provided a software,it started working.

I will attach a screenshot of the software.

Once again,thanks for your valuable suggestion.

---

### Post by rawfool on 2011-05-16
@ desaivarun_104lts - Oh.. I didn't try this. Thank you. Anyway fearing about some bugs in 11.04, I've switched back to 10.04.

@ alexfish - Thanks for your patience & replies dude.

---

### Post by alexfish on 2011-05-16
> **desaivarun_104lts said:**
> @Alexfish,

Thanks for you work towards the device..I kept the device in windows and extracted the linux installation .deb file which is given in the device,and installed the deb file.

After installing,after few attempts the device started connecting,now the device is working properly,without using the netwrok manager,BSNL provided a software,it started working.

I will attach a screen-shot of the software.

Once again,thanks for your valuable suggestion.

Hi all

good to see a provider doing the right thing

Had noted from the listing a sound driver , 
> I: If#= 7 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I: If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
so looked up all the drivers mentioned from the listing, and thought the sound driver may be loading due to then Vendor ID or possible something in the modalias of the device , so may be confusing Network Manager or Modem Manager.

Can you do something for the Linux Community by post some udev listing of the devive for future reference , as these would have been the next requests , for each of the below can open up a seperate terminal,connect the device,then make the connection with the software,can then puts all the info in one file , zip the file
and upload to attachments 

```
udevadm monitor -e | grep DRIVER
```
```
udevadm monitor -e | grep INTERFACE
```
```
udevadm monitor -e | grep modem
```
```
udevadm monitor -e | grep tty
```
```
udevadm monitor -e | grep /dev/
```
```
udevadm monitor -e | grep MODALIAS
```finally the listing of the "usb-devices" once connected
```
usb-devices 
```can locate the parts which indicate the device and post only those parts

Thanks in advance and
Regards alexfish

---

### Post by desaivarun_104lts on 2011-05-19
Hi,

None of the above commands did nothing..The cursor is just blinking in the terminal, waited about 5 minutes...

---

