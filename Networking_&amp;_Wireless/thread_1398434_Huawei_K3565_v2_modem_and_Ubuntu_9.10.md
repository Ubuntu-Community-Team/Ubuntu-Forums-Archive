---
title: "Huawei K3565 v2 modem and Ubuntu 9.10?"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by Nightstrike2009 on 2010-02-04
Hiya everyone

I have a **Huawei K3565 v2 (Vodafone Mobile Connect) 3g modem** and was just enquiring if anyone knew a **SIMPLE** way of getting it to work with Ubuntu 9.10.

(Or if it now works in Ubuntu 10.4, because if it doesn't work in 10.4LTS I am off to another linux distro FOR GOOD, no internet connection is a MAJOR BUG in an Linux OS):-(

The purpose of this thread is to get this type of modem working in Ubuntu 9.10  *as pain free as possible* (I know its a fault with 9.10's kernal an I am sick of reading endless screens of tech drivel and testing it out only to find it still doesn't work at the end of it)

PS: I apologise if I sound flustrated by this problem its because I am and have had to resort to using ubuntu 9.04 just to connect to the internet since October 2009, has have many of those who "upgraded" to 9.10 in october, was it to much to expect it to "just work" the way it did in Ubuntu 9.04, Apparently it was (Groan). :-(

---

### Post by alexfish on 2010-02-04
Hi Nightstick2009

if Ubuntu 9.10 is fully updated then this device should be working with minimal problems

if you have updated then try deleting the device from NM , also clean up the cache and configs etc , I find Ubuntu Tweak makes this process easy, do a power down without the device , reboot without the device ,then make new connection.

However I believe this device is problematic for Linux in general for several reasons

if you can post the output of the device listing from the lsusb command , just to confirm the  device then I will be able to post pointers as to the reasons why this device may be problematic.

Thanks in advance

alexfish

---

### Post by qwerty2009 on 2010-02-04
i have 2 mobile broadband devices and they both work without a problem, when karmic was first released there was a problem with 1 of them but now its fixed.perhaps you should reinstall ubuntu if you cannot get it fixed

---

### Post by Nightstrike2009 on 2010-02-04
> **By alexfish:** Hi Nightstick2009 Who's Nightstick2009? LOL nevermind (obviously a typo, excuse me having a bad day) anyhow after 3 months reading over technical drivel this is all you need to do

1) Connect modem before Ubuntu 9.10 boots up
2) When the modem turns up as a drive (as Desktop Icon) right click it then select "Eject" from menu
3) Complete Network Wizard with correct details
4) If doesn't work first time "Disconnect" then "Connect" again from network manager's menu.

Thats all! 

Its ironic that after reading page after page of technical drivel fro 3 4 months, this is all you need to do to get this modem working with Ubuntu 9.10, wish I'd tried this before I went back to Ubuntu 9.10 (or even better it had been ironed out before 9.10's release). 

It seemed to be seeing Usb Modem as a usb drive once I ejected it via right click menu, it worked as a modem again, my guess is ubuntu 9.10 was trying to use the windows drivers stored onboard it (Obviously not compatible) anyhow its sorted now :-)

Lsusb output before and after fix:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 004: ID 2040:6600 Hauppauge 
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 008 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 008 Device 005: ID 13dd:0001 i.Tech Dynamic Limited 
Bus 008 Device 003: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 008 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Don't understand all that myself.

PS: It always worked with windows XP, Windows Vista and Ubuntu 9.04, the problem was with Ubuntu 9.10 :-)

---

### Post by alexfish on 2010-02-04
hi

for vodafone users UK , if you find the default server slow then try

OpenNic

Primary     DNS 217.115.138.24

Pings show that the primary one is very fast although it is in  Germany.


also avoid using  addresses 10.11.12.13. and 10.11.12.14 coming from vodafone " they have no domain name resolution"

---

### Post by Nightstrike2009 on 2010-02-06
UPDATE: download this .deb from [http://packages.ubuntu.com/karmic/usb-modeswitch]("http://packages.ubuntu.com/karmic/usb-modeswitch")

its called [COLOR="Red"]usb-modeswitch_1.0.2-1_i386.deb[/COLOR] and ends this problem in 9.10 once and for all, icon still appears but connection works :-)

