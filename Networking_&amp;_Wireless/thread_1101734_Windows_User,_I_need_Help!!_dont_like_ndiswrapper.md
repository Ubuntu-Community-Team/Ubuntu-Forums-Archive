---
title: "Windows User, I need Help!! dont like ndiswrapper"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by HMCafe on 2009-03-20
I Really Need Help this is my first experience with Ubuntu and the forums. I've always wanted to try linux but was scared to because of it being incompatible with my wireless card . But now I installed Kubuntu 8.10 along with my Windows XP media Center edition. I'm not sure what information you need. ohh, and i dont like NdisWrapper its complicated and hurts my brain :-) I'm writing this in my Windows XP OS right now

Here's some info:

Wireless card: Broadcom 802.11g network adapter
From the properties of My Computer:

System:
   Microsoft Windows XP
   Media Center Edition
   Version 2002
   Service Pack 3

Manufactured and supported by:
Acer Inc.
AcerSystem
AMD Turion(tm) 64 Mobile
Technology MK-36
2.00 GHz, 768 MB of RAM
Physical Adress Extension

K someone please help. i'm so freakin clueless.

[email]HMCAFE@aol.com[/email] or
[email]JAHGoVeg@aol.com[/email]

---

### Post by wmatthews on 2009-03-20
Go into the terminal and type "lspci". Without the quotes.

---

### Post by HMCafe on 2009-03-25
I'll try that Wat does it do?

---

### Post by issih on 2009-03-25
The previous advice was not a fix of any type, it was an attempt to identify your wireless card, which we need to do to find out what drivers are available. Without that information nobody can help you, there is no one size fits all solution.

To that end running the following in terminal and then copying the output here would be helpful.(Note that in the terminal you can copy and paste using the mouse)

```
sudo lshw -C network
```
N.B. enter your login password and hit enter when prompted, it will not echo what you type to the screen.

This will list all the detected networking hardware in your machine and some details about it.

```
lspci
```

This will list all the devices connected to the pci bus of the computer

```
lsusb
```

This will list all the devices connected to the usb bus

Hopefully from one of those we will be able to accurately determine your wireless chipset and go from there.

---

### Post by HMCafe on 2009-03-27
Ok I will Paste the information here. sorry, i always have to reboot before i can go into linux

---

### Post by HMCafe on 2009-03-27
:KS

Here are my outputs for the codes
hopefully someone can help me. I'm not very good at this but i really wanted to give Linux an honest try.


Code:
sudo lshw -C network

OUTPUT: *-network:0                      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2                         
       bus info: pci@0000:08:02.0             
       logical name: eth0                     
       version: 10                            
       serial: 00:16:36:9a:7f:bd              
       size: 10MB/s                           
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:98:ee:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:9f:0a:a8:b5:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



Code:
lspci

OUTPUT:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)            
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)                                                                            
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridg00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)            
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge                       
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)                                                                            
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)e: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Code:
lsusb

OUTPUT:Bus 003 Device 006: ID 13fe:3123 Kingston Technology Company Inc.
Bus 003 Device 005: ID 043d:00ba Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 004: ID 15d9:0a33
Bus 003 Device 002: ID 058f:6254 Alcor Micro Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by HMCafe on 2009-03-27
Ok Whats Up? There has been like 104 VIEWS ON MY POST BUT only TWO gracious, kind  people have bothered to help me? What is wrong?

---

### Post by rshnike on 2009-03-27
> **HMCafe said:**
> Ok Whats Up? There has been like 104 VIEWS ON MY POST BUT only TWO gracious, kind  people have bothered to help me? What is wrong?

Don't get discouraged. If I've learned anything in the couple of years that I've started dipping into Linux it's that it's a process.

Now then,

this here is your wireless card:

[QUOTE=HMCafe]08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/QUOTE]


There's a lot of material here on the forums about this specific card.

Check this thread: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

Start at the top, things will be slightly different in KDE (kubuntu) but see if your card shows up in Hardware Drivers. Let us know.

Good luck.

---

### Post by HMCafe on 2009-03-27
Thank you SO much! I'll look at it. But dont stop replying people i will probably still need help

---

### Post by Bucky Ball on 2009-03-27
First, plug in an ethernet cable so you can get online in Ubuntu. You will get a heap of updates, accept them, shortly thereafter your wireless card should be taken care of automatically by the system. So, all you really have to do is get online, Ubuntu 8.10 will do the rest. If not (and that eventuality would be extremely odd as the Broadcom cards are dealt with since 8.04), try this:

Go to System->Administration->Synaptic package manager

Do a search for 

ubuntu-restricted-extras

Tick the box and 'Apply' (install)

ndiswrapper has been pretty much superseded for broadcom cards anyhow, the b43 and b43-fwcutter are the go for newer broadcom cards. Good luck and let us know how you go. And yeah, my posts rarely get answered and I end up solving myself, usually takes about a week, sooner if I'm lucky. Because I have 1500 posts up, maybe people think I am a guru! Like a lot of people on here, I know a lot about a small amount, some about most things, and absolutely nothing about the rest! :0)

