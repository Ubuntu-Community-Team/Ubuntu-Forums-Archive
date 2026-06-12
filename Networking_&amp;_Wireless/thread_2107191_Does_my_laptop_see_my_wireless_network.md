---
title: "Does my laptop see my wireless network?"
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by mick2w on 2013-01-21
First oif all my apologies if this has been covered a million times before.

I have a Dell Inspiron 1300 on which I used to run Ubuntu 10.04LTS. I was able to connect to the internet through the laptop wireless adapter. I upgraded to 12.04LTS and the wireless stopped working.

I have bought a LogicPro wireless adapter and that enables me to get online but it would be really nice if I could connect using the built in one, which as aforesaid, worked with the earlier version of Ubuntu.

I asked two questions of the terminal:-

mick@mick-laptop:~$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
mick@mick-laptop:~$ ndiswrapper -l
mick@mick-laptop:~$
mick@mick-laptop:~$ nndiswrapper -v
No command 'nndiswrapper' found, did you mean:
 Command 'ndiswrapper' from package 'ndiswrapper-common' (main)
nndiswrapper: command not found
mick@mick-laptop:~$ ^C
mick@mick-laptop:~$


 PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
mick@mick-laptop:~$

I'm afraid I can only guess what it's telling me although I think I recognise the 14e4:4318 bit.

I have looked at the posts on this subject and tried to use the terminal but on a lot (i.e. vast majority) of occasions I do not know what I'm doing or what to look for so please keep any answer fairly basic.

My inexperience with the terminal is I think, obvious. Thanks in anticipation.

Mick

---

### Post by ahallubuntu on 2013-01-21
This will probably work for you if you can temporarily get online with the other card:

[http://askubuntu.com/questions/150929/no-firmware-found-for-broadcom-wireless-card-bcm4318-on-dell-latitude-d610](http://askubuntu.com/questions/150929/no-firmware-found-for-broadcom-wireless-card-bcm4318-on-dell-latitude-d610)

---

### Post by mick2w on 2013-01-21
> **ahallubuntu said:**
> This will probably work for you if you can temporarily get online with the other card:

[http://askubuntu.com/questions/150929/no-firmware-found-for-broadcom-wireless-card-bcm4318-on-dell-latitude-d610](http://askubuntu.com/questions/150929/no-firmware-found-for-broadcom-wireless-card-bcm4318-on-dell-latitude-d610)

Hello,

Thanks for the suggestion.

Here is the result I got from the terminal when I typed in 

sudo apt-get install b43-fwcutter firmware-b43-installer 



mick@mick-laptop:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for mick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libutouch-grail1 libutouch-evemu1 libutouch-frame1 libutouch-geis1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mick@mick-laptop:~$ 

Does this mean the driver is already installed?

I gave it the suggested 30 seconds plus a bit more and nothing happens. I have just tried toggling Fn + F2 because there seems to be no way to check whether the wireless is on or off.  

Is there a way to check whether the wireless is working through the terminal?

Thanks 

Mick

---

### Post by grahammechanical on 2013-01-21
> I gave it the suggested 30 seconds plus a bit more and nothing happens

What do you mean "nothing happens?" What did you expect to happen?

Have you clicked on the Network Manager icon in the top panel to see if Network Manager is now detecting wireless access points? Have you gone into System Settings and opened the Network utility to see if there is an option for wireless?

Regards.

---

### Post by mick2w on 2013-01-21
Have you clicked on the Network Manager icon in the top panel to see if Network Manager is now detecting wireless access points? Have you gone into System Settings and opened the Network utility to see if there is an option for wireless?

Hello again,

Sorry if I'm not giving you the right info.

Yes I have clicked the Network Manager icon and it shows 'No Network devices are available'

When I open System Settings and select Network a dialogue appears which shows 'Wired Cable Unplugged' Hardware address AA;BB;CC;DD;55:66:77:88 and some other detail beneath which reads

IPv4 address 127.0.0.1
IPv6::1
Subnet Mask 127.0.0.1
Default Route 127.0.0.1
DNS          127.0.0.1

To the left of this is a panel still within the same dialogue which has a little icon with 2 screens and Network proxy beside it.

When I click that I get another dialogue I get a proxy - Method and three options in a drop down menu of None/Manual and Automatic.

I select automatic and I'm asked for a configuration URL.

I put in here my wireless router access point number and press enter but there isn't any response. Am I on the right track.

Thanks 

Mick

---

### Post by mick2w on 2013-01-24
I'm still searching the forum as time permits for an answer to this. 

I have looked at the bios and the Inspirion 1300 that I'm using has the wireless functionality but using the Fn/F2 buttons I get no response. What I mean by that is the operational telltale on the front of the laptop doesn't light up so as the name of the thread implies I do not know if the laptop is even looking for a signal from my router. When I stick the Logic Pro USB wireless adapter in my network appears as do those of my neighbour's. As aforesaid in my previous posts I have toggled back and forth with Fn/F2 buttons. Is this a driver problem - I don't know, perhaps some kind soul can help me out.

Looking at other threads it seems the problem which is being encountered by a number of people has been solved in issue 13.04 Ragtail so if all else fails I may have to wait till that releases in April (apparently).

BTW - What are proprietary drivers in the context of Linux and where might these be acquired/downloaded/bought?

If this wasn't enough I now seem to have lost Firefox. Every time I try it it just displays the legend 'Connecting' and looks like it is by the little rotating circle in the top left corner, but never does. I have tried un-installing and re-installing but no improvement. 

I don't know much about the terminal but maybe I've done something in my ignorance that now prevents me getting Firefox to work. The puzzling thing is Google Chrome still works.

I am considering reinstalling Ubuntu 10.04 which I have a disc for but then it's another lengthy process getting all those updates again. 

I've been trying to get the hang of Linux in various guises since 2009 but there have been long periods when I haven't bothered at all for a number of reasons including a complete lack of knowledge of anything computer wise before Windows (I know nothing of MS/DOS)and the odd seemingly disparaging comment which can be a bit disheartening. 

Seriously though although people tell me I should read, read and read more it would be great if there were a definitive beginners guide as opposed to the list of threads from newbie's. Or is there such a guide and I just can't find it.....?

Mick

---

