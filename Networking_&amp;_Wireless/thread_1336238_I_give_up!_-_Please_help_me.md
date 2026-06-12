---
title: "I give up! - Please help me"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by zootoxin on 2009-11-24
Hi guys, 

I have searched and tried, tried and searched to solve these problem and nothing I try seems to work. 

Please help me to get my old laptop working in my work enviroment (windows) and correct my resolution.

I have a Dell Inspiron 500m with Juanty installed. 

**Network **is run through a proxy that I have no control over but I know some things about.
(the details are changed to protect the innocent) 

I can get onto Firefox by setting manual proxy to 
HTTP: Pang
PORT: 7070
Username: t.ball
Password: bouncy

but I can not for the life of me get the update manager to work. 

**What I have tried**
Lets say to Domain name specified on _my offical windows work computer name section_ is _blag _and my computer name is set too 00001.

I have tried adding all the information I know to [U]network tab in synaptic manager. 
proxy tools
[/U]and anywhere else I could find to stick it! (in various combinations)
I have tried the NTLMAPS tutorial but that didnt work either. 

Am I missing something? 
Information? Knowledge? 

Can somebody guide me through the process please? 

Next..................
**Resolution**

Can't get above 1024x724 and it looks horrible and makes it difficult to use the laptop. 

[B]What I have tried
[/B]
Adding the mode line to xorg.conf 
Adding extra resolutions to compiz 
pulling really hard at both screen edges 
jumping up and down screaming momma! 
I am sure this must be easier, why would it not be? 


Please please please can some nice person help me. 

and if you don't like begging

Sir, would you kindly show me the way through these problems with guidence and a kind heart.

Thanks 

Zoot

---

### Post by ghostborg on 2009-11-24
If you installed your graphics driver through System=>Administration=>Hardware Drivers the Nvidia Config should be available somewhere in your menus. As for ATI I think you need to install the ATI Catalyst Control Center from the ATI website and follow their directions.

The easiest way to make sure Samba is installed properly is to pick a folder to share, right click on it=> Sharing Options, and it should tell you that it needs to install files.

---

### Post by zootoxin on 2009-11-25
> **ghostborg said:**
> If you installed your graphics driver through System=>Administration=>Hardware Drivers the Nvidia Config should be available somewhere in your menus. As for ATI I think you need to install the ATI Catalyst Control Center from the ATI website and follow their directions.

The easiest way to make sure Samba is installed properly is to pick a folder to share, right click on it=> Sharing Options, and it should tell you that it needs to install files.

