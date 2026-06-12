---
title: "get my vodafone prepaid working on ubuntu 9.04"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by starcraftmaster on 2009-08-14
hey guys
i need to know how i would get my vodafone prepaid moble broadband internet working on  ubuntu 9.04
since am petty new i will need steps

the wireless modem is usb

---

### Post by starcraftmaster on 2009-08-15
any one ?:(

---

### Post by starcraftmaster on 2009-08-19
well i guess no one knows a answer to this:(

---

### Post by GeorgeVita on 2009-08-19
Hi **starcraftmaster**, most times 'no answer' means 'I do not know' or "I did not see your thread!".

To help us ... help you, we need to know exact model of modem (manufacturer, type) see sticker at bottom side and also any results you have after attaching this modem to your computer running Ubuntu 9.04 (any wizard, message appeared).

Some info could come from the terminal commands: ```
lsusb
``````
ls /dev/ttyU*
```
(to open a terminal window: Applications > Accessories > Terminal)

Post here any data ...

Regards,
George

---

### Post by starcraftmaster on 2009-08-20
> **GeorgeVita said:**
> Hi **starcraftmaster**, most times 'no answer' means 'I do not know' or "I did not see your thread!".

To help us ... help you, we need to know exact model of modem (manufacturer, type) see sticker at bottom side and also any results you have after attaching this modem to your computer running Ubuntu 9.04 (any wizard, message appeared).

Some info could come from the terminal commands: ```
lsusb
``````
ls /dev/ttyU*
```(to open a terminal window: Applications > Accessories > Terminal)

Post here any data ...

Regards,
George

thnaks george
well here is the back of the modem
vodafone mobile conect
model: K3520
HSDPA USB Stick

Nothing appears when connecting the modem to the computer

heres the terminal data

daniel@PackardBell:~$ lsusb
Bus 001 Device 007: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 005: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 001 Device 004: ID 1631:5000 Good Way Technology 
Bus 001 Device 003: ID 0416:5518 Winbond Electronics Corp. 4-Port Hub
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daniel@PackardBell:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1


the way am connecting to the internet now is by a usb Modem(SurfBoard SB5101 Cable Modem) with optus(its not wireless)
this is just a basic modem

---

### Post by garryknight on 2009-08-20
Try here:
[http://www.betavine.net/bvportal/resources/datacards](http://www.betavine.net/bvportal/resources/datacards)

---

### Post by scottuss on 2009-08-20
When you insert the USB modem into the computer, it is being detected, as illustrated by the output of lsusb.

What you need to do now is click the icon in the top right hand corner of your screen, where you see the Network icon (it will look different if you are on wireless / wired internet)

Click on it and you should get a drop-down list of available networks. Your USB modem should have created an entry on there, if it is set up correctly.


Let us know how you get on

---

### Post by starcraftmaster on 2009-08-21
> **scottuss said:**
> When you insert the USB modem into the computer, it is being detected, as illustrated by the output of lsusb.

What you need to do now is click the icon in the top right hand corner of your screen, where you see the Network icon (it will look different if you are on wireless / wired internet)

Click on it and you should get a drop-down list of available networks. Your USB modem should have created an entry on there, if it is set up correctly.


Let us know how you get on



ok
how do i set it up ?
and i will try the betavine when i get time
thanks for the help so far

---

### Post by GeorgeVita on 2009-08-21
> **starcraftmaster said:**
> ...
how do i set it up ?

Hi **starcraftmaster**,
as shown from your lsusb and ls /dev/ttyU* all are OK.

Right click Network Manager icon, Edit Connections, Mobile Broadband, click to any existing and delete it. Then ADD a new connection, choose appropriate country, provider, prepaid account (if more than one selection).

Edit connection again to see parameters: APN, username, password
and check them with your provider (call them).

Ex. UK (britain) Vodafone prepaid has:
APN=pp.vodafone.co.uk
User=wap
Pass=wap
(according to the later version of network manager)

Finally try to connect with left click on network manager icon, and then on the providers name.

Regards,
George

---

### Post by scottuss on 2009-08-21
> **GeorgeVita said:**
> Hi **starcraftmaster**,
as shown from your lsusb and ls /dev/ttyU* all are OK.

Right click Network Manager icon, Edit Connections, Mobile Broadband, click to any existing and delete it. Then ADD a new connection, choose appropriate country, provider, prepaid account (if more than one selection).

Edit connection again to see parameters: APN, username, password
and check them with your provider (call them).

Ex. UK (britain) Vodafone prepaid has:
APN=pp.vodafone.co.uk
User=wap
Pass=wap
(according to the later version of network manager)

Finally try to connect with left click on network manager icon, and then on the providers name.

Regardss,
George

You took the words right out of my mouth :)

---

### Post by GeorgeVita on 2009-08-21
> **scottuss said:**
> You took the words right out of my mouth :)

Real: I am always happy when **more** people want to help!
Joke: Ha ha, you still have the double 's' at my Regardss!
Problem: when you see double letters the poster may using an EeePC (mine=1000H) kbrd is bouncing

Regards,
George

---

### Post by starcraftmaster on 2009-09-01
my brother run out of prepaid money for the modem
he probably never buy more lol so thanks for all the help you guys

---

### Post by tomreid on 2009-09-03
Hi

I'm arriving in the UK on Monday, was going to buy one of these prepaid USB sticks from Vodafone. 

Can anyone let me know if the procedures outlined below worked?

I'll have a mac with me too, but also a handy little Dell Mini 10V running 8.10, so it'd be nice to get this to work with the netbook too.

cheers

---

### Post by scottuss on 2009-09-04
> **tomreid said:**
> Hi

I'm arriving in the UK on Monday, was going to buy one of these prepaid USB sticks from Vodafone. 

Can anyone let me know if the procedures outlined below worked?

I'll have a mac with me too, but also a handy little Dell Mini 10V running 8.10, so it'd be nice to get this to work with the netbook too.

cheers

Yes, it should work without any issue. I have used a Vodafone prepay USB with 8.10 and 9.04. Any problems, post on here and people will be more than happy to help.

The reason, I suspect, his didn't work was as he said afterwards, there was no credit left on the account.

---

### Post by pi4r0n on 2009-09-04
Hello [starcraftmaster]("http://ubuntuforums.org/member.php?u=866410")

Not sure if this is what you are looking for but worth to have a go. It does work for me

In order to do it please follow steps provided by [StevenHarper]("http://ubuntuforums.org/member.php?u=167248") in this post [**Using mobile for internet**]("http://ubuntuforums.org/showthread.php?t=935203")

Cheers

pi4r0n

---

### Post by florus on 2009-09-04
I have just bought a Vodafone 'Top up and Go' stick and it installed in 9.04 far more quickly and easily than it did in Vista. Another nail in the coffin for Vista. Just TomTom and Mapyx Quo to sort out now.:(
The only problem might be checking the remaining balance; as far as I can see you would need Windows for that.

---

### Post by pi4r0n on 2009-09-04
**florus**

To keep track of your usage just install *[**vnstat**]("http://humdi.net/vnstat/") *    

    >  sudo apt-get install vnstat and then select your device
 
   >   sudo vnstat -i deviceCheers

Just top up your mob check your broadband limit and then monitor it with this software

pi4r0n

---

### Post by florus on 2009-09-04
Thanks for that help. I was expecting this to be fairly complicated, but in reality it took me all of 30 seconds from taking the stick out of its box to being connected and checking my emails. All I had to do was select the correct phone network from the dropdown list.:D

---

### Post by tomreid on 2009-09-05
Thanks guys, when I get to the UK I will try it out and see it it works. Knowing me I will be fighting jetlag and trying to handle technical stuff at the same time! I hope it's better than my disaster when I tried to install wireless network in Paris with all the instructions written in French last time I arrived in Europe!

---

### Post by tomreid on 2009-09-09
Hi all, well nothing is as easy as it seems and I can't get the USB Broadband modem to work with my Ubuntu 8.10 Dell Mini 10V netbook. 

I suspect this is a driver problem. When I run "lsusb" the device is not listed. It is a Huawei K3565. 

I have been looking at Betavine as they have a wide range of drivers and software for mobile devices on Linux but there seems to be a confusing amount of versions of the software and when I tried a few of the ".deb" packages, the Ubuntu package installer reported various different dependency errors when I tried to open the .deb package.

I will try to to read on, but when I tried connecting through Network Manager and selected all the vodafone pre-sets, the network manager seemed to be trying to connect, but never did. I suspect it is because the netbook hasn't registered the USB Modem is there due to lack of a driver.

Any help grately appreciated.

cheers

---

### Post by GeorgeVita on 2009-09-09
Hi **tomreid**, let's try to see it at lsusb doing some basic tests:

Boot without the modem, **wait** for the system to load, open a terminal window: ```
sudo dmesg -c
```Attach your modem, **wait** 15 seconds, check from terminal: ```
dmesg
``` ```
lsusb
```Post here terminal output from 2nd dmesg and lsusb commands.

Regards,
George

---

### Post by tomreid on 2009-09-09
Update:

I continued to experiment and discovered that Betavine have a package they say is for the Dell Mini 9. My Dell is a Mini 10V, but I took a chance and downloaded it. It installed fine. It is a version of Vodafone Mobile Connect, similar, but actually a bit fuller featured, than the one I'm using with my mac.

It even found the USB modem. All looked OK, I created a profile and put in the settings that were shown earlier in this post (also see screenshot below).

Everything looked OK, but it won't connect. Errors out after about 5 seconds with an error that says something like "it tried to connect 3 times and has now given up".

Very frustrating, so near yet so far.

---

### Post by GeorgeVita on 2009-09-09
Some checks:

- is your SIM enabled (some times they need an SMS, a call or a 'web action')
- remove SIM PIN check (using a phone)
- ask/check APN, user/password as sometimes is different for prepaid
- try to connect when a blue (3G) led is on

Good luck!
G

---

### Post by tomreid on 2009-09-09
Hi

Sorry, forgot to attach my screenshot before. 

The USB Modem is actually working fine on a mac, so the service is not an issue. I'm sure it;s something in the Ubuntu set up.

cheers

---

### Post by GeorgeVita on 2009-09-09
Check APN and authentication mode CHAP (?), compare with the working PC.
Vodafone UK has also "topup and go" with APN=pp.internet

If settings are OK, you must find any 'log' file from VMC.
I would also try wvdial as it shows some 'error messages' to terminal but ... you are so close to make it!

G

---

### Post by florus on 2009-09-09
Upgrading to 9.04 may be your simplest option.

---

### Post by tomreid on 2009-09-10
Hi

Thought of that, but this little Dell was supplied by them with 8.04 and it integrates so nicely with the machine that I didn't want to break that by upgrading the version. believe 9.04 breaks the integration with the build in mic.

Actually, due to jet lag I was wide awake at 4am and decided to delete the profile I made with the settings in this post and take the default settings in the profile that came with this Linux version of Vodafone Mobile connect, and it worked! Amazing. Linux support for Vodafone devices can only get better, but there is actually quite a lot of compatible software out there on betavine, it just needs better explained and organised.

cheers

---

### Post by tanuii on 2009-09-10
Hi folks

And what about if the 3G modem is integrated in the laptop?
What should I do? i tried to create a new WAN conection but I dont know what steps i must follow.
I dont know even if Ubuntu recognizes my 3G modem
Anybody for help?
Thanks a lot

---

### Post by jimmers on 2009-09-14
Hi TomReid,
I too have a Huawei k3565, if you have'nt resolved your problem try the following:-
Have a look at GaryKnight's post, and down load the following files and then install in this order:-
ozerocdoff_0.4.2_i386 deb
usb-modeswitch_0.9.7_i386 deb
vodafone-mobile-connect_svn2009615_all deb

Hope this helps

Jimmers

---

### Post by ubseamus on 2010-03-07
Having the same problem.

Running ubuntu 9.04 64bit

Trying to set up a Vodafone Top-up and go.

Have installed:

usb-modeswitch_0.9.7_amd64.deb
ozerocdoff_0.4_amd64.deb
vodafone-mobile-connect_svn20090615_all.deb

from betavin.

I have setup profiles using the VMC and the NM & tried a number of different combinations of apn [pp.internet, pp.vodafone.co.uk], username/password [web, wap, vodacom]

using:
user/password: web/web
apn: pp.vodafone.co.uk

seems to be getting somewhere. but i get screen prompting for a password. 

again I have tried web/wap/vodacom/my root password/ and leaving it blank [as suggested in another post]

Please help.

I've been at this for over 2 days now, & I have now other net connection. had to go to shopping centre to get wifi acces.....

I need help...

---

### Post by ubseamus on 2010-03-07
Attached is the mysterious password screen...

---

### Post by alexfish on 2010-03-08
> **ubseamus said:**
> Attached is the mysterious password screen...

Hi

Use the Network Manager connection First

If it is vodafone top up and go then see below screen shot . there is no user name or password required.

No sure if VMC works with Ubuntu 9.10 or above please check the VMC forum site / also for help on VMC

regards

alexfish

---

### Post by ubseamus on 2010-03-09
Thanks but no luck...

After making the suggested change I get the "Disconnected" message below.

My NM does look a bit different than the screen you posted. Has it been updated in 9.10, I am running 9.04.

If I did not mention it before, I am in the UK, so I think "apn: pp.vodafone.co.uk" is correct. 

I tried this with user/pword empty, and the result is the same...

Struggling here, any help is much appreciated.

---

### Post by ubseamus on 2010-03-09
Any suggestions for "PPP Settings" etc. ?

---

### Post by alexfish on 2010-03-09
> **ubseamus said:**
> Any suggestions for "PPP Settings" etc. ?

hi

This device should configure with the network manager ( as on other post you mention K3565)

Please check details with your service provider then enter the information required by the network manager ( wizard )

IE:

1 country

2. service provider

3. payment plan

4. user name and password if applicable

5. pin code if activated 

6. puck code {maybe required if the sim card is blocked }

also ensure this is the only modem attached to your system and disable all other network work connections.

if the wrong info has been entered previously ( user name and passwords )  then maybe the sim card is blocked, this will have to be resolved with your service provider

---

### Post by beercz on 2010-10-14
Hi guys

Apologies for regurgitating an old thread, but this thread is particularly relevant to my new problem.

I have a Vodafone USB Modem, Model HSDPA USB Stick K3520-Z

It worked very well under Ubuntu 10.04.

I have recently upgraded to 10.10 and now it is not even recognised.

lsusb doesn't list it.

I have tried another (generic) usb stick and it works fine.

Any ideas anyone?

Thanks in advance.

---

### Post by alexfish on 2010-10-14
Hi

can try from the terminal

Code:
[COLOR=Blue]
usb-devices[/COLOR]

look for the part which shows the device and post only that part

Added


Can you list which software and connection managers you have on the system

---

### Post by beercz on 2010-10-14
> **alexfish said:**
> Hi

can try from the terminal

Code:
[COLOR=Blue]
usb-devices[/COLOR]

look for the part which shows the device and post only that part

Added


Can you list which software and connection managers you have on the system
Hi alexfish

Thanks for responding.

Here's the relevant output from usb-devices:
> T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2000 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=USB ZTE Storage
S:  SerialNumber=P671M8VDF_MS
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)


I don't use any connection managers apart from the built in network manager.

Also, the device has a micro SD card installed, and prior to 10.10 when I inserted the device it was recognised (correctly) as a usb flash drive.

I have tried on two ubuntu 10.10 computers with the same result.  It used to work fine on both computers prior to 10.10.

Thanks again.

---

### Post by alexfish on 2010-10-14
hi

need to see what is happening in the syslog

post results
from the terminal 

Code:

grep ZTE /var/log/syslog

---

### Post by beercz on 2010-10-14
> **alexfish said:**
> hi

need to see what is happening in the syslog

post results
from the terminal 

Code:

grep ZTE /var/log/syslog
Here we go:
> ian@ryan:~$ grep ZTE /var/log/syslog
Oct 14 16:41:34 ryan modem-manager: Loaded plugin ZTE
Oct 14 17:25:23 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 17:32:16 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 22:07:20 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 22:11:11 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)