UPDATE: Connecting to the internet still seems flaky at times but at least its better than no connection, hope they sort this out in Ubuntu 10.04LTS.

---

### Post by Darkhorse85 on 2010-02-08
HI
My k3565 doesn't even get mounted, nor does it show any sign in the network connections. The light flashes red when i insert it and then turns to flashing blue. I have no internet connection on that computer as the wireless does also not work. Can anybody help? I have been struggling to find a solution for weeks. 

(I downloaded 9.10 in early January, would it help to download and install a more up to date 9.10?)

regards
A mere mortal

---

### Post by Darkhorse85 on 2010-02-08
I forgot that i had installed usb-modeswitch 1.0.2-1_i386deb. I uninstalled it and then it was mounting. When creating a mobile broadband connection after restarting with the dongle plugged in before startup (it then mounts and then I unmount it accordingly) The device does not get picked up by the network connections. It just says 'wireless networks disconnected' in gray

---

### Post by Nightstrike2009 on 2010-02-09
Thread now changed from solved to unsolved again, connection now totally lost again, it worked for a while but now its borked again. :-(

> **By Darkhorse**:
I forgot that i had installed usb-modeswitch 1.0.2-1_i386deb. I uninstalled it and then it was mounting

Weird I have usb-modeswitch 1.0.2-1_i386deb installed but my modem still mounts I can't connect to internet now though, I tried to uninstall it but didn't feature in Synaptic, how did you remove usb-modeswitch 1.0.2-1_i386deb? My problem seems to have worsened since I installed it. 

Problem remains the same as before I discovered the "eject" workaround now. (detects, configure with wizard, connect with network manager, page cannot be loaded error everytime)

---

### Post by Nightstrike2009 on 2010-02-09
Right got it done this and it should work;

Plug in modem and setup connection wizard with correct settings.

The file that turns up on your desktop, right click it and select "eject" from menu

Right click (Signal) Network manager icon, set "edit connections" go to "Mobile broadband" (tab), highlight connection name, then click edit.

Set 
> Number to: *99#
Username: web
Password: web

Then go to IPv4 Settings (tab)

> Change method to "Automatic (PPP) addresses only"
DNS Servers to: 10.206.65.68
Search Domains to: 10.206.65.68

then click apply.

When asked for permission to access secret network code select yes always.

Thats how its done with Vodafone UK and a Huawei K3565 v2 modem.

Enjoy and have fun :-)

---

