---
title: "Huawei E173...have spent 3 days trying to connect to the net"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by ltwinner on 2010-11-04
I am having desperate problems trying to connect to the net with a Huawei E173 USB modem. I was using Linux Mint 7 which I upgraded to version 9 today to see if that would fix the problem but it made no difference.

Basically it seems the only time I can connect to the net in linux is if I use the modem in windows and then restart straight into linux, in that case it sometimes gets recognised and works. So at least I know it can work.

Can someone please give me steps to take to get this fix this problem, I've been trying loads of stuff like usb_modeswitch I found on the net but none of it has worked. Here is what ls-usb gives me -

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Can someone please give me steps to take to solve this problem as I am unable to get any work done without the net and I will not have access to a wired connection til the new year.

---

### Post by ltwinner on 2010-11-04
I'd appreciate if someone could give me a guide on how to get this modem recognised and working...before I start kicking the monitors off my desk, this is really starting to **** me off.

---

### Post by The Foz on 2010-11-04
Sounds like you don't have the PIN number configured in Linux. It probably works when rebooting from Windows into Linux because the device doesn't power down in this case, and so the connection session is already authenticated fro Windows.

In recent versions of Ubuntu, there is a wireless applet in which you can set all the configuration. If your Linux doesn't have that, and you can't download it, then you will need to create a dialer configuration file. Here is an example:
```
[Dialer PIN]
Modem = /dev/ttyUSB0
Baud = 3600000
SetVolume = 0
FlowControl = NOFLOW
Init1 = ATZ
Init2 = AT+CPIN="7198"
Dial Attempts = 1

[Dialer PUK]
Modem = /dev/ttyUSB0
Baud = 3600000
SetVolume = 0
FlowControl = NOFLOW
Init1 = ATZ
Init2 = AT+CPIN="88563507"
Dial Attempts = 1

[Dialer umts]
Username = username
Password = password
New PPPD = yes
Phone = *99***2#
Stupid Mode = 1
Modem = /dev/ttyUSB0
Baud = 3600000
SetVolume = 0
FlowControl = NOFLOW
Carrier Check = no
Dial Command = ATDT
Init1 = ATZ
Init2 = ATM0
Init3 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","web.vodafone.de"
Dial Attempts = 3

[Dialer Huawei]
Modem = /dev/ttyUSB0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99***1#
Username = ppp
Password = ppp
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1 
```

---

### Post by ltwinner on 2010-11-04
What is the name of that wireless applet?

---

### Post by ltwinner on 2010-11-05
OK well I took the sim card out of the modem and put it in my phone and turned off pin lock. So it no longer requires a pin to connect, I just checked it in windows. The modem's light now flashes blue instead of green.

Anyway, I still cant connect and I still get the same output from lsusb -
Bus 002 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 

When the device does connect (which happens sometimes when I boot windows and then restart into linux) it looks like -
Bus 002 Device 002: ID 12d1:**140c** Huawei Technologies Co., Ltd. 

So can someone tell me how to switch it to  12d1:140c permanently in linux?

---

### Post by The Foz on 2010-11-05
This is the website for the "NetworkManager" applet: [http://projects.gnome.org/NetworkManager/]("http://projects.gnome.org/NetworkManager/")

I highly recommend it.

---

### Post by niallb on 2010-11-06
To switch your modem to the correct ID, the tool you use is indeed usb_modeswitch .
It works after windows has had it because windows has already run the modeswitch on it,
not because it's already connected and authenticated.
Unless this switch takes place, Ubuntu can only use the device as a small cdrom.
The one you list actually appears to be an E1692, an E1752 or a few other models rather than an E173.

What exactly have you tried typing in for usb_modeswitch ?
If you do get it to switch, you should be able to attach the driver with a command such as :

*modprobe -v usbserial vendor=0x12d1 product=140c*

Did you install the usb-modeswitch (and usb-modeswitch-data) packages, or download a usb_modeswitch binary from another website? Which version do you have?

---

### Post by fparri on 2011-01-07
Could you use it on Linux, in the end? I would like to buy it and need to know ;)

---

### Post by Blurey on 2011-01-07
> **niallb said:**
> To switch your modem to the correct ID, the tool you use is indeed usb_modeswitch .
It works after windows has had it because windows has already run the modeswitch on it,
not because it's already connected and authenticated.
Unless this switch takes place, Ubuntu can only use the device as a small cdrom.
The one you list actually appears to be an E1692, an E1752 or a few other models rather than an E173.

What exactly have you tried typing in for usb_modeswitch ?
If you do get it to switch, you should be able to attach the driver with a command such as :

*modprobe -v usbserial vendor=0x12d1 product=140c*

Did you install the usb-modeswitch (and usb-modeswitch-data) packages, or download a usb_modeswitch binary from another website? Which version do you have?