Thanks again

---

### Post by alexfish on 2010-10-14
Hi

can try this 

Code:

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules

find the lines 

# ZTE devices
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="usb_modeswitch '%b/%k'"

place a # on line to look like

# ZTE devices
#ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="usb_modeswitch '%b/%k'"

save the file

unplug the device and reconnect

note any changes from the syslog or from the command "usb-devices"

---

### Post by beercz on 2010-10-14
> **alexfish said:**
> Hi

can try this 

Code:

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules

find the lines 

# ZTE devices
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="usb_modeswitch '%b/%k'"

place a # on line to look like

# ZTE devices
#ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="usb_modeswitch '%b/%k'"

save the file

unplug the device and reconnect

note any changes from the syslog or from the command "usb-devices"
Hi Alexfish

I've edited the file as instructed, inserted the device.

Here's the relevant syslog output:

> ian@ryan:~$ grep ZTE /var/log/syslog
Oct 14 16:41:34 ryan modem-manager: Loaded plugin ZTE
Oct 14 17:25:23 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 17:32:16 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 22:07:20 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 22:11:11 ryan usb_modeswitch: switching 19d2:2000 (Qualcomm, Incorporated: USB ZTE Storage)
Oct 14 23:30:33 ryan modem-manager: Loaded plugin ZTE
Oct 14 23:49:29 ryan kernel: [ 1176.033047] scsi 4:0:0:0: CD-ROM            ZTE Corp USB Storage      2.31 PQ: 0 ANSI: 2

