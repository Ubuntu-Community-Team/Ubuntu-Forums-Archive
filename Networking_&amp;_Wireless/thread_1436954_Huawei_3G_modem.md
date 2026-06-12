---
title: "Huawei 3G modem"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by conniemalan on 2010-03-23
Where can I find any notes on how to use a USB HUAWEI 3G modem

Thanks

---

### Post by Nikusha on 2010-03-23
Just plug it in and Ubuntu would recognise it.

Click on the network applet in the panel and connect...

Or right click and edit, new connection, 3G connections and set it up from there

---

### Post by pdc on 2010-03-23
exactly as Nikusha describes

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

see half-way down page:

"Create a mobile broadband connection"

---

### Post by Sven6210 on 2010-03-24
Using a 3G device with Ubuntu can be very easy and very difficult - it simply depends on the hardware you are using.

The 'Huawei E160' for example works out of the box. You do not have any issue with the 'modeswitch' from storage mode to modem mode and the network manager makes the set-up very easy.

The 'Huawei E1750' caused me some trouble in the past and I did not manage to get it to work. In the end I gave up and used the 'E160' which works that easily. Whether or not the 'Huawei E1750' works under Linux I am not 100 % sure. 

However, I am sure that some 3G devices have trouble with Linux (or the other way round). One of the December issues of the German computer magazine ' c't ' tested different devices from Huawei, Optio etc. under Windows, Linux and Apple OS and the result was that even tehy did not manage all devices to work under Linux. And that is one of the better computer magazines with people that know what they are talking about - not a magazine which is just a collection of ADs.

Last but not least I also bought the 'Huawei E5830' which has some problems with Linux when connected via USB. As this device offers WLAN you can always connect your Linux machine through the WLAN and the E5830 builds up the 3G connection. Great hardware but as I said, limited to WLAN usage with Ubuntu so far (see some other posts from me).

Before buying any 3G hardware for a Linux computer I recommend to check in the internet whether it works well under Linux.

---

### Post by nmlferreira on 2010-07-11
Did you make it work via USB?
I tried and tried... and nothing.
When I try to run the auto-run file, I just get a warning message, saying that this isn't a zip file??

---

### Post by pdc on 2010-07-12
nmlferreira

plug your modem into your computer

**copy and paste** these two commands into a terminal: 

(are you happy to do that?)

and **copy and paste** back the answers you get

> lsusb

and 

> dmesg | grep tty

---

### Post by nmlferreira on 2010-07-12
pdc,
I made as you told me.
The result is in the attached file.
The first one (lsusb) listed all usb connections in use.
I could only run dmesg l.
grep tty didn't work?
Maybe I'm just not using the correct definitions.
This is how I did it:
Under "Network Connections" I select "Mobile Broadband".
I fill in the country = Bitain (UK)
the provider = 3
and the plan = internet
I then chose "Connect automatically"
I'm given a number = *99#
I'm not given a "User Name", a "Password".
The APN is defined autumatically = 3Internet
And I'm not given a "Network" or a "Pin".
Where do I fill in the SSID given by the provider? and the WIFI Key?
I'm sorry if this looks to basic, but my experience with Ubuntu has less than 24h!!
Thanks,
Nuno

---

### Post by pdc on 2010-07-12
so you got this 

> ID 12d1:1446 Huawei Technologies Co., Ltd. 

and this 

> SCSI emulation for USB Mass Storage devices 

so your device is still being seen as a virtual CD-ROM device (as it comes loaded with software ............)

you need to automate the flipping of the device so linux sees it as a modem

You need to install the latest version of **usb_modeswitch**

go here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

and HALF-WAY down the page to where it says: download usb_modeswitch

if you are using 32bit ubuntu, download the i386 version;

it will what is called a .deb package, so your system will offer to install it; say "yes" and enter your sudo password when it asks;

this latest package of usb_modeswitch should auto-configure; so let it install;

when all done; reboot and plug your modem in when settled; you should be able to configure: check by doing

> lsusb

