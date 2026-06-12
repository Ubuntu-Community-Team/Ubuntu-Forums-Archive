---
title: "How to Enable Your Hauppauge 1250 tv card"
date: 2010-12-18
forum: Multimedia Software
---

### Post by poe503 on 2010-12-18
**[SIZE="3"][SIZE="4"]Intro[/SIZE][/SIZE]**

This is a writeup to help you enable your Hauppauge 1250 tv tuner card so you can use it with programs such as Mythtv.  This will enable multiple cards.
I am assuming your card isn't working "out of the box".  You can check if it is recognized in the OS by following the instructions in "How to tell if the TV card is recognized" below.

In linux land, the 1250 is not just a 1250 but can be a variety of designations.  I own older 1250's which are listed as 1270's.  My newer cards are listed as 1255's.  These cards usually don't work "out of the box" with linux.  You have learn the ropes and enable them yourself.  You have to have time on your hands and be a glutton for punishment when it comes to setting up linux but a stable, well running system is worth it.  If you need everything done for you and want it "out of the box", you might as well ride back to Bill Gates' Boneless Chicken Ranch.

First off, here is an updated cardlist for the cx23885 driver that is used with the 1250 amongst other tuner cards:

[PHP]0 -> UNKNOWN/GENERIC                         [0070:3400]
 1 -> Hauppauge WinTV-HVR1800lp               [0070:7600]
 2 -> Hauppauge WinTV-HVR1800                 [0070:7800,0070:7801,0070:7809]            
 3 -> Hauppauge WinTV-HVR1250                 [0070:7911]
 4 -> DViCO FusionHDTV5 Express               [18ac:d500]
 5 -> Hauppauge WinTV-HVR1500Q                [0070:7790,0070:7797]
 6 -> Hauppauge WinTV-HVR1500                 [0070:7710,0070:7717]
 7 -> Hauppauge WinTV-HVR1200                 [0070:71d1,0070:71d3]
 8 -> Hauppauge WinTV-HVR1700                 [0070:8101]
 9 -> Hauppauge WinTV-HVR1400                 [0070:8010]
 10 -> DViCO FusionHDTV7 Dual Express         [18ac:d618]
 11 -> DViCO FusionHDTV DVB-T Dual Express    [18ac:db78]
 12 -> Leadtek Winfast PxDVR3200 H            [107d:6681]
 13 -> Compro VideoMate E650F                 [185b:e800]
 14 -> TurboSight TBS 6920                    [6920:8888]
 15 -> TeVii S470                             [d470:9022]
 16 -> DVBWorld DVB-S2 2005                   [0001:2005]
 17 -> NetUP Dual DVB-S2 CI                   [1b55:2a2c]
 18 -> Hauppauge WinTV-HVR1270                [0070:2211]
 19 -> Hauppauge WinTV-HVR1275                [0070:2215,0070:221d,0070:22f2]
 20 -> Hauppauge WinTV-HVR1255                [0070:2251,0070:2259,0070:22f1]
 21 -> Hauppauge WinTV-HVR1210                           [0070:2291,0070:2295,0070:2299,0070:229d,0070:22f0,0070:22f3,0070:22f4,0070:22f5]
 22 -> Mygica X8506 DMB-TH                    [14f1:8651]
 23 -> Magic-Pro ProHDTV Extreme 2            [14f1:8657]
 24 -> Hauppauge WinTV-HVR1850                [0070:8541]
 25 -> Compro VideoMate E800                  [1858:e800]
 26 -> Hauppauge WinTV-HVR1290                [0070:8551]
 27 -> Mygica X8558 PRO DMB-TH                [14f1:8578]
 28 -> LEADTEK WinFast PxTV1200               [107d:6f22]
[/PHP]

**[SIZE="3"][SIZE="4"]The Short and Sweet Writeup[/SIZE][/SIZE]**

This is for those of you who have been around the block with this stuff.
First, get the pci-id of your card and match that to what is listed above.
You need to download the v4l-dvb compilation or, if you have it and installed it, you need to uninstall it and clean up your mess.
Now that you have a clean and uninstalled v4l-dvb file, look for a file called "cx23885-card.c'.  Open the file and scroll down a ways to the area between lines 300 and 450.  You will see the pci-id designations for the different cards.  Swap the existing id of the appropriate card with your card's id number.  Save and close.
Configure, compile and install v4l-dvb and you are done.  Reboot and you hopefully should have your card appropriately recognized.

**[SIZE="3"][SIZE="4"]The Long and Winding Writeup[/SIZE][/SIZE]**

This is for those of you who know ' a little something about it' or don't know dip.

**Identify Your Card**

First you need to id your tv tuner card as it is seen by the operating system.  
Go to the terminal 

[PHP]lspci -v[/PHP]

Your tuner card should be listed.  You are interested in the line that says "Hauppauge ... Device XXXX". The XXXX would be the card number as recognized by the computer.  You want to match that to the card number on the above list which would be "0070:XXXX".

If your card isn't listed, see below in Troubleshooting.

**[SIZE="3"]If you haven't done anything yet[/SIZE]**

**Get v4l-dvb**