And here's the relevant output from usb-devices:

> T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2000 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=USB ZTE Storage
S:  SerialNumber=P671M8VDF_MS
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
Thanks once again.

---

### Post by alexfish on 2010-10-14
one step further

from the terminal

Code:

usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000

see what happens

note the messages of usb_modeswitch

---

### Post by beercz on 2010-10-14
> **alexfish said:**
> one step further

from the terminal

Code:

usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000

see what happens
This is what happens:
> ian@ryan:~$ usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000
Warning: TargetProductList overrides TargetProduct!

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 000 on bus 004 ...
Using endpoints 0x09 (out) and 0x89 (in)
Using endpoints 0x09 (out) and 0x89 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
 Could not claim interface (error -1). Skipping message sending

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Original device can't be accessed anymore. Good.
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 No new devices in target mode or class found

Mode switch has failed. Bye.


---

### Post by alexfish on 2010-10-14
think found the device

Code:

sudo gedit /etc/usb_modeswitch.d/19d2:2000

replace contents with

########################################################
# ZTE K3520-Z
#
# Contributor: Paul McDermott

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0055

MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"

NeedResponse=1
#####################################################################
Remember to remove spaces in the numbers in the file before saving

then try the 

Code:

usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000

ADDED removes the[COLOR=Red] [COLOR=Black]**;**[/COLOR][/COLOR] from file

