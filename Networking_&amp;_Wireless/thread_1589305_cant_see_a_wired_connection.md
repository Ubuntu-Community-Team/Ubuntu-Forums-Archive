---
title: "cant see a wired connection"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by gloomy666 on 2010-10-06
Hello all,

my first post on this forum after 5 hours of ubuntu use. and i hit my first problem.

I wanted to try ubuntu out but not as a single operating system on my computer. This is since i use photoshop and flash a lot and i wanted to save the struggle of installing that for later.

Now my problem is. I did a fresh install of ubuntu. And i cant connect to my router. Not by wire, not by wireless.

my wireless usb adapter is a 300N WL-182 from sitecom. And after some google-sessions i found out that the chipset was causing a problem ( RT2870sta). so i decided to try wired connection first.

now i plugged in a wire between my router and my computer. and i dont have any notifications or what so ever that ive been connected to a network. in fact, im not.

when i log into my router from my laptop ( windows 7, is connected wireless). i discovered this might have been because of DHCP. so i revoked the time left on my computer. and replugged the ubuntu computer in the router. no reactions what so ever. neither on router or on the computer itself.

The network card im using is built in my motherboard.

I allso checked out all the ubuntu 10.4 stable release documentations for help. but they all say there must be connectivity allready.

can anyone please help me with this?  if you have any questions about hardware, software, etc. please ask

summary: 
- built in wired network card
- sitecom 300N WL-182 wireless adapter
- D-link DIR-635 wireless router. windows computer can connect ( firmware is updated to 2.30EU)

no connection, neither with USB adapter or wired

---

### Post by n.brenner on 2010-10-06
How New is everything?  if its new enough for win-7 then it sounds

like Ubuntu doesnt have the drivers for either, Or the vendor ID

Unless you have static IP's then your router is not any problem.

---

### Post by gloomy666 on 2010-10-06
well the computer itself is about 2.5 years old.
graphics card is a Nvidea 8600 GT.

forgot to mention. its dualbooted with vista.

i just tried something from someone else his topic:

the output from "sudo dhclient eth0" is:

```

owner@owner-desktop:~$ sudo dhclient eth0
[sudo] password for owner: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while fetting interface flags: No such device
eth0: ERROR while fetting interface flags: No such device
Bind socket to interface: No such device

```

Does this mean my networkcard aint working? or doesnt have the right driver?


edit:
just found the terminal code: lspci.
i cant find any ethernet controller in the list given there. looks like i need to buy a new ethernetcard? or do i need to find a driver or something?

---

### Post by gloomy666 on 2010-10-06
okey just found out the builtin ethernet card is the RTL8111 from realtek.

I found some linux drivers and am going to try install them now, hope it works

---

### Post by bkratz on 2010-10-06
Here is a long thread about that device.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1022411&page=4](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1022411&page=4)

post 34 looks like a good place to start

---

### Post by gloomy666 on 2010-10-06
okey i checked out the topic you just send. and in post 34 there was a referral to post 1.

now the problem is. when i list pci  with 'lspci'. i dont see an ethernet controller, its not listed.

i checked it out when booting up windows vista. Dont have an ethernet controller there either.

now i checked bios and went to advanced settings: onboard device configuration. Onboard LAN is enabled and Onboard LAN Boot ROM is disabled. I hope this is right?

Is it possible i have to update my bios before trying to do the guide in the following topic? [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1022411](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1022411)

---

### Post by bkratz on 2010-10-06
First thing I would do is

sudo update-pciids

this should update the lspci listing and maybe show it up.  Then I would post the output of  ( using the <code> tags for readability )

lspci -nn


Which should be the verbose version of lspci. with ID's, this should give a more accurate picture.

Edit:
It is not really the verbose version (which is -vv), but should show PCI vendor and device codes as both numbers and names.

---

### Post by gloomy666 on 2010-10-06
this is the output of the codes:

```

jouke@jouke-desktop:~$ sudo update-pciids
jouke@jouke-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)

```


allso i just tried installing the lan drivers from my chipset CD ( wich i got with the motherboard) but it cant find a makefile  after extracting it...

i then tried the newest version drivers of my ethernet card. and i was able to install them. So now i atleast got the right driver on my computer. tho it still wont find my ethernet card :(

---

### Post by bkratz on 2010-10-06
Could it possibly be on an internal usb bus? I have seen some wireless cards this.  you could find out with 


lsusb

which will display the usb devices if any. It works like lspci.

---

### Post by gloomy666 on 2010-10-06
im allso concidering the posibility that the ethernet adapter might have been broken. Though the lights are working...
when i put in an ethernet cable to my router it shows up a orange light with a yellow one blinking from time to time.
Tho via the ethernet adapter i cant connect to the router. Not with windows vista, not with ubuntu.

i tried installing the drivers for the adapter on both OS's, no results. allso now tried to reset teh CMOS by removing the battery from my motherboard.  nothing worked. doesnt show up in device manager.

allso doesnt shuw op in lsusb. this one just shows my AMBX set ( phillips) and my mouse (logitech usb thilt wheel)

so no results so far.

_*heres a little summary of things that i discovered:*_

**usb adapter[ ( sitecom 300N):**
recognized by the ubuntu OS but not working. Can't see all networks only the G networks. Cant connect to the networks if i do find them. Tried to blacklist some drivers and other tips online, didnt work.

**motherboard m2a-vm** 
( loads of posts about this motherboard found, most problems with the SATA).

**intergrated ethernet adapter to the m2a-vm is the RTL8168/8111/8111c.**
Cant be recognized on the device manager of windows. Cant be found on the usb-list and the pci-list in ubuntu.
The adapters lights work. i can see the lights go on when i plug in a cable and the yellow light next to it is flashing. Tried a diffrent cable, same result. 

**router: Dlink dir-635.** recognizes the windows PC's tried setting it to static IP, didnt work. Other windows 7 computer DOES have connection by wire. and my laptop has a wireless connection to it.

---

### Post by bkratz on 2010-10-06
No wonder you are Gloomy!  Wish I could have been some help, but it looks like it may actually be dead.

---

### Post by gloomy666 on 2010-10-06
well time to try and get that usb dongle to work then :P
thanks anyways. if i got any more questions i will just open a new topic since the title of the topic wont match with what m trying to do anymore.

thanks for your help :D really appreciated ^^

---

### Post by gloomy666 on 2010-10-07
well after i now learned how to install tars and stuff. i managed to install the new update for my wireless card, and blacklisted some other drivers. and i got my wireless USB adapter to work.

finally time to enjoy the speeds of ubuntu ^^

---

### Post by bkratz on 2010-10-07
Sure am glad you at least got the wireless working. Congratulations, you earned it!

---