[pablo:driver] sudo gedit /etc/usb_modeswitch.conf
########################################################
# Huawei E173

DefaultVendor= 0x12d1
DefaultProduct=0x1c0b

TargetVendor=  0x12d1
TargetProduct= 0x1c0b

CheckSuccess=5

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

#############################################################

# Huawei E173s

;DefaultVendor= 0x12d1
;DefaultProduct= 0x1c0b

;TargetVendor= 0x12d1
;TargetProduct= 0x1c0b

;CheckSuccess=20

MessageEndpoint= 0x0f
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
####################################################

[http://www.fedoraforum.org/forum/showthread.php?t=255234](http://www.fedoraforum.org/forum/showthread.php?t=255234)

---

### Post by RazTaz on 2011-06-05
Try [this]("http://forum.ubuntu.ro/viewtopic.php?pid=106458"):

1. Download the Huawei E173 drive for linux. I found it [here](http://frontlinesms.ning.com/forum/attachment/download?id=2052630%3AUploadedFile%3A51370).

2. Unzip the linux.zip file in a convenient location, for instance on the desktop. Upon decompressing you'll have a new folder: ~/Desktop/Linux/

3. Right click on each individual file in the folder ~/Desktop/Linux/, chose >> Proprieties >> Permissions - read and write all + check on "Allow executing as a program"

4. Open a terminal window (CTRL+ALT+t) and write in command line:
```
cd ~/Desktop/Linux/
```
then
```
sudo ./install
```
and press Enter on all questions.

The Huawei E173 driver will install (the default installation path is in /usr/local/) together with a specific connection program called Moviestar 3.5G/Mobile Partner (program which we will ignore for the future. If it pops up, you can close it with absolutely no problem).

5 - From this step on everything is simple and related to the installation of 3G broadband modems in general - the standard tutorial.
5.a - stick the modemul in an usb port.
5.b. - [This movie](http://www.youtube.com/watch?v=8WtX4LK0pDE) gives you all the information you need.
5.c. - A new Device is found in Network Applet Manager. Click on it and choose connect.

---

### Post by paulplunkett on 2011-06-18
hey, 
i followed the instructions you gave about how to install the driver and i had the following error:

Install NDIS driver failed.
The compiling environment is not all ready.
Please check gcc, make and kernel build(/lib/modules/2.6.32-21-generic/build) to be all installed?

Any idea what this means??? i press Y to this and it said:

NDIS is disabled, and only modem can be used.

Still not sure what to do.

---

### Post by metallus on 2011-07-12
do you have this package installed: build-essential ?
if you did install it, please install the kernel headers like so:
open a terminal and type: sudo apt-get install linux-headers-`uname -r`
then try to compile the program again.

---

### Post by BwanaDNA on 2011-08-23
Thanks a bunch,I was having the same problem,you just made my day!!!!!!

Oh, for those who are yet to catch on - IT WORKS:)

---

### Post by mssrahul on 2011-09-27
hey try this !!! Download "universal mastercode.exe" crack from Google then execute it in windows or even in ubuntu using wine. enter your modems IMEI no. which is in the modem itself. now install MOBILE PARTNER in ubuntu and enter the pin generated by crack in mobile partner. Now you'll be able to connect your modem either through mobile partner or even by network manager !!!!.....

---

### Post by blureye on 2011-10-10
hi, 

I've just gotten my huawei e173 from my ISP, was managed to install the software into my fujitsu - window vista.  I am not able to access to internet even though the mobile partner is able to connect to the 3G.  :(
I tried the modem in my friend samsung-window7, it works well.
I guess it's my window vista problem..

May I know what should I fix?  Should I download any other drivers for my window vista?

---

### Post by pdc on 2011-10-11
please copy and paste this command into a terminal

> dmesg | grep tty

.........if you have to type this command out the vertical line is SHIFT-\



please copy and paste the result back here

also please copy and paste back 

> lsusb

---

### Post by dineshs on 2011-10-28
I have an E173 and I use [this]("http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html") to connect.

---

### Post by cepraksanta on 2012-05-10
> **pdc said:**
> please copy and paste this command into a terminal



.........if you have to type this command out the vertical line is SHIFT-\



please copy and paste the result back here

also please copy and paste back

cepraksanta@cepraksanta-TravelMate-2480:~$ dmesg | grep tty 
[    0.000000] console [tty0] enabled
[   31.503280] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[   31.507812] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[   31.510428] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 2906.954344] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 2906.959888] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 2906.961678] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4042.367204] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4042.380339] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4042.382645] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 4067.228971] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4067.237751] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4067.238572] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4076.815830] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4076.820665] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4076.826162] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 4101.628923] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4101.652387] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4101.652535] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4111.195295] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4111.204849] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4111.210415] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 4135.764527] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4135.776534] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4135.777095] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4145.239446] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4145.250974] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4145.251299] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 4170.041772] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4170.060387] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4170.060531] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4179.485696] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4179.496343] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4179.499554] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
cepraksanta@cepraksanta-TravelMate-2480:~$ 