or can try : remember to remove spaces in message content, if using copy and paste from here

usb_modeswitch -v 19d2 -p 2000 -M "5553424312345678000000000000061e0 00000000000000000000000000000"
usb_modeswitch -v 19d2 -p 2000 -M "5553424312345679000000000000061b 000000020000000000000000000000"


Also been thinking : noticed the modem-manager calling up the ZTE plugin , any prompt  requesting a pin code: or other info
or any VM ware installed

---

### Post by beercz on 2010-10-18
> **alexfish said:**
> think found the device

Code:

sudo gedit /etc/usb_modeswitch.d/19d2:2000

replace contents with

########################################################
# ZTE K3520-Z
#
# Contributor: Paul McDermott

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0055

MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"

NeedResponse=1
#####################################################################
Remember to remove spaces in the numbers in the file before saving

then try the 

Code:

usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000

ADDED removes the[COLOR=Red] [COLOR=Black]**;**[/COLOR][/COLOR] from file

or can try : remember to remove spaces in message content, if using copy and paste from here

usb_modeswitch -v 19d2 -p 2000 -M "5553424312345678000000000000061e0 00000000000000000000000000000"
usb_modeswitch -v 19d2 -p 2000 -M "5553424312345679000000000000061b 000000020000000000000000000000"


Also been thinking : noticed the modem-manager calling up the ZTE plugin , any prompt  requesting a pin code: or other info
or any VM ware installed
Hi Alexfish