### Post by Nightstrike2009 on 2010-02-09
PS: If you prefer to use Wvdial check this thread [http://ubuntuforums.org/showthread.php?t=1402565]("http://ubuntuforums.org/showthread.php?t=1402565")

---

### Post by ibates on 2010-02-09
Frustration?  I have been battling Ubuntu for several months now.  Each and every attempt at any new software amounts to frustration.

But be that as it may, with respect to your VMC problems, I had the same experience (well almost) and this is what I did to solve the problem.  Hope it works for you.  The latest version of VMC made all the difference, and because I could find no way of uninstalling the older version, I simply installed the newer version over the top.

Perhaps one day someone will be able to explain how to uninstall programs which were not installed through either the Ubuntu Software Centre or Synaptic repo.

Anyway, here's what worked for me.

1.  go to [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

2.  Download and install the latest appropriate version of VMC which for i386 system is vodafone-mobile-connect_2.15.01-2_all.deb

3.  Make sure you have installed the latest versions of Modeswitch and Ozeorocdoff (you probably have).

Good luck.

---

### Post by alexfish on 2010-02-09
> **Nightstrike2009 said:**
> Right got it done this and it should work;

Plug in modem and setup connection wizard with correct settings.

The file that turns up on your desktop, right click it and select "eject" from menu

Right click (Signal) Network manager icon, set "edit connections" go to "Mobile broadband" (tab), highlight connection name, then click edit.

Set 


Then go to IPv4 Settings (tab)



then click apply.

When asked for permission to access secret network code select yes always.

Thats how its done with Vodafone UK and a Huawei K3565 v2 modem.

Enjoy and have fun :-)

hi

each service provider may have different APN and DNS. check with your service provider for details

if you use the wizard ,then  the DNS details for "IPv4 Automatic (PPP) Adress only ", and other details can be found a File called "serviceproviders.xml"

sceenshot below

also you can check this site

[SIZE=2][http://modmyi.com/wiki/index.php/Carrier_APN_Settings](http://modmyi.com/wiki/index.php/Carrier_APN_Settings)[/SIZE]

---

### Post by GB_Joe on 2010-02-24
Okay - I've followed this to the letter, and it's not having it. I just get a few seconds of the spinning radial icon, then the message "GSM network disconnected".

I'm on a fully updated 9.10. Networking has always been flawless for everything else.

I don't suppose it's a USB problem? Clutching at straws...

Incidentally, I've tried wvdial too, check that thread for more tales of woe...

---

### Post by Silvertones on 2010-02-24
I had an issue with my USROBOTICS USB dialup Modem.There's a known bug in 9.1 This may help or it may not. Worth a try. In Synaptic uninstall "modemmanager". I did this and Bang right out of the box it works perfectly. Has never missed a beat.

---

### Post by GB_Joe on 2010-02-25
Thanks for the suggestion Silvertones!

I've tried it, but it's made no difference.

---

### Post by GB_Joe on 2010-02-25
Guys - I'm sorry, but I may have been leading you all up the garden path here...

Just tried it on my Windows XP partition and I can't actually get online with that either! I'm thinking it may just be a simple reception issue, but until it stop chucking down with rain I'm not going to try wandering the streets looking for a signal...

I'll post back once I've got a solution...

---

### Post by GB_Joe on 2010-03-03
Wellity, wellity, wellity...

So, I got online with XP - seems I just had to do another reboot and be really patient.

Then I started all over again with the Betavine VMC software. Eventually got it running and connected, but no Firefox. Some magic combination of shutting off wifi, restarting Firefox and checking/unchecking the "Work Offline" box eventually got me online. Woohoo!

Except not...

I rebooted so I could work out the exact steps needed to get online, and VMC wouldn't even run. Nice. The debug info is totally different to anything I've had before.

As this has now gone off-topic, I won't discuss further unless I get some kind of resolution to share with you all, but I've posted on the Betavine forum if anyone wants to look:

[http://www.betavine.net/bvportal/auth/forums/index.html?threadId=ff80808126c2015e012724e35c6633a7]("http://www.betavine.net/bvportal/auth/forums/index.html?threadId=ff80808126c2015e012724e35c6633a7")

Cheers all - hope to be able to report some good news soon before I have to top myself...
Joe.

---

### Post by alexfish on 2010-03-03
Hi GB_Joe

sorry to here about your problems with this modem, I to have one of these Modem and it does work with Ubuntu 9.10

to try and Identify the problem could you confirm it is a K3565,also could your mention Your Service Provider 

also could you post the details of these commands from the terminal

Code:

lsusb

Code:

dmesg | grep -e "modem" -e "tty" 

from this hopefully we can get this modem configured with the network manager and not the VMC software.

regards

alexfish

---

### Post by GB_Joe on 2010-03-03
Good evening alexfish!

The mystery just gets deeper and deeper here...

I've managed to get this working just fine using wvdial (see Nightstrike2009's other thread here: [http://ubuntuforums.org/showthread.php?t=1402565]("http://ubuntuforums.org/showthread.php?t=1402565")), just type ```
sudo wvdial
``` to get it going and hit [Ctrl] & C to disconnect.

Then, for some unknown reason I decided to hit the VMC icon again, and the bu99er only went and started up...

I've been doing some more testing, and it seems that to get VMC to work you need to go to standby and then wake up again. Yep, you read that right. Clean reboot or shutdown/restart and you get nothing (whether or not you eject the device), but close the lid and open it again and once everything's up and running again it works every time.

This makes no sense to me, but the end result is I now have two ways of getting online.

I still like the idea of NetworkManager working though... so here's the output of lsusb
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 005 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
and dmesg | grep -e "modem" -e "tty"
```

[    0.001466] console [tty0] enabled
[   12.279658] USB Serial support registered for Sierra USB modem
[   12.279684] sierra 3-1:1.0: Sierra USB modem converter detected
[   12.281634] usb 3-1: Sierra USB modem converter now attached to ttyUSB0
[   12.281683] usb 3-1: Sierra USB modem converter now attached to ttyUSB1
[   12.281726] usb 3-1: Sierra USB modem converter now attached to ttyUSB2
[   12.281746] sierra: v.1.3.7:USB Driver for Sierra Wireless USB modems
[   88.135924] USB Serial support registered for GSM modem (1-port)
[   88.136113] option: v0.7.2:USB Driver for GSM modems
[   95.920932] option 1-1:1.0: GSM modem (1-port) converter detected
[   95.921054] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
[   95.921142] option 1-1:1.1: GSM modem (1-port) converter detected
[   95.921198] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB4
[   95.921261] option 1-1:1.2: GSM modem (1-port) converter detected
[   95.921321] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB5
[   95.921399] option 1-1:1.3: GSM modem (1-port) converter detected
[   95.921454] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB6
[   95.921532] option 1-1:1.4: GSM modem (1-port) converter detected
[   95.921592] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB7
[  155.241819] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[  155.241894] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[  155.241966] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[  163.264218] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  163.264374] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  163.264524] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  163.264673] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  163.264818] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  166.204392] option 1-1:1.0: GSM modem (1-port) converter detected
[  166.204519] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  166.232208] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  166.232275] USB Serial deregistering driver GSM modem (1-port)
[  166.250676] USB Serial support registered for GSM modem (1-port)
[  166.250780] option: v0.7.2:USB Driver for GSM modems
[  174.152541] option 1-1:1.0: GSM modem (1-port) converter detected
[  174.152705] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  174.152934] option 1-1:1.1: GSM modem (1-port) converter detected
[  174.153037] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  174.158195] option 1-1:1.2: GSM modem (1-port) converter detected
[  174.158335] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[  340.349546] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  340.349650] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  340.349748] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  340.607293] option 1-1:1.2: GSM modem (1-port) converter detected
[  340.607447] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  340.607561] option 1-1:1.1: GSM modem (1-port) converter detected
[  340.607671] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  340.607782] option 1-1:1.0: GSM modem (1-port) converter detected
[  340.607921] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[  347.070858] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  347.071038] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  347.071193] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1550.992097] USB Serial deregistering driver GSM modem (1-port)
[ 1551.127410] USB Serial support registered for GSM modem (1-port)
[ 1551.127523] option: v0.7.2:USB Driver for GSM modems
[ 1558.849652] option 1-1:1.0: GSM modem (1-port) converter detected
[ 1558.849827] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1558.850053] option 1-1:1.1: GSM modem (1-port) converter detected
[ 1558.850149] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1558.850343] option 1-1:1.2: GSM modem (1-port) converter detected
[ 1558.850440] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2

