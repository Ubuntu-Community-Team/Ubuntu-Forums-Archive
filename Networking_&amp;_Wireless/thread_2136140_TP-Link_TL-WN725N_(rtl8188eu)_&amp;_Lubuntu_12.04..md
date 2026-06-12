---
title: "TP-Link TL-WN725N (rtl8188eu?) &amp; Lubuntu 12.04.2"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by tpprynn on 2013-04-16
Hello. I've had this tiny usb wireless dongle turn up this morning but as yet I have no wireless. If I type lsusb the dongle seems to be seen:

Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp.

I upgraded the kernel to 3.7.8 a little while ago too this afternoon with no change. I've googled for a few hours and tried to copy what some have done to the best of my knowledge but compiling (drivers from the Realtek site) and so on aren't things I've become fluent with. I installed build-essential and checkinstall but saw mention of errors in the output, for whatever reason. I'd rather not bother with compiling if I can help it. At least one person had this working out of the box with 12.04.

Is Lubuntu/LXDE part of the problem, for any reason similar to why it's a problem if you want hotkeys to work with it on a laptop (this current machine is a desktop pc however)?

I tried sudo modprobe rtl8192su to no avail. Other modules like rtl8818su and rtl8818cus were not found (it didn't seem consistent during googling what chip this dongle uses. Is there a terminal command to ascertain this?

What's next? My next stab if there are no replies is ndiswrapper but that seems a mess. After that I'll try and use it with my other Windows 7 computer and move the ethernet cable it uses to my Lubunutu machine which at least will work if the dongle is a good and reliable one. The Lubuntu machine is five feet from the router though instead of twelve and I like the consistency of ethernet with the computer furthest away. Do I need to blacklist or un-blacklist anything? I can't remember where these files are as well...

I've tried several of the pc's usb slots with no change.

Many thanks for any help, particularly from the fella with the medic avatar who was always good in the past!

(I also have an EDUP pcmcia card that I've tried to use with a Thinkpad T22 to no avail, with Lubuntu and Debian, it too is seen by lsusb's evidence, but the TP-Link dongle help is the priority for now.)

---

### Post by chili555 on 2013-04-16
> Many thanks for any help, particularly from the fella with the medic avatar who was always good in the past!MEDIC!! > Is Lubuntu/LXDE part of the problem,Very doubtful.> (it didn't seem consistent during googling what chip this dongle uses. Is there a terminal command to ascertain this?Google is what I use, looking for the device ID, in this case 0bda:8179. Google finds the generally reliable site here: [http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2) 

You'll see it refers to the correct ID and says:> **Linux driver**
probably not, at least, not yetIf you check the aliases for the various rtl8192xx drivers, your device ID is not found. ```
modinfo rtl8192pick_one
```

It seems that the always messy ndiswrapper is an option as is returning the device and buying another. We could also experiment with this process: [http://www.raspberrypi.org/phpBB3/viewtopic.php?t=29752&p=314656](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=29752&p=314656)

Do you want to be a pioneer and pave new ground or do you want to get a new device and get some work done? I am happy to help in either case.

---

### Post by chili555 on 2013-04-16
Further data: from netrtwlanu.inf:> ;; For 8188E RTK common		================================================================
%RTL8188eu.DeviceDesc%  			= RTL8188eu.ndi, 	USB\VID_[COLOR="#FF0000"]0BDA[/COLOR]&PID_[COLOR="#FF0000"]8179[/COLOR]
%RTL8188eu.DeviceDesc%  			= RTL8188eu.ndi, 	USB\VID_0BDA&PID_8179&REV_0200&SS
%RTL8188ee_vau.DeviceDesc%  		= RTL8188eu.ndi, 	USB\VID_0BDA&PID_A179
%RTL8188ee_vau.DeviceDesc%  		= RTL8188eu.ndi, 	USB\VID_0BDA&PID_A179&REV_0200&SSSo, maybe???

---

### Post by tpprynn on 2013-04-16
That's promising. I may have the renewed energy tomrrow for this (2.10 a.m. here and I've put the dongle in the Windows machine partly to be sure it isn't plain dead but also with dodgy nerves after ten hours of faffing). It's getting five bars but may have disconnected once. Tomorrow or the day after I actually have a Raspberry pi arriving myself - maybe Raspbian will let me check the filesystem for clues too? But yes I'll try that procedure on the other page linked, which I had found but which felt clear as mud at the time.

Are build-essential and checkinstall all I need to have added for compiling? Are the compiling tasks on Ubuntu using sudo or su? (I was getting authentication errors when I tried ot use su but there was an install.sh file that seemed to create errors, myfault or otherwise.) Bit rusty with this side of things but willing to have a go especially if the further away Windows pc keeps cutting out. Quite impressive thing though considering its size and lack of usual visible aerial.

More later, thanks.

---

### Post by chili555 on 2013-04-16
You will need build-essential and linux-headers-generic, both of which will install several dependencies. You will also need git. The rough process in Ubuntu is:```
sudo apt-get install build-essential linux-headers-generic
cd Driver_file/containing_makefile
make 
```And assuming there are no errors:
```
sudo make install
```I have plenty of doubts about the process I linked; it seems to be Pi-oriented. There are plenty of references to the ARM processor. Try it and let's see what happens. I generally try these myself but I'm even more skeptical that it works on my 3.8.0-xx kernel.

It looks like you need to precede 'make' with:```
make oldconfig
``` I simply accepted the default choices. I assume 'make' will create, among other things, 8188eu.ko. You can probably test with:```
sudo insmod /path/to/8188eu.ko
```See if a wireless interface was created, ideally wlan0:```
iwconfig
```If so, Network manager should take over, ask for the password and connect. If everything goes smoothly, then:```
sudo make install
```

---

### Post by tpprynn on 2013-04-17
No sign of 8188eu.ko unfortunately and iwconfig yields no change, and maybe this is because it's not an arm machine as it seems you predicted would be the case? There were very many things to okay during the make install thing seemingly often referring to other devices - does this or can this be undone now that I think I may have to try the dongle several months later in the hope a driver is around? 

Has that install which presumably installed settings possibly caused other potential problems or would its settings be confined to this attempt at making 8188eu.ko?

I'm tempted to battle away at ndiswrapper again but ndiswrapper seems generally broken now? I've seen references to pages of compiling and faffing that doesn't sound fun. Ndiswrapper just didn't want to know any of the drivers on the disc that I fed into it yesterday, they were invalid or the device was 'not found'. I had all the ndiswrapper extras installed. (I'm reminded of xcompmgr, which I'd used with the LXDE desktop - the current version is broken but sits there in the repository when I have learnt this morning that a deb file of a previous version installs without gripes and works. Sigh... Why not keep hold of the working versions in the repository.)

Ideally I would use ethernet with the Windows 7 pc and this dongle with the Lubuntu machine because of their positions from the router. If there is something else to try that's less of a headache than ndiswrapper I'm all ears, but if you think it's a bit doomed at the moment as an endeavour I'll leave it. At a guess there is a TP-Link dongle with an Ubuntu-friendly chip that I could have got for the same money if I'd known how to ascertain this - do you have or know of a list? I did have one that worked, the larger dongle type with aerial, but it died a couple of months ago.

If the above can't go further yet, would you be able to steer me a bit with the pcmcia EDUP wireless card I've tried in the Thinkpad T22? I'd seemed to find that it uses module b43 or b43legacy but didn't achieve results with it in fact the T22 wouldn't finish booting when I added b43 or b43legacy to /etc/modules). bcmwl5.inf is on the disc of Windows drivers I see.

Thanks.

---

### Post by chili555 on 2013-04-17
> Has that install which presumably installed settings possibly caused other potential problems or would its settings be confined to this attempt at making 8188eu.ko?As long as you only got to 'make' nothing ever left the folder you were working in. Even if you did try 'sudo make install', you can always reverse it with 'sudo make uninstall'.

The compiled from source ndiswrapper-1.58 works pretty well, actually. Are there Windows XP files on the disk? That's what ndiswrapper requires. Also, ndiswrapper works less well on 64-bit than 32. Which do you have?```
arch
```If you'd like to compile ndiswrapper, I suggest you start here: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981)

As I implied above, I probably have the XP files you need. I need to know 32- or 64-bit, however.

---

### Post by tpprynn on 2013-04-17
Whoops, I did get that far with sudo make install and have since shut that terminal, I didn't think you'd be around for a few hours. (At a guess I can't make uninstall cleanly now?) If anything behaves strange I'll just reinstall Lubuntu, I may anyway as I've been a bit too experimental this week in various ways with DEs.

Yes I had got into the habit of using XP drivers with ndiswrapper and this is 32 bit. I'll look at that link now, thanks.

---

### Post by chili555 on 2013-04-17
> At a guess I can't make uninstall cleanly now?You sure can. Simply cd to the relevant directory, the one with Makefile, and go ahead.  

Which file came on the disc? netrtwlanu.inf and its associated .sys file(s) by chance? The 32-bit files may be in a folder labeled WinXP and the 64-bit in WinX64. In order to use the files, I suggest you copy the WinXP folder from the (read only) disc to your desktop and then, approximately:```
cd Desktop/WinXP
sudo ndiswwrapper -i whatever.inf
ndiswrapper -l
```That's L for list and it will tell you if the files are valid, et al. Then do:```
sudo modprobe ndiswrapper
iwconfig
```If all has gone perfectly, you will have a wireless interface wlan0 and Network Manager will spring to life and offer to connect.

Mrs. Chili has informed me that I am taking her to lunch, so I'll check back later.

---

### Post by tpprynn on 2013-04-17
Big progress, must be nearly there.

netrtwlanu.inf is the Windows driver, yes.

My first attempt to compile seemed to work, no gripes on the screen, but there was no result, no wireless seen. I did in the end reinstall Lubuntu, preserving /home and so on, and first tried to compile ndiswrapper with the 3.2 kernel, which failed. I installed 3.8.8 and now... the wireless is seen. My network and just one other. I put the right password in but it's not connecting. I did try changing WPA and WEP and back but doesn't Network Manager identify the right type anyway? After forty seconds or so of the connecting animation the password prompt comes up again. I'm not mistyping anything.

In the meantime I'll try the same on the Thinkpad and google a bit but hopefully you'll know what the last step is. (Will ndiswrapper always start now by the way? I don't need to add it to /etc/modules?)

Don't know if this is of use:

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:81 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks.

---

### Post by chili555 on 2013-04-17
> Will ndiswrapper always start now by the way? I don't need to add it to /etc/modulesIt certainly can't hurt.> Don't know if this is of use:

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
[COLOR="#FF0000"]Bit Rate:81 Mb/s[/COLOR] Tx-Power:20 dBm Sensitivity=0/3
RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0I think it does help! Would you please temporarily turn off N speeds in the router and try again?> doesn't Network Manager identify the right type anyway? Usually, yes.

Please stick the PCMCIA in the slot and run and post:```
sudo lspcmcia ident
```We are interested in the device ID for the ?Broadcom?. It probably will be in the form of 14e4:4999 or some such. If it's really a Broadcom, it should be easy to get going.

---

### Post by tpprynn on 2013-04-17
Lubuntu is now wireless, although on the first reboot I lost it. I've connected the dongle with a lead now and have many more networks visible although maybe that was the turning off of N speeds? I gather you mean where I had a choice under the category WLAN for B/N/G. B/G and so on I needed to save the router's settings with one that didn't include N. That's what I did anyway. The speed is what it was, an above average for around here 6meg. It hasn't dropped anyway.

I'll boot once more and continue tomorrow.

---

### Post by chili555 on 2013-04-17
Great news! > although on the first reboot I lost it.Did you add ndiswrapper to /etc/modules?> I gather you mean where I had a choice under the category WLAN for B/N/G. B/G and so on I needed to save the router's settings with one that didn't include N.Exactly.

This is a relatively new device and, as you've seen from Google, there is almost no information about how to get it going. I suggest you add details about the name of the .inf file and also edit the title of the thread from: TP-Link TL-WN725N (rtl8818cus?) & Lubuntu 12.04.2 to [SOLVED]TP-Link TL-WN725N (rtl8818cus?) & Lubuntu 12.04.2. The searchers will have an easier time finding it then.

Glad it's working.

---

### Post by tpprynn on 2013-04-17
I jumped the gun, but tonight we've got a lot of strong wind here so the conditions aren't the best for getting a clear view (although ethernet's going fine and the wind isn't inside!). I'll certainly amend the subject line when I can, I always do, and will add a few details in earlier posts to be useful.

For the T22 laptop I only get this for lspcmcia ident:

lspcmcia ident

Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.0)

Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.1)

but this is at the end of lspci:

06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I'm going to spend an hour or so on the Thinkpad doing the compiling and other jiggery pokery again now but hopefully there'll be more progress tomorrow.

Thanks so far.

---

### Post by chili555 on 2013-04-17
> but this is at the end of lspci:

06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)May we see the lspci *-nn* for this device? I think it's pretty simple; i.e. no ndiswrapper or compiling needed!

---

### Post by tpprynn on 2013-04-17
06:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

That's good news about not needing ndiswrapper as weird stuff just happened, the 3.8.8 kernel was full of errors and ndiswrapper isn't found after compiling. Anyway I need a break. Thanks for your help today and I look forward to the magical resolution tomorrow.

---

### Post by tpprynn on 2013-04-18
Weirdly this morning wireless via the pcmcia card in the Thinkpad is working. I don't know what I did... I removed the 3.8.8 kernel because some error messages that came up during installation bugged me, though the machine booted with that kernel. I happened to catch sight of the side of the laptop and noticed the card's light for once, inspected Network Manager and saw the good news. But will it be there on reboot...

Yes, it has survived both a reboot and a boot from shutdown. What might have happened, and is there a command I can type to find out what driver is being used, in case I ever need to reinstall before this 13-year-old machine is dead? Over to the Lubuntu PC now before my Raspberry Pi bits arrive and get my attention.

---

### Post by chili555 on 2013-04-18
I'm quite sure it uses b43 and required firmware. Please check:```
sudo lshw -C network
```The usual reason these devices don't work outa da box is that the firmware is proprietary and isn't shipped with the GPL-ed open source default Ubuntu install. Once the firmware is in place, it ought to run just fine regardless of kernel version. Very rarely, the driver doesn't load automagically on boot and needs to be nudged in /etc/modules.

Here is a sample lshw from my machine for comparison, although I have no Broadcom:```
*-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="#FF0000"]wlan0[/COLOR]
       version: 35
       serial: xx:94:6b:99:55:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=iwlwifi[/COLOR] driverversion=3.8.0-18-generic [COLOR="#FF0000"]firmware=9.221.4.1 build 25532[/COLOR] ip=192.168.1.120 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:f2400000-f2401fff
```

---

### Post by Rutrus on 2013-07-05
Thanks!! This work for me. I tried to compile different drivers with errors.
I have [TL-WN723N v3]("http://wikidevi.com/wiki/TP-LINK_TL-WN723N_v3") and I also need 8188eu mod (versions 1 and 2 need different drivers)
I downloaded [this driver]("https://codeload.github.com/lwfinger/rtl8188eu/zip/master"), and I could compile OK. I use Linux Mint 15 (based on Ubuntu 13.04).

Before this, I waste my time compiling other drivers with errors. Even when I put my USB-wifi, my pc froze until I installed these drivers.

---

### Post by hyattjon on 2013-07-11
Thank you, the last post links gave me the correct driver (rtl8188eu-master.zip) and it works very easily after weeks of annoyance with broken/incorrect drivers. 

Simple "make" and "sudo insmod 8188eu.ko" had it up in the network manager instantly.

---

### Post by dongcalmada on 2013-09-09
Yes, this worked for me, too. My box is Ubuntu 12.04 with kernel 3.5.0. 

Thanks a lot.

> **hyattjon said:**
> Thank you, the last post links gave me the correct driver (rtl8188eu-master.zip) and it works very easily after weeks of annoyance with broken/incorrect drivers. 

Simple "make" and "sudo insmod 8188eu.ko" had it up in the network manager instantly.

---