Go to [[COLOR="Green"]http://linuxtv.org/hg/[/COLOR]]("http://linuxtv.org/hg/") . This is the site that has the latest v4l-dvb folder which contains, among other things, lots of drivers for assorted media-related hardware.  The newest version of v4l-dvb is towards the top of the list.  On the right hand side of the page, you have different download options.  Pick "gz" and allow it to download to your home folder.

(Note to 9.04 users or earlier:  You need to download an earlier version of v4l-dvb on the list.  The latest compilation causes an error in earlier versions of Ubuntu so that the dvb core isn't recognized.  I used (as of 12/10) a 9 month old version by Hans Verkuil and it works just fine.)

Extract the compressed file to your home folder.  
Skip the next section.

**[SIZE="3"]If you've already been working with v4l-dvb, etc.[/SIZE]**

**Clean up your mess**

Remove any cards enabled in mythbackend.
Remove any configuration files you've placed in modprobe.d
Uninstall v4l-dvb:

[PHP]cd v4l-dvb
make rminstall[/PHP]

Hit enter until everything is uninstalled.
Clean up the rest:

[PHP]make distclean[/PHP]

You're done. 

**[SIZE="3"]Put Your Card Number on the List[/SIZE]**

Now for the fix.
Look in your new v4l-dvb folder for a file titled "cx23885-cards.c"
Open the file and scroll down to the area between lines 300 and 450.  This area contains all the card id numbers matched with card type.  Find your card type as listed above such as: HAPPAUGE_HVR1255.

It should look something like this:

[PHP].subvendor = 0x0070, 
.subdevice = 0x2251, 
.card      = CX23885_BOARD_HAUPPAUGE_HVR1255,[/PHP]

Exchange whatever is listed with your card id number.
For example, I have a 0070:2259 card.  I just remove the 1 and put in a 9 so it reads "0x2259".
Save your changes and exit.  You don't need root privileges if v4l-dvb is in your home folder.

**[SIZE="3"]Installation steps[/SIZE]**

First shutdown mythbackend if you have Myth installed.
In the terminal (new version):

[PHP]sudo stop mythtv-backend[/PHP]

alternatively (old version):

[PHP]sudo /etc/init.d/mythtv-backend stop[/PHP]

**Configure**
There is a glitch that prevents v4l-dvb from compiling successfully in Ubuntu so you need to change the default configuration.
You need to be in the v4l-dvb folder:

[PHP]cd v4l-dvb[/PHP]
then:
[PHP]make config[/PHP]

You will be presented with a very long list of configuration options.  Just hit the 'enter' key for each option until you come to"FIREDTV" then hit the "n" key and then press "enter".  Continue to just press "enter" until the list is done.

**Compile**

While in the v4l-dvb folder:

[PHP]make[/PHP]

The program will compile.  This will take some time.
When done:

**Install**

[PHP]sudo make install[/PHP]

This will take some time.  When done:

**Reboot**

Your card should now be recognized.

**[SIZE="4"]How to tell if the tv card is recognized.[/SIZE]**

Go to System>Administration>Log File Viewer.
Look for the "dmesg" log.  Scroll down to near the bottom of the log and you should see something like  this if your card is recognized:
(the example shows 2 cards enabled)

[PHP]8.095770] Linux video capture interface: v2.00 
[    8.112896] cx23885 driver version 0.0.2 loaded 
[    8.113105] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    8.113207] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,autodetected] 
[    8.144163] ENS1370 0000:05:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    8.156885] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume 
[    8.259571] tveeprom 1-0050: Hauppauge model 22111, rev E2F5, serial# 7291320 
[    8.259573] tveeprom 1-0050: MAC address is ed1fbc9d 
[    8.259575] tveeprom 1-0050: tuner model is NXP 18271C2 (idx 155, type 54) 
[    8.259576] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88) 
[    8.259578] tveeprom 1-0050: audio processor is CX23888 (idx 40) 
[    8.259579] tveeprom 1-0050: decoder processor is CX23888 (idx 34) 
[    8.259580] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter 
[    8.259582] cx23885[0]: hauppauge eeprom: model=22111 
[    8.259583] cx23885_dvb_register() allocating 1 frontend(s) 
[    8.259584] cx23885[0]: cx23885 based dvb card 
[    8.352383] tda18271 2-0060: creating new instance 
[    8.354427] TDA18271HD/C2 detected @ 2-0060 
[    8.586378] DVB: registering new adapter (cx23885[0]) 
[    8.586381] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)... 
[    8.586549] cx23885_dev_checkrevision() Hardware revision = 0xd0 
[    8.586556] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfe800000 
[    8.586562] cx23885 0000:03:00.0: setting latency timer to 64 
[    8.586584] cx23885 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    8.586683] CORE cx23885[1]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,autodetected] 
[    8.679645] psmouse serio1: ID: 10 00 64<6>tveeprom 4-0050: Hauppauge model 22111, rev E2F5, serial# 7291090 
[    8.733134] tveeprom 4-0050: MAC address is ed1fbc9d 
[    8.733136] tveeprom 4-0050: tuner model is NXP 18271C2 (idx 155, type 54) 
[    8.733137] tveeprom 4-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88) 
[    8.733139] tveeprom 4-0050: audio processor is CX23888 (idx 40) 
[    8.733140] tveeprom 4-0050: decoder processor is CX23888 (idx 34) 
[    8.733141] tveeprom 4-0050: has no radio, has IR receiver, has no IR transmitter 
[    8.733143] cx23885[1]: hauppauge eeprom: model=22111 
[    8.733144] cx23885_dvb_register() allocating 1 frontend(s) 
[    8.733146] cx23885[1]: cx23885 based dvb card 
[    8.778774] tda18271 5-0060: creating new instance 
[    8.780818] TDA18271HD/C2 detected @ 5-0060 
[    9.008712] DVB: registering new adapter (cx23885[1]) 
[    9.008714] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)... 
[    9.008854] cx23885_dev_checkrevision() Hardware revision = 0xd0 
[    9.008860] cx23885[1]/0: found at 0000:01:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xfbe00000 
[    9.008865] cx23885 0000:01:00.0: setting latency timer to 64
[/PHP]

If not recognized, the log should look something like this:


[PHP][ 29.664538] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 29.664543] cx23885[1]: Your board isn't known (yet) to the driver.
[ 29.664544] cx23885[1]: Try to pick one of the existing card configs via
[ 29.664545] cx23885[1]: card=<n> insmod option. Updating to the latest
[ 29.664545] cx23885[1]: version might help as well.
[ 29.664547] cx23885[1]: Here is a list of valid choices for the card=<n> insmod option:
[ 29.664549] cx23885[1]: card=0 -> UNKNOWN/GENERIC
[ 29.664550] cx23885[1]: card=1 -> Hauppauge WinTV-HVR1800lp
[ 29.664551] cx23885[1]: card=2 -> Hauppauge WinTV-HVR1800
[ 29.664552] cx23885[1]: card=3 -> Hauppauge WinTV-HVR1250
[ 29.664554] cx23885[1]: card=4 -> DViCO FusionHDTV5 Express
[ 29.664555] cx23885[1]: card=5 -> Hauppauge WinTV-HVR1500Q
[ 29.664556] cx23885[1]: card=6 -> Hauppauge WinTV-HVR1500
[ 29.664557] cx23885[1]: card=7 -> Hauppauge WinTV-HVR1200
[ 29.664558] cx23885[1]: card=8 -> Hauppauge WinTV-HVR1700
[ 29.664559] cx23885[1]: card=9 -> Hauppauge WinTV-HVR1400
[ 29.664561] cx23885[1]: card=10 -> DViCO FusionHDTV7 Dual Express
[ 29.664562] cx23885[1]: card=11 -> DViCO FusionHDTV DVB-T Dual Express
[ 29.664563] cx23885[1]: card=12 -> Leadtek Winfast PxDVR3200 H
[ 29.664564] cx23885[1]: card=13 -> Compro VideoMate E650F
[ 29.664566] cx23885[1]: card=14 -> TurboSight TBS 6920
[ 29.664567] cx23885[1]: card=15 -> TeVii S470
[ 29.664568] cx23885[1]: card=16 -> DVBWorld DVB-S2 2005
[ 29.664569] cx23885[1]: card=17 -> NetUP Dual DVB-S2 CI
[ 29.664570] cx23885[1]: card=18 -> Hauppauge WinTV-HVR1270
[ 29.664571] cx23885[1]: card=19 -> Hauppauge WinTV-HVR1275
[ 29.664572] cx23885[1]: card=20 -> Hauppauge WinTV-HVR1255
[ 29.664574] cx23885[1]: card=21 -> Hauppauge WinTV-HVR1210
[ 29.664575] cx23885[1]: card=22 -> Mygica X8506 DMB-TH
[ 29.664576] cx23885[1]: card=23 -> Magic-Pro ProHDTV Extreme 2
[ 29.664577] cx23885[1]: card=24 -> Hauppauge WinTV-HVR1850
[ 29.664578] cx23885[1]: card=25 -> Compro VideoMate E800
[ 29.664657] CORE cx23885[1]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 29.792147] cx23885_dev_checkrevision() Hardware revision = 0xd0
[ 29.792154] cx23885[1]/0: found at 0000:03:00.0, rev: 4, irq: 19, latency: 0, mmio: 0xfe800000
[ 29.792160] cx23885 0000:03:00.0: setting latency timer to 64
[ 29.792163] IRQ 19/cx23885[1]: IRQF_DISABLED is not guaranteed on shared IRQs

[/PHP]


If you are using Mythtv,  go to the backend and try to enable a "new capture card".  
Select "DVB DTV Capture Care (v3.x)".  
Myth should select a card number (0,1.etc) and there should be a description in "Frontend ID".
Example:
[I]Card Type: DVB DTV capture card (v3.x)
DVB Device Number: /dev/dvb/adapter0/frontend0
Frontend ID: LGDT3305
Subtype: ATSC
[/I]
In the main Mythbackend menu, there is also "video sources" and "input connections".

The bare bones of it is you need to set your card as a "video source" and then fix up the "input connection" which includes scanning for channels.

**[SIZE="4"]Troubleshooting[/SIZE]**

[B][SIZE="3"]My card is not on the list.
[/SIZE][/B]
You can try to find out if your card will be recognized as one of the card numbers on the list by creating a new file named "cx23885.conf" in /etc/modeprobe.d/.
First in the terminal:

[PHP]sudo nautilus[/PHP]

This is a very powerful command; use it wisely or you can easily shoot your whole installation to hell.

Navigate to /etc/modeprobe.d.
Right click in the window and select "create document" then select "empty file".  
Name the file "cx23885.conf".
Place the following in the file:

[PHP]options cx23885 card=20 
options CORE_cx23885[0]_dvb adapter_nr=0[/PHP]

You can use any "card=x" you wish from the cardlist that is posted above.
Save and close the file.
Reboot.
Follow the "how to tell if the TV card is recognized" instructions above.
If not recognized,  change the number in the modeprobe.d file and try again.  Hopefully you will have success and can then use the fix described above.
The modeprobe fix is limited to one card and I found the results to be poor as far as video quality and sound sync were concerned.

**[SIZE="3"]The video doesn't look too good.[/SIZE]**

Download the EnvyNG program which will improve the results you get from your graphics card.
You typically need to add "vmalloc=256M" to the kernel parameters in grub for Envy to boot correctly.  This may not be true of newer versions of Ubuntu.



**[SIZE="4"]Sources:[/SIZE]**

The fix:

[http://www.mythtvtalk.com/two-hvr-1250s-13295/](http://www.mythtvtalk.com/two-hvr-1250s-13295/)

v4l-dvb:

[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by Raoul Duke, esq. on 2010-12-29
SWEET! thanks for the great walk through! 

Now what do I do if I want to use my 1250 to capture an Analog signal from my Sony Hi8 CCD-TRV67 NTSC so I can back up my old video tapes to DVD? What program do I need?

---

### Post by VonSpyder on 2010-12-29
will this work for a USB tuner card? I just got a Diamond ATI Tv Wonder HD750 and hgavent had any luck getting linux to recognize it.

---

### Post by poe503 on 2010-12-29
I am afraid that I am a one-hit wonder when it comes to this stuff, gents.  I am not the grand poobah of tv cards.

This tutorial is the result of a lot of digging and personal experience getting my 1250s to work for ATSC.

I can comment on my writeup but you will have to look elsewhere for advice on the rest.

---

### Post by redwoodguy on 2011-01-08
This didn't work for my 1250 card. I get this from the system log:
[   16.894409] cx23885 driver version 0.0.2 loaded
[   16.894449] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.894681] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   16.989392] lp0: using parport0 (interrupt-driven).
[   17.172058] IR NEC protocol handler initialized
[   17.172276] RPC: Registered udp transport module.
[   17.172279] RPC: Registered tcp transport module.
[   17.172281] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   17.181539]   alloc irq_desc for 21 on node -1
[   17.181543]   alloc kstat_irqs on node -1

However, nothing will set the card up when I try to "add capture card" in the mythbuntu back end.
It won't give a "card number"

---

### Post by poe503 on 2011-01-09
A "0070:2259" card should be "card=20", not "card=3".  In other words, it should be recognized as a 1255 not a 1250.

---

### Post by sgarbeil on 2011-03-09
If you are building against a kernel > 2.6.36, use git. The hg repo is now backports only and there are several changes to the linux kernel that make compiling irritating and problematic. 
It can be done (I did it) but it's very time consuming.

---

### Post by freewaybear on 2011-04-19
Thanks for this, I just acquired a 1290, and this is the first possibly useful thread I've found :D I will go through all this on the weekend, wish me luck.

---

### Post by Exeleration-G on 2011-04-26
Is this DVB-T only? I'm trying to get this running with a HP Digital/Analog TV Tuner ExpressCard, which is in fact just a rebranded Hauppauge HVR-1500, but without any success until now. It does get recognised, my system hangs if I just remove it. But it won't be accessible in VLC, nor in any other TV program.