* Update: This might get you going, second post:

[http://ubuntuforums.org/showthread.php?t=881903&page=2](http://ubuntuforums.org/showthread.php?t=881903&page=2)

* Tip: If you have a problem, do a search for the problem and end it in Kubuntu. I found that page with:

'Broadcom Corporation BCM4318 ubuntu'

... in a search engine. Don't worry the instruction is for Ubuntu. They're all Ubuntu with a different desktop manager. KDE for Kubuntu, Xfce for Xubuntu (my favourite) and Gnome for straight Ubuntu. If you want to try any of the others you can simply install them using Synaptics Package Manager (instructions above), then log out, choose 'Sessions' at the login screen, choose 'Xfce' or Gnome or whatever you've installed and put your details in and voila, you will now be using Xfce or Gnome instead of KDE, but all your software remains the same (programs etc). I have a straight Ubuntu install but have loaded Xfce, Openbox, Ice and a couple of others so I have a choice of environments at login (I am in an Xfce mood 98% of the time, though). Welcome to the forums and Linux, hope you have fun and grow to love it as much as many of us here do ... :)

---

### Post by HMCafe on 2009-03-27
> **HMCafe said:**
>  But now I installed Kubuntu 8.10 along with my Windows XP media Center edition.

This is to answer bucky ball as to what os I'm running

---

### Post by Bucky Ball on 2009-03-27
Got ya. Plug in an ethernet cable and that should be it. I have edited my last post, read the beginning again. :)

---

### Post by HMCafe on 2009-03-27
you see but the thing is i don't have any other internet connection but wireless. we canceled it. I know it was stupid.

---

### Post by Bucky Ball on 2009-03-27
Ah, ha. The plot thickens and now it does get a little tricky, but maybe not. You need to research whether the b43/b43-fwcutter is on the install disk. Have you got a friend with an ethernet connection (I am presuming you are using a laptop but could be totally wrong). You may be able to download and save to a drive accessible by Ubuntu, then boot into Ubuntu and install.

It is realllll late here and I better hit the sack, but that is the what you want, forget about ndiswrapper. As I say, you shouldn't need to do anything to install that card apart from press a few buttons and read the screen. Make sure you have the details for your access point (name and security key, if there is one) which you will be able to find from your windows setup. Good luck and I'll check your progress in the morning. Shite, it almost is morning! zzzzzzzzzzzz

Here's a start:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by HMCafe on 2009-03-27
no they are not preinstalled :-(

---

### Post by HMCafe on 2009-03-27
anyone have a different approach?

---

### Post by issih on 2009-03-27
Are you 100% sure that your router does not have any normal ethernet ports on it? It certainly is physically possible to make one without them, but I have never seen such a thing, they pretty much all have some hardline ports. Go and check, and if there is a port, connect up to it, it will make your life a huge amount simpler.

---

### Post by Bucky Ball on 2009-03-28
I didn't say pre-installed, I said on the Live install disk that you installed Ubuntu with. 

HMCafe, any other approach is going to be harder (as issih has re-stated), and besides, there isn't really any other approach. I advise you get a hard wire ethernet cable into that machine from somewhere and "make your life a huge amount simpler", or download the appropriate packages using windows onto a cd then install them in Ubuntu.

Not sure what you are missing here but I will say it one more time:

b43-fwcutter is the driver used for these cards now. Ndiswrapper has been superceded for Broadcom cards by the b43 driver.

Take a look at my computer specs below, I am using a broadcom on the laptop and couldn't get it up in 4 months with ndiswrapper. I got rid of 7.04 and installed 8.04 and was up in less than 5 minutes. So get on a hardwire and you are done. 

And yes, I would be surprised if there is not ethernet ports on your router. Look again cos if you get online, your problems will be solved very easily. Or, you can go ahead and look for a more difficult way of doing this if you wish, but I don't like your chances and hope you have plenty of time on your hands. May be just knuckle down and sort this out the easiest way. I've told you how to do it, for some reason you're not hearing me. :) ?

Go to this page:

[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

Go to the section called:

'Directly downloading the tarball'

... and click on the hyperlink:

[the compat-wireless-2.6 archive]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/")

It is all there in black and white. Good luck with it. Maybe someone else can give you a step by step if you need it from there. :)

---

### Post by issih on 2009-03-28
As I understand things its the firmware file that is required to be downloaded, which is what the b43fwcutter program does.

Anyway, the appropriate debs ARE on the install cd rom and this guide:

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

will take you step by step through what to do to install them from there, and will then tell you how to download and extract the firmware that is needed.

Still easier if you can plug the computer in to an ethernet port, but at least it can be done.

Hope that helps.

---

### Post by Bucky Ball on 2009-03-28
Double that. Nice work issih. And again, good luck with it. Should be reasonably straightforward if *all* the required software is on the CD. :)

---

### Post by HMCafe on 2009-04-07
Thank you guys so much!!!!!!

---

### Post by Bucky Ball on 2009-04-08
Pleasure. Success!

---