```
This is post-wake-up. I can tell, because VMC works! Do you want to see if the results are different after a reboot?

Incidentally, the laptop is a T60 with a built in Sierra MC8755 - you may have noticed that in the blurb above. I have tried popping the SIM in there, but I'm getting nothing with that...

Cheers!

Joe.

---

### Post by folabiklan on 2010-03-04
Hum. Well its great 2 see im not suffering alone. In my case its a huawei E156G usb modem and apparently network manager does recognise it and i can start a connection. But i cant browse the web, ping gets no response either. Infact as far as i can tell im offline yet network manager is connected and the modem is showing the blue led light which means connected.

This applies to both 9.04 and 9.10 by the way.

Whither goes ay? Nb : its perfect in xp and vista by the way!

---

### Post by alexfish on 2010-03-04
> **folabiklan said:**
> Hum. Well its great 2 see im not suffering alone. In my case its a huawei E156G usb modem and apparently network manager does recognise it and i can start a connection. But i cant browse the web, ping gets no response either. Infact as far as i can tell im offline yet network manager is connected and the modem is showing the blue led light which means connected.

This applies to both 9.04 and 9.10 by the way.

Whither goes ay? Nb : its perfect in xp and vista by the way!

HI


Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30


Save the file and exit

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

Tip try 30 first to see if this works, then work down


regards

alexfish

---

### Post by folabiklan on 2010-03-05
hey thanks for your help

well i tried your suggestion this morning. first i connected the modem successfully as usual and tried to surf but it didnt work, then i tried ur suggestion and uncommented the
icp-max-failure line and set it to 30 as pasted.

but then i looked into the network manager tabs and saw that under the wired tab, there was a "Auto-eth0" there. i have never used a wired lan connection on the computer before so i was bemused by that. i deleted it and lo and behold i cannot make a connection anymore! i tried t delete my connection there and make a new one, i restarted the computer but no way. i cant dial a connection with it anymore!

network manager does not recognise the modem or list it anymore.

ls usb still lists it but it gets the model wrong(it always has anyway) its listed as a E220, but is a E156G.

what have i done wrong and how do i remedy this mess! its very discouraging!!!

---

### Post by GB_Joe on 2010-03-05
folabiklan - it may be too late for you if you've borked NetworkManager (;)), but when I first established a connection with Betavine's VMC (that is, I got the solid blue light on the modem) I still found I couldn't get on to t'internet. I can't remember the exact combination and order of events now, but I think I had to have my wifi link disabled (nb NOT deleted) and Firefox closed, then got the modem connected, then things worked.

It may not work for you, but I hope this might be some encouragement... I think if you've got a solid blue light you're basically there...?

Good luck!
Joe.

PS I screwed my own laptop so badly messing around with this that the only solution was an upgrade to Lucid alpha3 via CD...

---

### Post by GB_Joe on 2010-03-05
alexfish

It's all gone wrong again...

Had my mate round tonight to collect the (working) laptop, except of course it didn't work. Not with wvdial, and VMC totally refused to start up.

So, as requested, here's another go at outputting lsusb
```

Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1199:6804 Sierra Wireless, Inc. MC8755 Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
and dmesg | grep -e "modem" -e "tty"
```

[    0.001469] console [tty0] enabled
[   14.709635] USB Serial support registered for Sierra USB modem
[   14.709664] sierra 3-1:1.0: Sierra USB modem converter detected
[   14.711530] usb 3-1: Sierra USB modem converter now attached to ttyUSB0
[   14.711576] usb 3-1: Sierra USB modem converter now attached to ttyUSB1
[   14.711623] usb 3-1: Sierra USB modem converter now attached to ttyUSB2
[   14.711645] sierra: v.1.3.7:USB Driver for Sierra Wireless USB modems
[  350.739052] USB Serial support registered for GSM modem (1-port)
[  350.739170] option: v0.7.2:USB Driver for GSM modems
[  358.517393] option 1-2:1.0: GSM modem (1-port) converter detected
[  358.517575] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  358.517716] option 1-2:1.1: GSM modem (1-port) converter detected
[  358.517816] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  358.517934] option 1-2:1.2: GSM modem (1-port) converter detected
[  358.518033] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  358.518174] option 1-2:1.3: GSM modem (1-port) converter detected
[  358.518287] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  358.518425] option 1-2:1.4: GSM modem (1-port) converter detected
[  358.518518] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
```