---

### Post by poe503 on 2011-04-30
Sorry, I am not familiar with your card.

Perhaps you should post your problem on a new thread with your card type in the title.  Someone who knows about this might pick up on it.

---

### Post by Exeleration-G on 2011-05-01
OK, I will. Thanks for the posts though.

---

### Post by petesbbq on 2011-06-16
Pulling my hair out trying to configure this card:
[http://linuxtv.org/wiki/index.php/AVerMedia_M791_PCIe_Combo_%28OEM%29](http://linuxtv.org/wiki/index.php/AVerMedia_M791_PCIe_Combo_%28OEM%29)

I followed the instructions above to no avail.  I found this post which 'claims' to have the card working:
[http://ubuntuforums.org/showthread.php?p=10947200#post10947200](http://ubuntuforums.org/showthread.php?p=10947200#post10947200)

But my card is not identified nor does the post author state the card they used.  Tried card=20 but I get an error, card=3 does not work either.  I have successfully extracted the OEM firmware but have not been successful in making it work thus far.  Any ideas?

---

### Post by poe503 on 2011-06-16
A quick glance at the card link you posted indicates that this is an Avermedia card not Hauppauge.  The bottom of the page seems to indicate that no linux driver is available for this card.  Sorry.

---

### Post by poe503 on 2011-06-17
I would add that the OS is trying to do its best to match your card with an appropriate driver, so you get a list of cards that work with the CX23885 driver which is probably the closest approximation to what is needed for your card.

A search of the PCI id of your card "1461:d439" on google brought up this interesting link: [*http://lists-archives.org/video4linux/21248-avermedia-m791-combo-oem-tv-card.html*]("http://lists-archives.org/video4linux/21248-avermedia-m791-combo-oem-tv-card.html")

---

### Post by Tronester on 2011-07-04
I have the exact same card as you, the 2259.

I followed your instructions but on the capture card setup, it lists my front end Id as a samsung s5h1411 qam.  Is this correct?  I scan for channels and get 0 signal strength on every single one.

---

### Post by poe503 on 2011-07-04
Yes, the Samsung id is correct.  Be sure that you have an appropriate antenna for ATSC.  An antenna I used to use couldn't pick up any signal and I had to change.  ATSC is terribly go/no go.  A somewhat weak signal won't pick up at all.

---

### Post by 3j3x on 2011-08-01
heh... you know how you said, "Just hit the 'enter' key for each option until you come to"FIREDTV" then hit the "n" key and then press "enter"."? Well....I was zoned out and hit enter instead of "n". 

Did I just fire my TV?

---

### Post by poe503 on 2011-08-01
Ha,ha.:D

You can rehire your tv by running "make config" again.  Nothing lost.

By not firing Firedtv, the program won't compile.  (at least didn't used to; time moves on, you know, and this may no longer be applicable)

If you tried to compile and it complained, just run "make config" again and "n" to Firedtv and then compile.

---

### Post by Daibhi on 2011-10-15
Followed your instructions, unfortunately the card is still not recognized. I'm a noob to Linux so please do shut me down. But the videocard is a Hauppauge 1250 PCI-E card, when I try to run Mythtv it gives me a No UPNP popup. When I try to run TVTime it says no signal, and cannot open capture device /dev/video0. I do go to the /dev folder but find no video0. Is this something I can create in Nautilus or am I stepping out of my league. I would appreciate any help on this very much. This card works fine in Win7, but like all OS devotees and virgins like me. I rather like OSS.

---

### Post by poe503 on 2011-10-16
First of all, did you identify your card as described in the first step and is it on the card list?

---

### Post by Daibhi on 2011-10-16
on the lspci -v entry on terminal I get

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
    Subsystem: Hauppauge computer works Inc. Device 2259
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

So I've been working using cx23885 as the base to work from.

---

### Post by poe503 on 2011-10-16
Well... "2259" or "0070:2259" is exactly the version of the 1250 card that I am addressing in this tutorial.  This version of the card is too new (at least a year ago) to be used "out of the box" with Ubuntu so it is necessary to do the steps in the tutorial.

Rather than asking "20 questions", give me a rundown of what you did while following this tutorial.  Be sure to state any uncertainties you had while doing this.

---

### Post by Daibhi on 2011-10-16
From Poe: Well... "2259" or "0070:2259" is exactly the version of the 1250 card  that I am addressing in this tutorial.  This version of the card is too  new (at least a year ago) to be used "out of the box" with Ubuntu so it  is necessary to do the steps in the tutorial.

Rather than asking "20 questions", give me a rundown of what you did  while following this tutorial.  Be sure to state any uncertainties you  had while doing this."

Me: I'm 30 plus yr Microsoft glutton for punishment and have recently joined the Linux side of the Force. As a Microsoft idgit I'm used to following instructions letter by letter, also how I was taught. So yes, I did a dry run first making sure I had an eyeball as to where everything was. Then a wet run in which I went through and applied each item as written. I'm running the 11.10 version of Ubuntu if that may make a difference. I'm did a double check on the v4l-dvb directory file for the c23885 card specs and did change the code correctly. 

The only concerns were during compiling on a couple of items not links to this issue it gave an error permission denied code.

I tried getting in through Mythtv backend, and it comes up with a No UPnP error. And shows no card.

---

### Post by Daibhi on 2011-10-16
when I checked the dmesg log I found this entry for the card, after reboot.

[   21.499847] cx23885 driver version 0.0.2 loaded
[   21.499893] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.554429] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,insmod option]
[   21.702250] parport_pc 00:07: reported by Plug and Play ACPI
[   21.702361] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   21.749623] intel_rng: FWH not detected
[   23.232643] leds_ss4200: no LED devices found
[   23.278610] lp0: using parport0 (interrupt-driven).
[   23.790984] tveeprom 0-0050: Hauppauge model 22111, rev E2F5, serial# 7430875
[   23.790989] tveeprom 0-0050: MAC address is 00:0d:fe:71:62:db
[   23.790993] tveeprom 0-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   23.790996] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   23.790999] tveeprom 0-0050: audio processor is CX23888 (idx 40)
[   23.791002] tveeprom 0-0050: decoder processor is CX23888 (idx 34)
[   23.791005] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   23.791007] cx23885[0]: hauppauge eeprom: model=22111
[   23.791011] cx23885_dvb_register() allocating 1 frontend(s)
[   23.942491] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.942551] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   23.942579] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.339150] cx23885[0]: cx23885 based dvb card