in a terminal again:

if you see something like 

> 12d1:1001 Huawei Technologies Co., Ltd. 

.. or someother different number to 1446 !! it means the device has flipped and can be configured 

Configure as here on the link below:**_ halfway down the page_** is 

"Create a mobile broadband connection"

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

> *Where do I fill in the SSID given by the provider? and the WIFI Key?*

........ Not needed for mobile broadband ......

---

### Post by nmlferreira on 2010-07-13
Pdc
I can only thank you for all your patience.
I've downloaded the usb-modeswitch_1.1.3-1_i386.deb and tried to run it through ubuntu.
It gave me an error message: Dependency can not be satisfied (translated from Portuguese): usb-modeswitch-data (>= 20100127).
Then it gives me an explanation about the ZeroCD feature.
Meanwhile I found out usb-modeswitch-data-2010623-1_all.deb and installed both with success.
I was now following the instructions to create the mobile broadband connection, which is easy, because I'd already tried it before.
The problem now is that I can't find the "Network Manager" to set this new connection as default. I looked everywhere and I found out it is installed. I just can't find where.

---

### Post by pdc on 2010-07-13
if you **copy and past**e these commands into a terminal

and then we can know what you are dealing with ..

> lsusb

and 

> dmesg | grep tty

and **copy and paste** the results back here to us please

hopefully we can get this all working for you

---

### Post by nmlferreira on 2010-07-14
Ok.
I tried the "lsusb" command yesterday and I remember one of the parameters has changed:
I had before **Bus 001 Device 006: ID 12d1:[COLOR=Red]1446[/COLOR] Huawei Technologies Co., Ltd.** and now have   **Bus 001 Device 006: ID 12d1:[COLOR=Red]1401[/COLOR] Huawei Technologies Co., Ltd.** 
From what I read in other forums, this is good news.
I'll try the dmesg command later, however the first time I did it, it looked like there were some parameters missing. Should I try "dmesg l grep -e "modem" -e "tty"?
One last thing is this Network Manager. I've been reading in several places about it, but I just can't find it on my toolbar. The only place I think it is, when I click it, it just gives me the chance to add the several types of connections: dial, wireless, broadband, etc.
Meanwile let me know if you can think of something else... it will be another sleepless night.
Thanks a lot for your support.
Nuno

---

### Post by pdc on 2010-07-15
>  ID 12d1:1401 Huawei Technologies Co., Ltd. 

okay

> *Should I try "dmesg l grep -e "modem" -e "tty"?*

if you want, but I think you would have been pleasantly surprised what

> dmesg | grep tty gave you ..

..... that's why I asked you to do it ..................

..... we need to know if you see ttyUSB0 and ttyUSB1 ...........

---

### Post by nmlferreira on 2010-07-15
pdc,
See attached the result.
I've copied as much as I could, but to be honest it's all giberish to me.
Can you make any sense of it?

---

### Post by nmlferreira on 2010-07-15
pdc
It's me again.
I was going crazy with a lot of errors and undetected usb memory sticks, that I decided to re-instal Ubunto and do all over again.
Here's the latest result of what you asked me to do.
Is it better or worse than the previous one?
Cheers,
Nuno

---

### Post by nmlferreira on 2010-07-15
Did I say I was going crazy?
I really don't know what's happening, but everytime I do the same thing, I have diferent results. Attached is the last.
To add to this, my toolbar disapeared, everytime I want to read from my pen drive, I have to eject the modem... what else can happen?

---

### Post by pdc on 2010-07-16
I think the ttyUSB0 means your device is recognised as a modem;

......... and should be ready to be configured as a modem .............

......... so ..............

if you go HALF-WAY down the page of this link

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

to 

"Create a mobile broadband connection .."

You right-click on network manager; left-most of the icons on the top right of your toolbar; having configured ...

you LEFT-CLICK and should see your entry; and LEFT click on your entry to activate

perhaps you tell us your network to ensure the correct APN is in your settings ............

---