i'm using xubuntu 12.04 and have a problem with e173 huawei... please help. Thanks

---

### Post by cepraksanta on 2012-05-10
Guys, i have solved problem with huawei e173
1. You can check it on  [http://askubuntu.com/questions/126854/problem-connecting-internet-through-usb-modem-micromax](http://askubuntu.com/questions/126854/problem-connecting-internet-through-usb-modem-micromax)

Raj giving solution like this:
I had the same problem too. if your usb modem doesnt not detect as usb mass storage,then try this. open terminal type [B]lsusb
[/B]for example: $ lsusb
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 005: ID 1c9e:9605 OMEGA TECHNOLOGY
  Note down the id of your device i.e from above example 1c9e:9605
  and in terminal type **sudo modprobe usbserial vendor=0x1c9e product=0x9605**
  it will ask for user passwd if required. then wait for some minutes 
  check the network manager applet if detect it will show the **new mobilebroadband gsm** or cdma,then click the new mobilebroadband. if not detected try to remove modem and connect it
  type same cmd **sudo modprobe usbserial vendor=0x1c9e product=0x9605**
and wait for some minutes. and check network manager and i think you have to do this every time you reboot the system, till ubuntu team find solution for this. 



2. You can search on Ubuntu Software Center: D-Bus service for managing modems - debugging symbols. Install it. It will recognize your huawei e173 modem...


There's all from me. Hope's my solution useful. At least it's work on my PC.

---

### Post by Nikshay on 2012-05-26
Hi

I am too is struggling with this problem, 

These steps does not worked for me....

***********************************************************
1. Download the Huawei E173 drive for linux. I found it here.

2. Unzip the linux.zip file in a convenient location, for instance on the desktop. Upon decompressing you'll have a new folder: ~/Desktop/Linux/

3. Right click on each individual file in the folder ~/Desktop/Linux/, chose >> Proprieties >> Permissions - read and write all + check on "Allow executing as a program"

4. Open a terminal window (CTRL+ALT+t) and write in command line:
Code:
cd ~/Desktop/Linux/
then
Code:
sudo ./install
and press Enter on all questions.

The Huawei E173 driver will install (the default installation path is in /usr/local/) together with a specific connection program called Moviestar 3.5G/Mobile Partner (program which we will ignore for the future. If it pops up, you can close it with absolutely no problem).

5 - From this step on everything is simple and related to the installation of 3G broadband modems in general - the standard tutorial.
5.a - stick the modemul in an usb port.
5.b. - This movie gives you all the information you need.
5.c. - A new Device is found in Network Applet Manager. Click on it and choose connect.
************************************************************

Please help me to solve this problem

I am using Ubuntu 10_04_02 (x64)

Thanks in advance

---

### Post by alexfish on 2012-05-28
Have a look here
			 			[Huawei Mobile Broadband Devices (Ubuntu 12.04)]("http://ubuntuforums.org/showthread.php?t=1974458")

same drivers will work from 10.04 up

---

### Post by krishnacbhatt on 2012-08-20
> **RazTaz said:**
> Try [this]("http://forum.ubuntu.ro/viewtopic.php?pid=106458"):

1. Download the Huawei E173 drive for linux. I found it [here]("http://frontlinesms.ning.com/forum/attachment/download?id=2052630%3AUploadedFile%3A51370").

2. Unzip the linux.zip file in a convenient location, for instance on the desktop. Upon decompressing you'll have a new folder: ~/Desktop/Linux/

3. Right click on each individual file in the folder ~/Desktop/Linux/, chose >> Proprieties >> Permissions - read and write all + check on "Allow executing as a program"

4. Open a terminal window (CTRL+ALT+t) and write in command line:
```
cd ~/Desktop/Linux/
```then
```
sudo ./install
```and press Enter on all questions.

The Huawei E173 driver will install (the default installation path is in /usr/local/) together with a specific connection program called Moviestar 3.5G/Mobile Partner (program which we will ignore for the future. If it pops up, you can close it with absolutely no problem).

5 - From this step on everything is simple and related to the installation of 3G broadband modems in general - the standard tutorial.
5.a - stick the modemul in an usb port.
5.b. - [This movie]("http://www.youtube.com/watch?v=8WtX4LK0pDE") gives you all the information you need.
5.c. - A new Device is found in Network Applet Manager. Click on it and choose connect.

worked for me !!!!!!!!!!!!! thanx a lot:)!!!!!

---