Gee and I thought the old IBM AS400's to be quirky!

---

### Post by poe503 on 2011-10-16
Your demesg entry shows the card is being recognized. 

"no UPnP" in relation to the mythbackend sounds familiar but I don't do this regularly so I will need to think about it.  Are you getting the mythbackend menu?  It has a list like "capture card", "video sources",etc..

Often no mythbackend is available because the person installing Mythtv entered passwords during installation and should have left them blank.  A classic mistake.

---

### Post by Daibhi on 2011-10-17
Mythtv backend is picking up no input nor is giving me menu choices beyond the host/ping/database locations. This is a stumper for me I'm trying everything. The only thing I haven't done yet and I don't know if it'll blow up my system is to use Nautilus and physically create a video0 file similar to the cx23885.conf file to see it that might jumpstart it.

---

### Post by poe503 on 2011-10-17
Mythbackend should boot to its menu even if no video card is installed.  In that instance, the capture card part of the menu would show no card is available to use.

Your Mythtv installation is at fault, not the video card.

Did you put in passwords for Mysql when you were installing Myth? You should have left the various prompts for a password blank during the installation process. That is usually the reason mythbackend is unavailable after a fresh installation.

---

### Post by Daibhi on 2011-10-17
I am uninstalling the version of Myth and reinstalling from the Ubuntu Software Center Console, it has the newer versions. I tried connected and got a screen after the No UPnP Screen with the error that it could not connect to database even though database was built. 

So at present I'm stuck with a system that recognizes there's a card there but cannot pull a signal through the card. This may be of some use but does it make a difference if the incoming signal is routed through a cable box? Should I bypass the box all together?

---

### Post by MartyBuntu on 2011-10-17
> **Daibhi said:**
> 

So at present I'm stuck with a system that recognizes there's a card there but cannot pull a signal through the card.

Have you tried a digital input signal? That seems to be supported out of the box.

It's the analog signal that's tricky.

---

### Post by Daibhi on 2011-10-17
Wish I could go back and delete last msg. Tried and no success with running cable straight into system. I'm back to running it through the box just in case. 

I'm going to do another make config in the v4l-dvb directory to make sure that Firedtv is down.

Any other suggestions while i'm in there would be appreciated. 

And yes I do appreciate the time you're taking with this poor doof here trying to get this in order.

---

### Post by Daibhi on 2011-10-17
Marty! Thanks for the reply, I've tried everything and am will to try standing on my head sacrificing a rubber duck if it would help! :) Can  you give me a heads up on how to the get to the digital signal area because right now I've got two TV apps, one being MythTV that says there's no card there, even though the system says uh yeah! All help is appreciated.

---

### Post by MartyBuntu on 2011-10-17
What are you connecting to your card? What is your digital input?

---

### Post by Daibhi on 2011-10-17
FWIW this was under the input where the signal for the Hauppauge card was accepted. 

[   24.831448] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   24.831460] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfe800000
[   24.831471] cx23885 0000:03:00.0: setting latency timer to 64
[   24.836038] init: failsafe main process (744) killed by TERM signal
[   24.906913] init: apport pre-start process (847) terminated with status 1
[   24.968617] init: apport post-stop process (876) terminated with status 1

---

### Post by MartyBuntu on 2011-10-17
The 1250 only supports digital mode at this time.

Have you seen this page?

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)


...or this?

[http://linuxtv.org/wiki/index.php/Hauppauge](http://linuxtv.org/wiki/index.php/Hauppauge)


Are you using an ATSC antenna hooked up to your card?

---

### Post by poe503 on 2011-10-17
Again,if you can't get into the Mythbackend, it's not the video card's fault.

I am not clear from what you have posted if this is a password problem with Mysql (database server).  

If so, removing and reinstalling Myth won't fix the problem as Synaptic installed a package associated programs, including Mysql, with the initial installation of Myth. When you ask it to remove and reinstall Myth, it won't remove and reinstall that whole package of programs with Myth.

There are ways to fix a password problem but I don't have the information to hand.

---

### Post by Daibhi on 2011-10-17
I'll check the mysql area but in the meantime when I pulled the lspci -v in terminal I noticed this packet...

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
    Subsystem: Hauppauge computer works Inc. Device 2259
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

It id's the cards a cx23887/8 would this make a difference?

Thanks

---

### Post by MartyBuntu on 2011-10-17
You are complicating this.

**Can you receive a digital signal?**

The 1250 "works out of the box". Test it with Kaffeine or MeTV.
Believe me, they are way easier to set up than Myth.

---

### Post by Daibhi on 2011-10-17
Try Kaffiene, am getting a black screen, I go to Channels and try to do a scan and it says "No available device found." I've tried Me TV in all configurations and it's not pulling any stations.

---

### Post by MartyBuntu on 2011-10-17
I keep asking you how you are hooking up your card...to what?

Are you using an ATSC OTA antenna or do you have a cable provider?

---

### Post by Daibhi on 2011-10-17
Sorry, the cable is running through a standard Comcast converter box.

---

### Post by MartyBuntu on 2011-10-17
I believe Comcast encrypts most of it's channels now.

Try this...try running the cable directly into the card, bypassing the Comcast box and make sure you search for QAM as well.

Anything?

---

### Post by MartyBuntu on 2011-10-17
**For cable, change Modulation to 'Cable (QAM-256)'. All U.S. cable companies either use QAM-256 or QAM-64, most including Comcast use QAM-256. **

Maybe this.

---

### Post by Daibhi on 2011-10-17
BTW that is my digital signal.

---

### Post by Daibhi on 2011-10-17
tried direct run, nothing. Still no results on a QAM search, I tried that early on. Let me try that on the modulation. At this point rerunning Ubuntu load from scratch is looking real good, if nothing else to clean up the files and perhaps get it recognized when it details the hardware devices. Hey Marty, thanks for putting up with this noob, I'm learning a good bit from y'all.

---

### Post by MartyBuntu on 2011-10-18
I'll see what else I can come up with later today.

---

### Post by Daibhi on 2011-10-18
FWIW, did a complete reinstall of Ubuntu, went through setup procedure recommended by POE, TVTime still shows nothing in /dev/video0, I'm going to investigate that a bit deeper and see if there is another folder it should be pointing to. However Kaffiene shows no device available.

---

### Post by MartyBuntu on 2011-10-18
> **Daibhi said:**
> still shows nothing in /dev/video0

You're looking in the wrong place. /dev/video0 pertains to analog or analog/digital hybrid cards. You have a digital-only card.

Look in **/dev/dvb**.

Anything there?

---

### Post by MartyBuntu on 2011-10-18
I have Kaffeine and MeTV installed and I'm ripping phenomenal quality, HD "over-the-air" broadcasts.

If you have either of these programs installed, I can walk you through the steps.

---

### Post by Daibhi on 2011-10-18
yeah adapter0 which I assume is the correct adapter. I've got Kaffiene loaded but it keeps throwing back no device available, obviously I'm doing something wrong.

---

### Post by MartyBuntu on 2011-10-18
- Start Kaffeine
- Click the "Television" tab
- Click "Configure Television"
- Beside the "General Options" tab should be a tab labeled "Device 1"
- For "source", make sure it's set to **US-Cable-STD QAM256**
- The "name" should be **Atsc**.


Let me know if you've got that far.

---

### Post by Daibhi on 2011-10-18
right with ya

---

### Post by Daibhi on 2011-10-18
I'm there!

---

### Post by MartyBuntu on 2011-10-18
Awesome. Hang on a sec...

---

### Post by MartyBuntu on 2011-10-18
Great. Then click "OK" and back on the main window of Kaffeine, click the "Television" tab and then choose "channels".

You should see this...

[IMG]http://i.imgur.com/Prr76.png[/IMG]

The box on the left is probably empty for you at this time.

Just go ahead and click the "Start Scan" button...

---

### Post by Daibhi on 2011-10-18
Where I should be getting channels I get a little pop up box saying "no available device found."

---

### Post by MartyBuntu on 2011-10-18
Okay, I don't use Comcast (I'm on Rogers Digital cable service here in Canada) but as I understand it, Comcast encrypts their signal...but they might not encrypt *all* signals. For example, my cable company only allows a handful of unencrypted signals, namely music-only channels and free-preview channels.