### Post by pdc on 2010-07-16
eg here is the apn of the only vodafone portugal network listed ..

(hopefully jpg attached ...........)

---

### Post by nmlferreira on 2010-07-16
I got another problem... I can't find the Network manager anywhere.
My toolbar only has "Applications", "Places" and "System".
I usually go to "System" -> "Preferences" -> "Network Manager", to edit or add an entry.
However, when I'm checking what software is installed, I found out that "Network Manager" is one. It shows like a sideways wireless icon, with a green tick.

As for the APN, I phoned the provider "3" and they gave me two options: three.co.uk and 3internet. This last one is what the system generates automatically.
At the moment I decided to create two entries, each one with a different APN. The trouble is I can't set any of these as default.
Anything else I need to do?

---

### Post by pdc on 2010-07-16
your ubuntu doesn't sound very well;

can I suggest you consider sakis 3g instead to connect? (instead of network manager .............)

I think it works very well

[http://www.sakis3g.org/](http://www.sakis3g.org/)

click on the download button; assuming you have 32bit download the i386 system; it is a small file; follow sakis's instructions; it should offer you the choice as it loads, of which system you wish to connect to

> My toolbar only has "Applications", "Places" and "System".

that is TOP-LEFT?

TOP-RIGHT: is network manager not the most left of the TOP-RIGHT icons?

---

### Post by nmlferreira on 2010-07-18
pdc
I had a friend looking into this, but we didn't go too far.
The good news is that I now have a completr top toolbar, which never happened before.
Here are the latest information I got:


nuno@nuno-desktop:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 011: ID 08ec:0008 M-Systems Flash Disk Pioneers TravelDrive 2C 
Bus 001 Device 008: ID 12d1:1401 Huawei Technologies Co., Ltd.  
Bus 001 Device 003: ID 041e:4053 Creative Technology, Ltd Live! Cam Video IM 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
nuno@nuno-desktop:~$ dmesg|grep tty 
[    0.000000] console [tty0] enabled 
[    0.306305] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    0.306458] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    0.307215] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    0.307446] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    0.406112] tty tty16: hash matches 
[   22.355630] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0 
[   22.356991] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1 
[   22.357502] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB2 
[   90.877911] type=1503 audit(1279455439.966:15):  operation="open" pid=1404 parent=1401 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0" 
[   90.877972] type=1503 audit(1279455439.966:16):  operation="open" pid=1404 parent=1401 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB1" 
[   90.878030] type=1503 audit(1279455439.966:17):  operation="open" pid=1404 parent=1401 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB2" 
[ 1319.811352] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
[ 1319.901811] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
[ 1319.912190] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2 
[ 1515.973268] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0 
[ 1515.996692] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1 
[ 1516.004772] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB2 

Now, when I go to the link you gave me "Create a mobile broadband connection".
That's easy and I already confirmed the APN as being "3internet" and that no password is needed. Therefore the broadband is correctly configured.
Next I click the NetworkManager and:
If I left-clig, I get:
  wired network
  disconect
  VPN connections
If I right-click, I get:
  enable networking (ticked)
  enable notifications (ticked)
  connection information (can't select it)
  edit connections
  about

It doesn't appear the broadband connection I configured?
Any idea on what to do next?
Cheers,
Nuno

---

### Post by pdc on 2010-07-18
if you now left-click on network manager (NM);

do you see an option of 3internet? 

If not,

RIGHT-CLICK on NM;

select EDIT CONNECTIONS;

click on mobile broadband;

Is there an option already set up for 3internet?

IF NOT, click on ADD;

now select your country and network;

MAKE SURE you select the correct 3 plan .........

there is a drop=down arrow there ........... offering options ..

now accept when all done

_________________

now LEFT-CLICK on NM;

do you now see a 3internet option?

If so, LEFT-CLICK on it .........

if you have credit in your account; ........ it should connect ......

---

### Post by nmlferreira on 2010-07-20
I give up!!!
I've decided to take another route.
I'll plug a usb stick with wireless and try connecting that way.
If it doesn't work, I'll be back.
Thank you a lot for all your support.

---

### Post by alexfish on 2010-07-20
why give up . the info from the below indicates the device has configured and ready to be used , although , the network manager as you say can't see the device.
[ 1515.973268] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1515.996692] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1516.004772] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB

