---
title: "rogers rocket stick"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by brydong on 2009-12-20
I'm looking for ANY links, advice, help on getting a Rogers usb rocket stick for mobile broadband access working on karmic koala. I've tried adding a connection using all the default Rogers options but that doesn't get me anywhere.

thanks,
brydon

---

### Post by hansdown on 2009-12-20
Hi brydong.

I haven't tried these, but they may help.

[http://mlodecki.net/?p=55](http://mlodecki.net/?p=55)

[http://dan.cognitiveflatulence.org/2009/02/gprs-dial-up-networking-ubuntu-and-others/](http://dan.cognitiveflatulence.org/2009/02/gprs-dial-up-networking-ubuntu-and-others/)

---

### Post by brydong on 2009-12-20
I tried the latter link ([http://dan.cognitiveflatulence.org/2009/02/gprs-dial-up-networking-ubuntu-and-others/](http://dan.cognitiveflatulence.org/2009/02/gprs-dial-up-networking-ubuntu-and-others/)) and got as far as the detect modem in gnome-ppp. I can only get it to report no modem found.

---

### Post by pdc on 2009-12-20
looks like it is a ZTE MF636

[http://www.rogers.com/web/link/wirelessBuyFlow?forwardTo=PhoneThenPlan&productType=normal&productId_Detailed=MF636REDR](http://www.rogers.com/web/link/wirelessBuyFlow?forwardTo=PhoneThenPlan&productType=normal&productId_Detailed=MF636REDR)

no one is really too sure how steady Ubuntu 9.10 really is with mobile broadband;using say Network Manager

if you search on the MF636 in Ubuntu, there were various posts describing how to get it going;

eg 

[http://ubuntuforums.org/showthread.php?t=1065934&highlight=ZTE+MF636](http://ubuntuforums.org/showthread.php?t=1065934&highlight=ZTE+MF636)

and here describing the similar MF626

[http://ubuntuforums.org/showthread.php?t=1147685&highlight=ZTE+MF636](http://ubuntuforums.org/showthread.php?t=1147685&highlight=ZTE+MF636)

I got one of these working on Mandriva2010 (gnome) and Ubuntu 9.10 using wvdial;

so I downloaded wvdial (eg sudo apt-get install wvdial)

[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271)

the wvdial.conf file was 

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","whateveryourAPNsettingsare"
Phone = *99#
Stupid Mode = 1

when I plug the mode in, it shows an icon on the desktop; I haven't got round to installing usb_modeswitch; I just right click on the icon, and select "eject" and then run 

sudo wvdial 

in ubuntu

---

### Post by Rhubarb on 2009-12-20
I've got to say that wvdial is very good to use, better than network manager (especially in karmic), because it works most of the time, and it seems to be able to download faster aswell.

pdc is spot on in recommending wvdial :)

my /etc/wvdial.conf
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Modem = /dev/ttyUSB0
Baud = 115200

[Dialer three]
Phone = *99#
Username = a
Password = a
Stupid Mode = 1
Baud = 7372800
Init3 = AT+CGDCONT=1,"IP","3services"
```

It's much the same as pdc's wvdial.conf, with a few differences to note:
[LIST]
[*]the baud rate on mine is much higher, and doesn't cause any problems with my Huawei E160g usb dongle
[*]It uses /dev/ttyUSB0 rather than ttyUSB2
[*]3services should be replaced to whatever your Access Point Name is
[*]For the service I'm currently using, a username and password is not required.
[*]'three' is just the provider for the service I use - you can use any name here
[/LIST]

To connect, simply type in:
```
sudo wvdial three
```

---

### Post by pdc on 2009-12-21
pleased to hear this worked for you; I used 3 in Oz a couple of months ago; using a Huawei 160 on easy peasy 1.1 and network manager; it was a bit unsteady; it was northern NSW; 

how did you measure baud rate? 
how did you pick ttyUSB0 ?

My script was copied for another WV script: hence my baud rate etc!

Maybe I edit it; or maybe the modem does its own thing anyway;

good to hear wvdial works for you; where you seemed to find ?? 9.10 was a bit unsteady with NM ???

---

### Post by Rhubarb on 2009-12-22
> **pdc said:**
> how did you measure baud rate?
The baud rate is simply the speed at which your computer talks with the 3G modem.  Unless you set the baud rate less than your maximum throughput from your 3G internet, having a baud rate that's too high has no effect on internet speed performance.
I reached the value of 7372800 because:
[LIST]
[*]It's a multiple of 115200 - which is a typical speed that most (old) serial devices communicate at
[*]It's faster than my maximum actual internet connection speed on 3G
[*]It works
[/LIST]

> **pdc said:**
> how did you pick ttyUSB0 ?
It's the first serial port that linux gives me when I plug the 3G usb modem in
It can be found thus:
```
tail -f /var/log/messages
```
Then plug in your 3G modem, and see what /dev/ttyUSBx it gives you.  Usually the last /dev/ttyUSBx is unusable as it's just there to configure and access some random stuff on the unit.  But the first /dev/ttyUSBx is the one that you want.
eg: "usb 1-4: GSM modem (1-port)converter now attached to ttyUSB0"
Press **Ctrl** + **c** to exit tail.

> **pdc said:**
> good to hear wvdial works for you; where you seemed to find ?? 9.10 was a bit unsteady with NM ???

9.10's network manager only worked successfully around 1/7 of the time for me. - When it did work, my maximum download speed was 160kB/s

Now using wvdial, I get atleast 250kB/s when downloading stuff from the internet.

All though very occasionally (around 1 in 10, maybe more) my wvdial doesn't work as ubuntu didn't detect /dev/ttyUSB0.
- easily solved by pulling it out and putting the 3G modem back in again.

I've also found with recent updates to 9.04 the network manager ceases to work with my 3G modem too (wvdial works fine here too).

Also, if using wvdial, note that the empathy IM client won't work.
This is easily fixed:
[[SOLVED] empathy/pidgin and other programs dont detect wvdial ..]("http://ubuntuforums.org/showthread.php?p=8537691#post8537691")

... And finally, I'd worked all this out by looking at the Arch Linux forums, where they've got some info about wvdial.
- I had installed and used Arch with wvdial around 4 months ago.  Everything worked beautifully, and I'm rather impressed by wmii (tiling window manager).  But an update managed to take down X, and changed my keyboard layout to qwerty (I'm a dvorak typist) - which was the last straw for me.  I'll probably go back to using Arch soonish again :)

---

### Post by brydong on 2009-12-22
I'll try some of these this evening, thanks! For those who have tried this, do you need an actual username and password as I have nothing like that.

---

### Post by Rhubarb on 2009-12-22
> **brydong said:**
> ... do you need an actual username and password as I have nothing like that.

No username or password is required (well, atleast with "3" in Australia anway).
As *I think* wvdial requires a username and password, I just give it "a" for both of these fields.  And it works fine for me.

---

### Post by brydong on 2009-12-22
The actual device I'm working with is a Sony Ericcson MD400G

---

### Post by brydong on 2009-12-22
I used the wvdial.conf taken from [here]("http://www.timetraveller.org/rogers/"):

[Dialer Defaults]
Dial Command = ATDT
Stupid Mode = 1

[Dialer reset]
Modem = /dev/ttyUSB0
Init1 = AT

[Dialer rogers]
Phone = *99***1#
Username = XXXXXXXXXXXXXXX
Password = XXXX
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Init5 =AT+CGDCONT=1,"IP","internet.com","",0,0;
~                                                

I then eject the usb drive through nautilus and run "sudo wvdial rogers" which only results in:

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

I'm still unsure if I need to actually fill in the username and password as I'm literally using the exact conf file above.

---

### Post by Rhubarb on 2009-12-22
> **brydong said:**
> I used the wvdial.conf taken from [here]("http://www.timetraveller.org/rogers/"):

...

I'm still unsure if I need to actually fill in the username and password as I'm literally using the exact conf file above.

Well that could be the problem.
The URL that you provided (above) says that,
> The Username is a 12 digit number found under the bar code next to the SIM on the credit card sized card you get from Rogers when you sign up. The default password for the device is 1234.

Hopefully that's the problem and even more importantly, hopefully it works for you!

---

### Post by brydong on 2009-12-22
Well I'm worried then because I don't have the credit card sized card they refer to. I don't believe they ever gave it to me, they likely just tossed it out.

---

### Post by pdc on 2009-12-22
plug in the modem;

when it shows an icon on the desktop;

type

> lsusb in a terminal

right-click on the desktop icon; the icon may well disappear; and a window opens, showing a storage of 127MB or somesuch; (that's what mine does); close the window;

we hope by doing the above to "flip" the device; initially linux is likely seeing it as a CD-ROM device; by "flipping" you unmask to linux that it has a modem function as well, and linux can now address it as a modem

again type

> lsusb

the Vendor ID should stay the same, but the Product ID should change:

then type 

> ls /dev/ttyUSB* in the terminal

tell us what each of the results are

(my wvdial script uses ttyUSB2)

The script you followed had the vendor ID: product ID of vendor=0x1410 product=0x4400 as the device then was a Novatel Ovation MC950D; I got the sense that they were now using a ZTE MF636 but we can find out from your lsusb enquiries

---

### Post by brydong on 2009-12-22
thanks for the reply...

First, I feel like there was a piece missing from "right-click on the desktop icon; the icon may well disappear; and a window opens, showing a storage of 127MB or somesuch; (that's what mine does); close the window;"

Were you wanting me to right click on the desktop icon and select something like eject?

The relate output for lsusb is:

Bus 001 Device 018: ID 0fce:d103 Sony Ericsson Mobile Communications

There are no ttyusb devices showing up:

ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

---

### Post by pdc on 2009-12-22
Hi rhubarb;

thanks for your clarifications in post #7; very helpful;

will see about editing my wvdial script

---

### Post by brydong on 2009-12-24
I think I'm getting closer....

Using usb_modeswitch, the network manager can now see the modem.

sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

I then create the connection using network manager, selecting Rogers etc. It then appears as an available network, however, when I select it, it fails to connect.

Some forums have mentioned that username/password does nothing, others mention that you need the SIM card frame in order to get these details off that. Is this the piece I'm missing? If so, I wonder if I could get this by phoning Rogers ?

---

### Post by Craigwell on 2010-01-26
I had the md400g working with 9.04, using usb_modeswitch. 

The string I used in terminal: 

 sudo usb_modeswitch -v 0fce -p d103 -O

Then network manager in 9.04 would see the device and it would connect. 

In network connections, make sure you have the following settings:

number: *99#
user: wapuser1
pass: wap

under ipv4 settings, I had the following under DNS servers. 

207.181.101.4, 207.181.101.5

This worked fine for me in 9.04, (without GPS function unfortunately) but I cannot get it work with 9.10 Karmic. 

Everything seems fine until I select Rogers from network manager. It tries to connect for a split second before I get the "GSM network disconnected" tag on the screen.

Let me know how you make out. I am going to try the other network app another poster discussed in the thread.

---

### Post by brydong on 2010-01-28
I had to use wvdial with the config file located here [http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html](http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html)

I could never get network manager to work, always getting the results you mentioned.

---

### Post by mrpenguin on 2010-02-08
None of these posts has helped me to make my Rogers Rocket stick to work .. anybody with a better suggestion ?

---

### Post by brydong on 2010-02-08
All I can say is I followed the directions on this blog post, right down to using the exact conf file and it got me running, [http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html](http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html)

Where are you at in the process?? What specific issues are you having?

---

### Post by mrpenguin on 2010-02-08
I have tried all different ways but I keep on getting stuck here ..

> sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: SEMC
 Product String: MMC Flash Card
Revision String:    0
-------------------------

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################
 After 20 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo gedit /etc/wvdial.conf
jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0fce -p d103 -O

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 005 on bus 002 ...
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo gedit /etc/wvdial.conf
jaques@jaques-laptop:~$ sudo wvdial
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
jaques@jaques-laptop:~$ 



---

### Post by mrpenguin on 2010-02-08
I think I might have got it working ??
I am on wifi so I need to fugure out how to switch it off first

> jaques@jaques-laptop:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&0[1d]l:}1X~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&0[1d]l:]5~
--> PPP negotiation detected.
--> Starting pppd at Mon Feb  8 10:42:06 2010
--> Pid of pppd: 3081
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> local  IP address 10.141.178.146
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> primary   DNS address 64.71.255.198
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> secondary DNS address 64.71.255.253
--> pppd: &#65533;&#65533;&#65533; &#1585;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 



---

### Post by mrpenguin on 2010-02-08
> **brydong said:**
> All I can say is I followed the directions on this blog post, right down to using the exact conf file and it got me running, [http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html](http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html)

Where are you at in the process?? What specific issues are you having?


Thanks a million !!!!
Looks like I disconnected from the wifi and i am still on the internet, I can see a blue light flashing on the rogers stick ... but it seems very slow, way slower than what I have on windows ?
Also what do I do if I want to get on it again ... redo all the commands or is there just one that will make it dial up next time ?
also how do i disconnect the rogers stick now from the internet ?

---

### Post by mrpenguin on 2010-02-08
well I just redid everything I did before but this time its not working ??

> jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 007 on bus 002 ...
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo gedit /etc/wvdial.conf
jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0fce -p d103 -O

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 007 on bus 002 ...
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such device
--> Cannot open /dev/ttyACM0: No such device
--> Cannot open /dev/ttyACM0: No such device
jaques@jaques-laptop:~$ 


---

### Post by brydong on 2010-02-08
I simply plugin my stick and run a 2 line shell script I have in sudo, which I'll attach to this.

---

### Post by mrpenguin on 2010-02-08
Something else must be wrong with mine ... earlier steps needs to be done ..

> jaques@jaques-laptop:~$ usb_modeswitch -v 0x0fce -p 0xd103 -O 1

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 000 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry

Device description data (identification)
-------------------------
Error: could not get description string "manufacturer"
Manufacturer: 
Error: could not get description string "product"
     Product: 
Error: could not get description string "serial number"
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
Error: sending Sony control message failed (error -1). Aborting.


---

### Post by mrpenguin on 2010-02-09
bump

---

### Post by mrpenguin on 2010-02-13
Ok ... It is working for sure

This is what I did to connect to the internet using my Rogers Rocket stick :

> jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: SEMC
 Product String: MMC Flash Card
Revision String:    0
-------------------------

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################
 After 20 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo gedit /etc/wvdial.conf
jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0fce -p d103 -O

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 002 ...
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}"=g[04]Y3~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}"=g[04][15]^~
--> PPP negotiation detected.
--> Starting pppd at Sat Feb 13 12:34:49 2010
--> Pid of pppd: 2341
--> Using interface ppp0
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> local  IP address 10.141.227.107
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> remote IP address 10.64.64.64
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> primary   DNS address 64.71.255.198
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 
--> secondary DNS address 64.71.255.253
--> pppd: &#65533;xl &#1537;l [18]yl hyl &#65533;yl &#65533;yl 



My question is ... how do I disconnect my Rogers device now that it is active ?
Also is there an easier way to connect the next time I want to go on the internet or do I need to do all of what I did every single time ??

Please help thanks

---

### Post by mrpenguin on 2010-02-14
also it seems when I loose my connection then the only way to get my rocket stick to work again is to restart my computer and then to redo everything i did above again ???

---

### Post by mrpenguin on 2010-02-17
bump

---

### Post by Craigwell on 2010-02-25
This really has become a great thread. 

I have had nothing but difficulty with this device since September 2009, it was better for me in jaunty, when all I had to do was use the usb_modeswitch command and then network manager would do the job after that. 

Since Karmic, network manager has been useless, and I believe it's due to the init commands it is (or isn't) using. 

I haven't resolved this yet, nor have I quite gotten the unit to work with gnome-ppd. Seems like it uses wvdial, but not the same wvdial.conf settings that I can use manually in terminal with wvdial.

Wvdial and the no-pin rogers conf options, and wvdial run from terminal are all I've gotten to work --- after using usb-modeswitch. 

There was another wvdial.conf file out there I seen for a different device that actually worked very well, enabled gps etc, when I find it again i will post, as i believe the content helps our cause.

---

### Post by Craigwell on 2010-03-14
here is the working wvdial.conf file settings:

Dialer Defaults]
New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem

#[Dialer PIN]
#Init1 = AT+CPIN=

[Dialer signal]
Modem = /dev/ttyACM1
Init1 = AT+CSQ
Init2 = AT+COPS?

[Dialer gps]
Modem = /dev/ttyACM0
Init1 = AT*E2GPSCTL=1,2,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Phone = *99***1#
Password = wap
Username = wapuser1

---

### Post by pdc on 2010-03-15
mrpenguin seemed to want to know how to turn off wvdial when used to activate a usb_stick

what works for me is 

> control-c

 in a terminal

---

### Post by seanc7 on 2012-01-28
Not trying to resurrect a dead thread, just wanted to update saying the ZTE 3G sticks that Rogers used to sell back in 2009 now work in version 11.10 without any effort needed to get it going. :)

---