Apologies it's taken a couple of days to come back.

I have done the above (edited the file  /etc/usb_modeswitch.d/19d2:2000 and removed the spaces in the numbers as instructed), then I ran usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000 and here's the output:

> Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 000 on bus 005 ...
Using endpoints 0x09 (out) and 0x89 (in)
Using endpoints 0x09 (out) and 0x89 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.
As far as the modem manager is concerned, I can only think of the network configuration tool where I can edit connections.  In 10.04 I was able to edit my USB modem connection with no problem and in 10.10 the USB connection configuration still appears when I right-click on the icon and choose Edit Connections->Mobile Broadband.

I don't have a pin, never have, and I haven't changed any of the connection settings.

The connection does not appear in the list of connections in the connection manager when I plug the device in.

Also, under 10.04, when I plugged the device in I got a icon on my desktop showing a USB flash drive (the device has a 4Gb micro-SD card in it), and it also appears under Places and Places->Computer.  In 10.10 this no longer happens.

Thanks again for your help.

---

### Post by alexfish on 2010-10-18
hi

this is what i am thinking

Some ZTE devices do not require usb_modeswitch

as to what is happening with the Modem-Manager plugin and the usb_modeswitch , and possibly other udev rules
is only an assumtion that the system is getting confused

since the usb-modeswitch is not working with the -C action
you could try as suggested with the -v , -p , -M : ie

Code:
usb_modeswitch -v 19d2 -p 2000 -M "5553424312345678000000000000061e0 00000000000000000000000000000"

Code:
usb_modeswitch -v 19d2 -p 2000 -M "5553424312345679000000000000061b 000000020000000000000000000000"

see what happens, remember to remove spaces in the message content , after the -M   and only one command at a time 

but from what i am reading the system may be only seeing the flash drive(don't know yet)

could try removing the flash drive see what happens, yet if this works , still left with flash drive problem


So since the usb_modeswitch is not working on the system

could try un-installing or disable the usb_modeswitch

this will narrow the field a bit

---

### Post by beercz on 2010-10-22
Hi Alexfish

From reading other threads on this issue (for example [http://ubuntuforums.org/showthread.php?t=1602199](http://ubuntuforums.org/showthread.php?t=1602199)) it seems to be a problem with modeswitch,

To save me time, I have reverted back to 10.04 for the time being.  When I am less busy I will try again.

Thanks for all your help, much appreciated.

---