does inserting the device after booting up make any difference

Also can you tell us which version of UBUNTU  are you using,

Knowing the Version may help us to Identify the problem

regards

alexfish

---

### Post by pdc on 2010-07-21
I wonder too if you have the correct APN 

this article 

[http://www.talk3g.co.uk/showthread.php?6126-Anyone-got-the-APN-setting-for-3](http://www.talk3g.co.uk/showthread.php?6126-Anyone-got-the-APN-setting-for-3)

talks of 

> three.co.uk

and this 

[http://www.filesaveas.com/gprs.html](http://www.filesaveas.com/gprs.html)

---

### Post by nmlferreira on 2010-07-21
Well... I'm just inclined to the wireless option, because as soon as I pluged it in, it was recognized right away.
I'm using the latest version of ubuntu: 10.4

Regarding the APN, I already spoke with "3" and they told me that 3internet is usually used for the broadband and three.co.uk for handsets. Those are the automatic options ubuntu gives me when I try to configure the broadband.
I even created both, but I can't make the network manager to let me chose which one to use.

I also trided Gnome-PPP and a third one which I can't remember now (it was only a script), but it also didn't work.

I'll try to sort something out later this week, wireless or not and let you know.
Thaks again for all support and patience.

---

### Post by nmlferreira on 2010-07-26
Hi again,
   
  I've spent this last week reading some guidelines of how to use the Network Manager and the Gnome-PPP.
  After trying everything I could understand, the result was none.
  My poor knowledge of this system and how things work, were enough to understand that the modem is being recognized, however I don't know what to do next.
   
  I've tried a usb stick with wireless and it worked... for 5 minutes.
  The system recognized right away all the wireless networks available and I was even able to connect to mine. However it only lasted 5 minutes. Then the connection was terminated and I wasn't able to connect to it again.
   
  I'm now going back and try to establish the broadband, by connecting my Huawei E5830 via usb.
  Below are the commands I learned and outputs.
  I need guidance from this point onwards.
  
  **nuno@nuno-desktop:~$ lsusb**
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 001 Device 005: ID 12d1:1401 Huawei Technologies Co., Ltd. 
  
  Bus 001 Device 003: ID 041e:4053 Creative Technology, Ltd Live! Cam Video IM
  
  Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
  
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
  *Note:*
  *Device 005 is the modem, I understand that. I also understand that the &#8220;1401&#8221; is important, however   don't know what it means.*
  *Device 003 is a web camera. I'm not interested on this yet.*
  *Device 002 is a hub with 4 ports, where both the modem and the camera are connected.*
   
  **nuno@nuno-desktop:~$ dmesg|grep tty**
  
  [    0.000000] console [tty0] enabled
  
  [    0.308137] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  
  [    0.308287] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
  
  [    0.309041] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  
  [    0.309335] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
  
  [   22.615746] usb 1-1.4: GSM modem (1-port) converter now attached to ttyUSB0
  
  [   22.617185] usb 1-1.4: GSM modem (1-port) converter now attached to ttyUSB1
  
  [   22.620639] usb 1-1.4: GSM modem (1-port) converter now attached to ttyUSB2
  
  [   90.116924] type=1503 audit(1280090938.212:15):  operation="open" pid=1419 parent=1416 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"
  
  [   90.116989] type=1503 audit(1280090938.212:16):  operation="open" pid=1419 parent=1416 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB1"
  
  [   90.117046] type=1503 audit(1280090938.212:17):  operation="open" pid=1419 parent=1416 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB2"
  
   
  *Note:*
  *I don't really know what to make of this, but lines 6, 7 and 8 lead me to believe that the modem is being recognized as a modem.*
   
  **nuno@nuno-desktop:~$ sudo wvdialconf**
  
  Editing `/etc/wvdial.conf'.
  
   
   
  Scanning your serial ports for a modem.
  
   
   
  ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
  
  ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
  
  ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
  
  ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
  
  ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
  
  ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
  
  Modem Port Scan<*1>: S2   S3   
  
  WvModem<*1>: Cannot get information for serial port.
  
  ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
  
  ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
  
  ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
  
  WvModem<*1>: Cannot get information for serial port.
  
  ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
  
  ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
  
  ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
  
  WvModem<*1>: Cannot get information for serial port.
  
  ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
  
  ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
  
  ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
  
   
   
   
   
  Sorry, no modem was detected!  Is it in use by another program?
  
  Did you configure it properly with setserial?
  
   
   
  Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
  
   
   
  If you still have problems, send mail to <[EMAIL="wvdial-list@lists.nit.ca"]wvdial-list@lists.nit.ca[/EMAIL]>.
  
   
  *Note:*
  *I just tried this command and one doesn't have to be a genius to understand that &#8220;no modem was detected&#8221;.*


What should be my next step?

By the way, I'm using Ubuntu 10.4

---

### Post by alexfish on 2010-07-26
[B]Exmaple :Testing a external usb 3g modem from the Command line {Terminal}
[/B]
Boot the computer without the device then connect the device { allow approx 30sec for the device to settle }
open up first terminal and enter this code

code:
ls -al /dev/serial/by-id/usb*

Eample reply:

lrwxrwxrwx 1 root root 13 2010-06-19 13:30 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-06-19 13:30 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1

try testing each port listed above untill you get the "CONNECT" reply

To monitor the devivc now enter this code {edit the "ttyX According to the results of the " ls -al /dev/serial/by-id/usb* " command

Code:
tr -s "\n" < /dev/ttyUSB0

Open up second teriminal and endter these codes

Codes:

echo -e "ATZ\r" > /dev/ttyUSB0

find the baud rate

Code:

echo -e "AT+IPR\r" > /dev/ttyUSB0

Example reply

115200

find the CGDCONT profiles for <cid> dialing {and APNs }

Code:

echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0

Example reply

example response use :for <cid> dialing . 
+CGDCONT: 1,"IP","general.t-mobile.uk","0.0.0.0",0,0 can try ATDT*99# or ATDT*99***1#
+CGDCONT: 2,"IP","payandgo.o2.co.uk","0.0.0.0",0,0  can try ATDT*99***2#
+CGDCONT: 3,"IP","m-bb.o2.co.uk","0.0.0.0",0,0 can try ATDT*99***3#
 


 send the dial command editing the ATDT<phone number>
 
 Code:
 echo -e "ATDT*99#\r" > /dev/ttyUSB0
 
 example response { shows the modem has connected and ready to respond ready to respond }
 
 CONNECT
 
if you get a "NO CARRIER " message from the first terminal try the dial cammand 3 times then try a different port

Now call the ppp Daemon
 
Code:
sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns
 
If username and password required append the abvove with user < user> password <yourpassword>

example response:
 
 [sudo] password for alexfish: <enter your login password for ubuntu >
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
PAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 10.158.21.15
remote IP address 10.64.64.64
primary   DNS address 149.254.201.126
secondary DNS address 149.254.192.126

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

### Post by nmlferreira on 2010-07-26
Thanks, I'll give it a go.

> **alexfish said:**
> 
try testing each port listed above untill you get the "CONNECT" reply

How do I test the ports?

> **alexfish said:**
> 
[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

This link has been my bedtime reading for this past week... it hasn't been easy, but I'll try again.

---

### Post by alexfish on 2010-07-26
> **nmlferreira said:**
> Thanks, I'll give it a go.


How do I test the ports?



This link has been my bedtime reading for this past week... it hasn't been easy, but I'll try again.

try statserial mentioned at post #16

The how to link will be updated in while / looking at further methods to check the serial port lines , for debugging

regards

alexfish

---

### Post by nmlferreira on 2010-07-27
I have good news and bad news...
The bad news first:
   
The first bit worked:
   
  **nuno@nuno-desktop:~$ ls -al /dev/serial/by-id/usb***
  lrwxrwxrwx 1 root root 13 2010-07-26 19:49 /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if00-port0 -> ../../ttyUSB2
  
  lrwxrwxrwx 1 root root 13 2010-07-26 19:49 /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if02-port0 -> ../../ttyUSB1
  
  lrwxrwxrwx 1 root root 13 2010-07-26 19:49 /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if03-port0 -> ../../ttyUSB0
  
   
  As for testing the ports by using &#8220;statserial&#8221;... not so lucky:
   
  **nuno@nuno-desktop:~$ statserial**
  The program 'statserial' is currently not installed.  You can install it by typing:
  sudo apt-get install statserial and when I try to install it:
   
**   nuno@nuno-desktop:~$ sudo apt-get install statserial**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Couldn't find package statserial
  
  I'll have to find this package before going any further.

Now the good news:
I was finally able to connect via wireless.
I read through a thread about using the Windows drivers so that Ubuntu can recognize the hardware and it worked.
If it continues, I'll leave it as it is. If not, I'll keep trying connecting direct.
Thanks once again for everyone's help.

---

### Post by alexfish on 2010-07-27
**nuno@nuno-desktop:~$ ls -al /dev/serial/by-id/usb***
lrwxrwxrwx 1  root root 13 2010-07-26 19:49  /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_12345678  90ABCDEF-if00-port0 -> ../../ttyUSB2

lrwxrwxrwx 1 root root  13 2010-07-26 19:49  /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_12345678  90ABCDEF-if02-port0 -> ../../ttyUSB1

lrwxrwxrwx 1 root root  13 2010-07-26 19:49  /dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_12345678  90ABCDEF-if03-port0 -> ../../ttyUSB0


hi

if read through the post #16 in the How To it will show that the above results show the device is incorrectly switched,if this happens Network Manager will not see the device

also in same post and the above shows how to test the port and try a connection testing each of the ports I suggest try port tttyUSB2 First
if the correct details are entered it may connect connect, statserial will only confirm that the modem has reset and is recognised by sending the init codes and the dial command to the correct port

can you supply your dialup details for you service provider from NM ,and i will try to list the commands to test the modem again

Any one wondering how this works, { the device is forced by sending AT commands directly to the device using Linux system commands IE: does not rely on other software managers Device Recognition }

                                  Post #**[16]("http://ubuntuforums.org/showpost.php?p=9483244&postcount=16")**
 

 [How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
 
regards

alexfish

---

### Post by alexfish on 2010-07-27
hi

try these from the terminal

open up first terminal and enter this code

Code:
tr -s "\n" < /dev/ttyUSB2

Open up second terminal and end enter these codes : monitor the respose in the first terminal

Reset the device
CODE:

echo -e "ATZ\r" > /dev/ttyUSB2

response in first terminal should =  OK

Send init1

echo -e "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0\r" > /dev/ttyUSB2

response in first terminal  OK

Set the APN
CODE:

echo -e "AT+CGDCONT=1,\"IP\" \"3Internet\"\r" > /dev/ttyUSB2

response in first terminal  should = OK

Dial Command
CODE:

echo -e "ATDT*99#\r" > /dev/ttyUSB2

The response in the first terminal may show something like  CONNECT


If you get a "NO CARRIER " message in the first terminal try the dial command 3 or 4 times if it fails Repeat from start trying  a different port

When you get a CONNECT message in the first terminal call the ppp Daemon

Code:
sudo pppd ttyUSB2 115200 nodetach defaultroute noipdefault noauth lock usepeerdns

If username and password required append the above with user < user> password <yourpassword>

example response:

[sudo] password for alexfish: <enter your login password for ubuntu >
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
PAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local IP address 10.158.21.15
remote IP address 10.64.64.64
primary DNS address 149.254.201.126
secondary DNS address 149.254.192.126

---