Sadly, he needs it back and working, so I'm probably going to have to just cave in and put a dodgy copy of Windows XP on instead.

*sigh*

So much for my Ubuntu evangelism, eh? Still, I've got a few waking hours left, maybe some miracle will occur!

---

### Post by ubseamus on 2010-03-08
Hi guys, trying to setup Vodafone E620 & having similar frustrations...

see my post @ 

[http://ubuntuforums.org/showthread.php?t=1240240](http://ubuntuforums.org/showthread.php?t=1240240)

---

### Post by alexfish on 2010-03-08
Hi GB-Joe

From your listing there are two modem attached to the system

Plug in only the USB modem that is required IE the Huawie 620

also disable any wireless or wired connections

then try the WVDIAL again


Please note from the name who I am posting the relies . Also of note,  this thread is for a K3565 modem 


regards 

alexfish

---

### Post by ubseamus on 2010-03-09
> **alexfish said:**
> Please note from the name who I am posting the relies.
 
Was it my post that caused this response?
 
> **alexfish said:**
> Also of note, this thread is for a K3565 modem
 
I am using a k36565, at least on my girlfriends macbook it shows up as that [and works]. But on lsusb lists it as e620 in ubunut.
 
 
Sorry if I failed to fully represent the situation.

---

### Post by GB_Joe on 2010-03-12
Well... that dongle was labelled K3565 v2, but it was identified in Ubuntu as an E620 (as ubseamus found).

Now, the thing is, I got this working in my own Ubuntu lappie, but it was identified as an E660 there.

Sadly, I can no longer do any work on this dongle, I had to give it and the laptop back to their owner, complete with a fresh install of Windows XP.

:-(

---