If you have your cable running into a set-top-box and then into your 1250 card, try running the cable directly into the 1250 card and re-run my previous instructions.

Lets see if you get anything that way.

---

### Post by Daibhi on 2011-10-18
sorry, same song second verse.

---

### Post by MartyBuntu on 2011-10-18
One more thing...

In Kaffeine, under the "Television" tab...and then "Configure Television" and then "Device 1", do you see something similar to this?

[IMG]http://i.imgur.com/x8jvF.png[/IMG]

---

### Post by Daibhi on 2011-10-18
No mine shows SSH1411 QAM/BVSB Frontend

---

### Post by MartyBuntu on 2011-10-18
No, that's fine. I use the Hauppauge 1800, that's why.

In this pic, are all your settings identical when you hit scan (aside from the found channels in my chart) both with the set-top-box connected and without?

[img]http://i.imgur.com/Prr76.png[/img]

---

### Post by Daibhi on 2011-10-18
My source says Atsc. is there a way to make that selection Cable or Transponder. I'm not getting a choice at my end.

---

### Post by MartyBuntu on 2011-10-18
Try doing a scan with **w_scan**, specifically for Kaffeine...

[http://wirbel.htpc-forum.de/w_scan/index_en.html](http://wirbel.htpc-forum.de/w_scan/index_en.html)


Get w_scan from here:

[http://manpages.ubuntu.com/manpages.gz/natty/man1/w_scan.1.gz](http://manpages.ubuntu.com/manpages.gz/natty/man1/w_scan.1.gz)

Then, after it's installed, in a terminal type:

**w_scan -A2 > channels.conf**    (*run it as root*)

(This is for American cable and should work for Comcast)

---

### Post by MartyBuntu on 2011-10-18
[http://wirbel.htpc-forum.de/w_scan/index_en.html](http://wirbel.htpc-forum.de/w_scan/index_en.html)

This is a more detailed instruction page.

---

### Post by Daibhi on 2011-10-18
have some problems getting w_scan.1 to load stand by.

---

### Post by Daibhi on 2011-10-18
Dumb ? here, that file you sent was w_scan.1, what's the command line to run that..? I've tried all the ones that I do know so far and again the obvious something I'm missing.

---

### Post by MartyBuntu on 2011-10-18
D'OH! Sorry...

Get it here:
[http://vdr.bluox.org/download/index.php?path=DVB/](http://vdr.bluox.org/download/index.php?path=DVB/)

It's the file labelled: w_scan-20050908.tar.bz2

---

### Post by Daibhi on 2011-10-18
Results don't look too good...

david@david-ubuntu-orthanc:~/w_scan$ ./w_scan
Info: using DVB adapter auto detection.
Info: unable to open frontend /dev/dvb/adapter0/frontend0'
Info: unable to open frontend /dev/dvb/adapter1/frontend0'
Info: unable to open frontend /dev/dvb/adapter2/frontend0'
Info: unable to open frontend /dev/dvb/adapter3/frontend0'
main:1780: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

The Card is there, and runs fine, or it did under Windows. I'm going to back out of Linux a mo and check Windows...much as a I frakking hate to. Windows :P But that's just me,

---

### Post by MartyBuntu on 2011-10-18
I hate to say it but, I had a Hauppauge 1600 PCI card I bought on eBay die on me within two weeks...

:o


Hope that's not the case.

---

### Post by Daibhi on 2011-10-18
Ok this is weirder than dog-doo! I went into the cx23885.cards.c file over in the v4l dir. Changed the code for the 1250 card to the code that lspci returns which was 2259, now Kaffiene is scanning, don't know if I'll get any channels yet but something positive in that.

---

### Post by Daibhi on 2011-10-19
Packing it in for the night for this puppy. Will try some more tricks tomorrow.

---

### Post by Daibhi on 2011-10-20
Still at square one. The little trick I tried with the cards file didn't really do anything substantive. No freqs read in any combination of settings in Kaffiene.

---

### Post by wolfen69 on 2011-10-20
You can spend months trying to get a tv card working in linux, and it still won't work right. If you can afford it, sometimes you are just better off buying a new one that is known to work well with linux.

---

### Post by MartyBuntu on 2011-10-20
> **wolfen69 said:**
> You can spend months trying to get a tv card working in linux, and it still won't work right. If you can afford it, sometimes you are just better off buying a new one that is known to work well with linux.


The Hauppauge 1250 does work with Ubuntu. We just have to find out why the OP's card doesn't.

---

### Post by MartyBuntu on 2011-10-20
> **Daibhi said:**
> Still at square one. The little trick I tried with the cards file didn't really do anything substantive. No freqs read in any combination of settings in Kaffiene.

You mentioned something about testing the card on your Windows install.
Any luck?

---

### Post by poe503 on 2011-10-20
I agree that the 1250 card works well with Ubuntu.  I have been using them for a number of years.  I can't tell the difference between a Mythtv recording using this card and live TV on my 50" plasma set.

Hauppauge occasionally comes out with a revised chip for this card which requires the kind of song and dance to get it to work as I describe at the beginning of this thread.

Daibhi might do well to use an older and debugged version of Ubuntu such as the LTS (long term service) version,10.04.  11.10 is hot off the press and new versions of Ubuntu tend to have many bugs that eventually get cleared up.

---

### Post by wolfen69 on 2011-10-20
> **MartyBuntu said:**
> The Hauppauge 1250 does work with Ubuntu. We just have to find out why the OP's card doesn't.

My statement was more of a general one.

---

### Post by Daibhi on 2011-10-20
The card does work in Windows, quite exceptionally. That's why I don't understand why it doesn't just mesh with Ubuntu which is the closest Linux to Windows. (or so it would seem)

---

### Post by Daibhi on 2011-10-20
That's an idea as well Poe. I may have to roll back to a previous version of Ubuntu.

---

### Post by Daibhi on 2011-10-21
Ok kiddies here's what dumbass has done so far. 

1. Wiped and installed Ubuntu 10.04.03 
2. installed Kaffiene and tried to run channels in all settings, nothing.
3. installed Me Tv ditto.

Conclusion at this point the cable box is causing some interference and cannot be bypassed. I will work with Comcast. Tech support to try and solve this issue. If anyone has comcast and is successfully working a TV card please respond!!

---

### Post by Daibhi on 2011-10-21
Oh, Poe I did run through your tutorial for my end in 10.04, I'm pretty much convinced the cable box has me buggered.

---

### Post by MartyBuntu on 2011-10-21
I wish I could help you beyond that, but my connection is coaxial cable to an ATSC OTA antenna...No experience hooking up a cable box to a Hauppauge HVR card, although I am connected to my cable service with a PVR-150 running 10.04.

Sorry. If I come up with anything else, I'll let you know.

---

### Post by ppcblaster on 2011-12-22
I followed your example and have tv on 11.10 through Me TV

What I have noticed is the tv signal is weak 0% in Ubuntu 11.10 but not in Windows 7.

I have picture and sound but get frequent pixelization

any suggestions?


During compile some of the questions had  y/M/

or y/m/n,  What is the "m" selection do?

05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
	Subsystem: Hauppauge computer works Inc. Device 2259
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: cx23885
	Kernel modules: cx23885



Thank you..

---

### Post by poe503 on 2011-12-22
The "m" option in *makeconfig* is an instruction: "Compile this feature as a module, separate from the kernel." The "y" option instructs "Compile and include this feature inside of the kernel."  See this link [http://en.wikipedia.org/wiki/Menuconfig]("http://en.wikipedia.org/wiki/Menuconfig") for more information.

The signal strength meter doesn't work at all in some of the versions of software I use.

Sorry, I don't know why your tuner works better in Windows than in Ubuntu.  Pixellation certainly indicates a weak signal source.

---

### Post by theshowmecanuck on 2012-02-02
> **MartyBuntu said:**
> You are complicating this.

**Can you receive a digital signal?**

The 1250 "works out of the box". Test it with Kaffeine or MeTV.
Believe me, they are way easier to set up than Myth.

This was the BEST advice I've seen yet. I have exactly the same card and have trying for 2 days to figure out how to get mythtv to work. With all due disrespect to the development team: **** MythTV. It is an overly complicated POS. Any time I have to search that hard to get it to work I don't want it. This was the absolutely last forum I was going to look at before putting the card back in a MS Win 7 box. I moved it because I couldn't stand the ****** hauppage software. Then I thought, man this Linux TV option just sucks ten times worse. Fortunately you had the right uncomplicated answer. Just use a program that isn't a pain in the ***. And it worked. I use over the air digital. I get a signal as good as the hauppage software. 

Thanks a great deal. 

BillR

:popcorn:

---

### Post by DJP55 on 2012-02-26
Hey everyone,
So sorry to keep adding on to an older thread, but I've been fighting with this for a week or so.  I'm running [Pinguy]("http://distrowatch.com/table.php?distribution=pinguy") which is for all intents and purposes Ubuntu 10.10.  I have the 1250 (device 2259) and I've been trying to make it work.  It does not show up at all in Kaffeine or in Myth, or anything else for that matter.  I installed Win7 to check that the card was still alive and it is.  I followed the instructions to the letter at the beginning, and i've tried every idea I've come up with.
Anyone know any other ideas why this could still not work for me?
It seems that there is some sort of driver issue, but I know there shouldn't be.  It sees the card when I list PCI, but no program will grab it.
Thanks in advance for any help,
-DJ

---

### Post by poe503 on 2012-02-27
How is the card listed in dmesg?

---

### Post by nhtrader on 2012-05-28
This seemed the best place to respond. Apologies if this isn't proper.

I too can't get HVR-1250 to work with new install of MythTV v0.25/Ubuntu 12.04. Also verified that it works on Windows.

Here's what I did to diagnose problem and don't know what to do next...
```


1. Verified TV Capture Card works on a WinXP.

2. On Mythbuntu 12.04-v0.25 Fresh Install below are the commands used for diagnostic purposes:

sudo su
dmesg|grep cx23885  (output below)
	[   16.178221] cx23885 driver version 0.0.3 loaded
	[   16.178601] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
	[   16.178785] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
	[   16.325679] cx23885[0]: hauppauge eeprom: model=22111
	[   16.368096] cx25840 2-0044: cx23888 A/V decoder found @ 0x88 (cx23885[0])
	[   17.086276] cx25840 2-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
	[   17.094833] cx23885_dvb_register() allocating 1 frontend(s)
	[   17.094838] cx23885[0]: cx23885 based dvb card
	[   17.332720] DVB: registering new adapter (cx23885[0])
	[   17.333047] cx23885_dev_checkrevision() Hardware revision = 0xd0
	[   17.333052] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
	[   17.333060] cx23885 0000:02:00.0: setting latency timer to 64
	[   17.356147] input: cx23885 IR (Hauppauge WinTV-HVR1270) as /devices/pci0000:00/0000:00:04.0/0000:02:00.0/rc/rc0/input12
	[   17.356215] rc0: cx23885 IR (Hauppauge WinTV-HVR1270) as /devices/pci0000:00/0000:00:04.0/0000:02:00.0/rc/rc0
	[   17.356285] input: MCE IR Keyboard/Mouse (cx23885) as /devices/virtual/input/input13
	[   17.356358] rc rc0: lirc_dev: driver ir-lirc-codec (cx23885) registered at minor = 0

sudo su
lspci -vvnn   (output below)
  02:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb [14f1:8880] (rev 04)
	Subsystem: Hauppauge computer works Inc. Device [0070:2211]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data
		Unknown small resource type 01, will not decode more.
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [200 v1] Virtual Channel
		Caps:	LPEVC=1 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32+ WRR64+ WRR128-
		Ctrl:	ArbSelect=WRR64
		Status:	InProgress-
		Port Arbitration Table [240] <?>
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=1 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Kernel driver in use: cx23885
	Kernel modules: cx23885

lshw -C multimedia   (output below)
       description: Multimedia video controller
       product: CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:16 memory:fd600000-fd7fffff


sudo su
lsof /dev/dvb/adapter0/frontend0   (output below)
	COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
	mythbacke 1822 mythtv   11u   CHR  212,0      0t0 8299 /dev/dvb/adapter0/frontend0
stop mythtv-backend
scan /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256   (output)
	scanning /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 73753600:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 73753600:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 55752700:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 55752700:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 61753000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 61753000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!


scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256   (output below)
	scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 57000000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 57000000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 63000000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 63000000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 69000000:QAM_256
	WARNING: >>> tuning failed!!!


scan /usr/share/dvb/atsc/us-MA-Boston   (output below)
	scanning /usr/share/dvb/atsc/us-MA-Boston
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 503000000:8VSB
	WARNING: >>> tuning failed!!!
	>>> tune to: 503000000:8VSB (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 509000000:8VSB
	WARNING: >>> tuning failed!!!
	>>> tune to: 509000000:8VSB (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 527000000:8VSB

installed w-scan (not w_scan)
sudo su
apt-get install w-scan

w_scan -ft -A 2 -t 3 -c US -X >> channels.conf     (note: command and pkg-name are different) (output below)
			(options: -ft = DVB-T,  -A 2 = cable,  -t 3 = slowest tuning timeout, -c = country, -X = output format)
	w_scan version 20111203 (compiled for DVB API 5.4)
	using settings for UNITED STATES
	ATSC
	QAM US/CA
	frontend_type ATSC, channellist 2
	output format czap/tzap/szap/xine
	WARNING: could not guess your codepage. Falling back to 'UTF-8'
	output charset 'UTF-8', use -C <charset> to override
	Info: using DVB adapter auto detection.
		/dev/dvb/adapter0/frontend0 -> ATSC "LG Electronics LGDT3305 VSB/QAM Frontend": good :-)
	Using ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
	-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
	Using DVB API 5.4
	frontend 'LG Electronics LGDT3305 VSB/QAM Frontend' supports
	INVERSION_AUTO
	8VSB
	QAM_64
	QAM_256
	FREQ (54.00MHz ... 858.00MHz)
	-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
	57000: QAM256(time: 00:00) 
	63000: QAM256(time: 00:02) 
	69000: QAM256(time: 00:05) 
	79000: QAM256(time: 00:07) 
	85000: QAM256(time: 00:10) 
	177000: QAM256(time: 00:13) 
	183000: QAM256(time: 00:15) 
	189000: QAM256(time: 00:18) 
	195000: QAM256(time: 00:20) 
	201000: QAM256(time: 00:23) 
	207000: QAM256(time: 00:26) 
	213000: QAM256(time: 00:28) 
	123000: QAM256(time: 00:31) 
	123012: QAM256(time: 00:33) 
	129000: QAM256(time: 00:36) 
	129012: QAM256(time: 00:38) 
	135000: QAM256(time: 00:41) 
	.
	.
	.
	807000: QAM256(time: 06:41) 
	813000: QAM256(time: 06:44) 
	819000: QAM256(time: 06:46) 
	825000: QAM256(time: 06:49) 
	831000: QAM256(time: 06:51) 
	837000: QAM256(time: 06:54) 
	843000: QAM256(time: 06:56) 
	849000: QAM256(time: 06:59) 
	tune to: QAM256   f=153000 kHz 
	(time: 07:02) Info: VCT(cable) filter timeout
	tune to: QAM256   f=111000 kHz 
	(time: 07:08) Info: VCT(cable) filter timeout
	tune to: QAM256   f=117000 kHz 
	(time: 07:15) Info: VCT(cable) filter timeout
	tune to: QAM256   f=693000 kHz 
	(time: 07:23) Info: VCT(cable) filter timeout
	dumping lists (7 services)
	Done.

w_scan -fc -A 2 -t 3 -c US -X >> channels.conf
	(option: -fc = DVB-c. Note this produced similiar results as with option -ft  =  no usable TV channels)
	
	.
	.
	.
	849000: QAM256(time: 06:56) 
	tune to: QAM256   f=153000 kHz 
	(time: 06:58) ----------no signal----------
	tune to: QAM256   f=153000 kHz  (no signal)
	(time: 07:01) ----------no signal----------
	tune to: QAM256   f=111000 kHz 
	(time: 07:04) ----------no signal----------
	tune to: QAM256   f=111000 kHz  (no signal)
	(time: 07:07) ----------no signal----------
	tune to: QAM256   f=117000 kHz 
	(time: 07:11) ----------no signal----------
	tune to: QAM256   f=117000 kHz  (no signal)
	(time: 07:14) ----------no signal----------
	tune to: QAM256   f=693000 kHz 
	(time: 07:17) ----------no signal----------
	tune to: QAM256   f=693000 kHz  (no signal)
	(time: 07:20) ----------no signal----------

	ERROR: Sorry - i couldn't get any working frequency/transponder
	 Nothing to scan!!


```


reviewed these URLS:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)
[http://ubuntuforums.org/showthread.php?t=1669420](http://ubuntuforums.org/showthread.php?t=1669420)
[http://ubuntuforums.org/showthread.php?t=1648472](http://ubuntuforums.org/showthread.php?t=1648472)
[http://ubuntuforums.org/showthread.php?t=1573600](http://ubuntuforums.org/showthread.php?t=1573600)
[http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada))

---