I can't install samba because the synaptic manager doesn't work mate. :(

---

### Post by zootoxin on 2009-11-29
I have tried looking at the Hardware drivers part, but it states the are no drivers for my system. 

there must be a way to get the resolution correct??

---

### Post by t.rei on 2009-11-29
you dont need the synaptic manager to install anything: all you need is a commandline:

```
sudo apt-get update
```will update the package information and get the new info from the servers in you /etc/apt/sources.list

```
sudo apt-get upgrade
```Will install any upgrade to the software that - to put it simple - will not remove anything to resolve dependencies.

```
sudo apt-get dist-upgrade
```This does an upgrade like the forementioned, but will also resolve dependencies and install most of what was "held back" in the one above.

```
apt-cache search whatIamLookingFor
```will search for anything available containgin "chatIamLookingFor"

```
sudo apt-get install whatIwantToInstall
```will install the package "whatIwantToInstall"

```
sudo apt-get install samba
```as an example would install the package called "samba" and everything this package needs (aka dependencies)

As for the resolution issue:
If you could provide us with the info on what graphics card you are using, we might be more helpfull at the basic problem of your screens resolution.
As a hint: once again on terminal: ```
lspci
``` or ```
lshw
``` should give you some line containing info on your graphics card/adapter that could be helpfull here.

---

### Post by zootoxin on 2009-11-29
Thanks the samba installed fine

LSPCI

darren@old-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
darren@old-laptop:~$ 

LSHW

*-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0



I hope this can help you help me

thanks

---

### Post by opt1k on 2009-11-29
Hi zootoxin,
Im sorry to hear about your troubles and it looks like the replies are less than helpful.
Try the console method for adding a proxy for apt at this URL

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

It looks like it will work for you.

Edit your /etc/bash.bashrc file as root.
so from the terminal type 
sudo gedit /etc/bash.bashrc
Put these line at the end of your /etc/bash.bashrc file :
export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

It appears that you would use [http://t.ball:bouncy@pang:7070](http://t.ball:bouncy@pang:7070)

Then log out and back in and it "SHOULD" work

I would also recommend reading the documentation here since ubuntu is for all intensive purposes debian.  Their documentation is usually much more complete. 
[http://www.debian.org/doc/](http://www.debian.org/doc/)
Good luck!
> **zootoxin said:**
> Hi guys, 

I have searched and tried, tried and searched to solve these problem and nothing I try seems to work. 

Please help me to get my old laptop working in my work enviroment (windows) and correct my resolution.

I have a Dell Inspiron 500m with Juanty installed. 

**Network **is run through a proxy that I have no control over but I know some things about.
(the details are changed to protect the innocent) 

I can get onto Firefox by setting manual proxy to 
HTTP: Pang
PORT: 7070
Username: t.ball
Password: bouncy

but I can not for the life of me get the update manager to work. 

**What I have tried**
Lets say to Domain name specified on _my offical windows work computer name section_ is _blag _and my computer name is set too 00001.

I have tried adding all the information I know to [U]network tab in synaptic manager. 
proxy tools
[/U]and anywhere else I could find to stick it! (in various combinations)
I have tried the NTLMAPS tutorial but that didnt work either. 

Am I missing something? 
Information? Knowledge? 

Can somebody guide me through the process please? 

Next..................
**Resolution**

Can't get above 1024x724 and it looks horrible and makes it difficult to use the laptop. 

[B]What I have tried
[/B]
Adding the mode line to xorg.conf 
Adding extra resolutions to compiz 
pulling really hard at both screen edges 
jumping up and down screaming momma! 
I am sure this must be easier, why would it not be? 


Please please please can some nice person help me. 

and if you don't like begging

Sir, would you kindly show me the way through these problems with guidence and a kind heart.

Thanks 

Zoot

---

### Post by frankwakeman on 2009-11-29
Maybe post your xorg.conf here too.

---

### Post by opt1k on 2009-11-29
I dug up this information for you that might help with your graphics issues.
[http://divby0.blogspot.com/2008/09/915resolution-xorgconf-intel-82852855gm.html](http://divby0.blogspot.com/2008/09/915resolution-xorgconf-intel-82852855gm.html)
it appears that you should be using the i810 driver in your xorg.conf
chances are you are using an Xvesa or fbdev driver.

---

### Post by zootoxin on 2009-12-01
Got the sharing working fine now thanks.
but
The resolution thing is driving me nuts! 

I was going to edit my xorg.conf

```
sudo gedit etc/x11/xorg.conf
```

But its completely blank!! 

I can't believe it can be this hard to correct resolution, I must be doing something simple wrong

Any ideas?

---

### Post by bkratz on 2009-12-01
> **zootoxin said:**
> Got the sharing working fine now thanks.
but
The resolution thing is driving me nuts! 

I was going to edit my xorg.conf

```
sudo gedit etc/x11/xorg.conf
```

But its completely blank!! 

I can't believe it can be this hard to correct resolution, I must be doing something simple wrong

Any ideas?



This will help you

[http://ubuntuforums.org/showthread.php?t=1174702&highlight=xorg](http://ubuntuforums.org/showthread.php?t=1174702&highlight=xorg)

---

### Post by zootoxin on 2009-12-01
Strange when I browse to the location the xorg is ok, but I edit from terminal its blank!!

---

### Post by bkratz on 2009-12-01
> **zootoxin said:**
> Strange when I browse to the location the xorg is ok, but I edit from terminal its blank!!



Did you capitalize the X? It is case sensitive

---

### Post by zootoxin on 2009-12-02
I think the problem is my xorg.conf is like below???

I have tried about 15 tutorials now from apt-get install xserver-xorg-video-intel to all the ones on here.

I can do the 915resolution fix because its not in the synaptec. 

please help

sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by zootoxin on 2009-12-03
I heard on the grapevine that the next version of ubuntu will have a fix for the intel problem. 

So fingers cross until then eh

---

