---
title: "Ubuntu 9.10 mobile broadband can't connect"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by alexfish on 2009-11-19
[B][SIZE=2][COLOR=Red]Thread no longer maintained (iinks may fail) [COLOR=Black]{as of [/COLOR][COLOR=Black]18 july 2010}[/COLOR][/COLOR]

Problems Getting Connected[/SIZE][/B] 
 
most of what you see is now here

[COLOR=#980101]**[ubuntu]**[/COLOR] [How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")


RE: USB MOBILE BROADBAND DONGLES

[LIST]
[*][SIZE=2]First see if your dongle is an  OPTION DEVICE  it may work out of the box 
[/SIZE]
[*][SIZE=2]Use the Network Manager make new Connection Wizard[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]Not an Option Device Then the usb_modeswitch may help[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]To find your device Id from the Terminal try this Code: lsusb[/SIZE]
[*][SIZE=2][Finding and Monitoring Devices and Connections - System  Logs]("http://www.pcurtis.com/ubuntu-mobile.htm#connection_monitoring")[/SIZE]
[*][SIZE=2]
[/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]Check out the the Known [/SIZE][[SIZE=2]Known     working hardware[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#hardware")
[/LIST]

[LIST]
[*][SIZE=2]If it is listed then you may get it working with the usb modeswitch[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]Some devices configure with the eject or safely remove command : ejecting a second time may cause a reset , so the device will have to be reconfigured :BE CAREFUL[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]HsoConnect  :also try a search on this forum with this title 
[/SIZE]
[*] [SIZE=2][Re: Option iCON 515m wireless USB modem (Orange)Hsoconnect]("http://ubuntuforums.org/showthread.php?t=1351612")[/SIZE]
[*][SIZE=2]Pharscape Forum [http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]Usb ModeSwitch Latest     debian Package (1.1.3-1) 
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]The USB MODE_SWITCH may work with other versions of Ubuntu [/SIZE]Please Check The Ubuntu [Version] [Details of package] Site
[*][SIZE=2][COLOR=Red]Every Thing I have tried Failed[/COLOR] : Search the forums with your Model version :[/SIZE][SIZE=2] Consider Posting a new thread if your searches fail[/SIZE][SIZE=2] : Quoting the Model , and the Problem :also post a listing of the device obtained from the     lsusb   command  [ this is done from the terminal  ] ; provide as much info as possible ; Someone with experience of the Device may spot the Thread[/SIZE]
[*][SIZE=2]**[COLOR=Red]( Most ISP's or Retailers now implement a money back guarantee , check this out and also the time limit , also check to see if it is Linux compatible) [/COLOR]**
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]APN Network Settings This site is worth checking out : also Ideal for IPv4 setting { setting to Automatic (PPP) addresses only } this usually cures the Network Manager and Browser issues[/SIZE]
[*][SIZE=2]ignore the name on the index ! But the site does help
[/SIZE]
[*]                                  [SIZE=2][http://modmyi.com/wiki/index.php/Carrier_APN_Settings](http://modmyi.com/wiki/index.php/Carrier_APN_Settings)[/SIZE]
[/LIST]


 [SIZE=2]**USB_ModeSwitch - Activating Switchable USB Devices on Linux**[/SIZE]
 
[LIST]
[*][[SIZE=2]Introduction[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#intro")
[*][[SIZE=2]Download[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#download")
[*][[SIZE=2]How     to install[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#install")
[*][[SIZE=2]How     to use and to automate[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#automate")
[*][[SIZE=2]Known     working hardware[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#hardware")
[*][[SIZE=2]Troubleshooting[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#trouble")
[*][[SIZE=2]Contribute[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#contrib")
[*][[SIZE=2]Whodunit[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#whodunit")
[*][[SIZE=2]History[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/#history")
[/LIST]
 

The latest release version is **1.1.3**. The tar archive contains  only the source. I used libusb-0.1.12 but the "compat" library from  libusb-1.0 is now working smoothly too.
**Important:** you need  the data package as well !!
Changes and updates to the configuration  data may happen more often than new releases; most of the valuable  knowledge about devices is contained in these files. That's why it is  provided separately.

[LIST]
[*]Download [usb-modeswitch-1.1.3.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.3.tar.bz2"),  dated from 2010-06-21; a Debian (Xandros/Ubuntu) package should be  available soon at the [Debian Repository]("http://packages.debian.org/usb-modeswitch").  Many architectures are supported there (like amd64 or ia64).
[*]Download  the [usb-modeswitch-data]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100707.tar.bz2")  package (2010-07-07). It contains the device database and the rules  file, including full paths. You can use this package with program  releases from 1.0.3 upward, but the latest devices and features may  require the most recent program release too.
[*]The optional [device_reference.txt]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt.gz")  (gzipped) from 2010-07-07; this is a collection of all device setups  with their respective contributors; you can use it as a starting point  if you want to make a new device working.
[*]Don't forget [libusb]("http://libusb.wiki.sourceforge.net/") if it's not on  your system. In most distributions there is most likely a package named  "libusb-dev" or "libusb-devel". Choose the legacy version (0.1.12) or  the "compatible" package from libusb-1.0; last time I checked it had the  version number 0.1.13.
[/LIST]

[COLOR=White]................[/COLOR]*************************************************************************************************************************************************

[SIZE=2]If you are                            experiencing Problems With the Network Manager   ..Set up with the wizard .. This Will help with some of the details .. THEN Try Using Gnome ppp this is a front end to wvdial . 

[/SIZE]( Orange Icon series can't resolve named servers )[SIZE=2]consider Installing  resolvconf[/SIZE]  { Note this software may want to remove Gnome ppp . Plus need Manual configs }. [SIZE=2]

Other Named resolutions problems [/SIZE]IE MY MODEM SEEMS CONNECT AND THE BROWSER DOES NOT WORK  ,SEE Post #23 it may help


[SIZE=2]Sakis3G  This Method is also worth trying[/SIZE] . ([SIZE=2]Will also detect[/SIZE] [SIZE=2]if you are KDE so may be of use if experiencing problems here ) ......[/SIZE]{ Read the Two Links thoroughly before hand } { Also has usb_modeswitch and will implement if the modem has not switched from storage mode.a + couple of fixes for zte devices ,also probes the modem ports so may be a better tool if you have problematic devices IE : multiple ports registering on the system which makes life hard for the Network Manager. Check out the script file , its is easy to enter your provider info},Will  work with WVDIAL OR Direct with PPP,  so if wvdial is installed be carefull , Read the script file

[http://sakis.tel4u.gr/blog/sakis3g/#features](http://sakis.tel4u.gr/blog/sakis3g/#features)

[http://sakis.tel4u.gr/blog/2010/01/26/sakis3g-unknown-operator/](http://sakis.tel4u.gr/blog/2010/01/26/sakis3g-unknown-operator/)

[http://wiki.sakis3g.org/wiki/index.php?title=Main_Page](http://wiki.sakis3g.org/wiki/index.php?title=Main_Page)

Check it out at Sakis' blog [ToDo Forever]("http://sakis.tel4u.gr/blog/sakis3g/"). 

Reminder " Read the script file "

If done with Ubuntu the " sakis3g " script should be in the " usr/bin "  it is easy to add to the menu go to edit menu's and add new item , then locate the script , also give it a name



[SIZE=2][PPP Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")[/SIZE][SIZE=2]

[The gnome-ppp dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")[/SIZE]
[LIST]
[*][SIZE=2][User Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")[/SIZE]
[*][SIZE=2][Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")[/SIZE]
[/LIST]


[SIZE=3][COLOR=Red][COLOR=Black][B][SIZE=2]Problem solving : PPP, Network Manager : and more

[/SIZE][/B][/COLOR] [/COLOR][/SIZE]                                  
[LIST]
[*][SIZE=2][https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2][The     PPTP-client website]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml") has some great troubleshooting tips. Start     there, even if you're using [NetworkManager]("https://help.ubuntu.com/community/NetworkManager")'s     PPTP support.      [/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]NM daily Trunk PPA { Please read in detail } use at own risk : but worth a read
[/SIZE]
[*][SIZE=2]http://www.asoftsite.org/s9y/
[/SIZE]
[/LIST]
                                                    
[LIST]
[*][SIZE=2][[COLOR=#000000]http://live.gnome.org/NetworkManager/MobileBroadband[/COLOR]]("http://live.gnome.org/NetworkManager/MobileBroadband")[/SIZE]
[/LIST]

[LIST]
[*][SIZE=2][COLOR=#000000]How can you help to improve  Network Manager (read all)
[/COLOR][/SIZE]
[*][SIZE=2]                                  [http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/](http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/)[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2][[COLOR=#000000]http://tldp.org/HOWTO/PPP-HOWTO/c1337.html[/COLOR]]("http://tldp.org/HOWTO/PPP-HOWTO/c1337.html")[/SIZE]
[*][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE]
[*][SIZE=2][[COLOR=#000000]http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ[/COLOR]]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ")[/SIZE]
[*][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE]
[*][SIZE=2][[COLOR=#000000]http://live.gnome.org/NetworkManager/Debugging[/COLOR]]("http://live.gnome.org/NetworkManager/Debugging")[/SIZE]
[*][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE]
[*]                                  SOLVED] **[Idea Netsetter USB internet]("http://ubuntuforums.org/showthread.php?t=1380292")**
[*][B]Note :
[/B]
[*][B]Network manager Problem Try this how to
[/B]
[*]                                  **[How to :Modify new name server address(NS1/NS2)]("http://ubuntuforums.org/showpost.php?p=8664426&postcount=6")**
[/LIST]

[LIST]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]RE     : Ubuntu Tweak ;[/COLOR][COLOR=#000000]This     is What I use to Clean up My system etc/etc / Installing and using     at your own risk /But the site is Worth a visit / [/COLOR][/COLOR][/SIZE]
[LIST]
[*][SIZE=2][COLOR=#000080][[COLOR=#000000]http://ubuntu-tweak.com/[/COLOR]]("http://ubuntu-tweak.com/")[/COLOR][/SIZE]
[LIST]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]From             the Menu Package Cleaner Here are the options[/COLOR][/COLOR][/SIZE]
[LIST]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]Clean                 Package[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]Clean                 Cache[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]Clean                 Config[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#000080][COLOR=#000000]Clean                 Kernel[/COLOR][/COLOR][/SIZE]
[/LIST]
         
[/LIST]
     
[/LIST]
 
[/LIST]
                   
 
 
.............................................................................................................................................................................................................................

to find out what usb_modeswitch can do from the Terminal

Code:

man usb_modeswitch

Or see Post #10 

                                 **#[Details of Man usb modeswitch]("http://ubuntuforums.org/showpost.php?p=8454870&postcount=10")**
 
.................................................................................................................................................................................................................................................

     Link to                             [ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")
[URL="http://www.draisberghof.de/usb_modeswitch/bb/"]
[/URL]
 Also, there is still a bit of information to fill in for certain devices, to assign the right switching command depending on device description data. **Your input is needed** !!
 See this [forum thread]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=165").
 ................................................................................................................................................................................................................................................
 **Links for usb-modeswitch** (1.1.3-1)  ..Please Check The Ubuntu [Version] [Details of package] Site for any of the below
**Debian Resources:**

[LIST]
[*][Bug Reports]("http://bugs.debian.org/usb-modeswitch")
[*][Developer  Information (PTS)]("http://packages.qa.debian.org/usb-modeswitch")
[*][Debian  Changelog]("http://packages.debian.org/changelogs/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.3-1/changelog")
[*][Copyright  File]("http://packages.debian.org/changelogs/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.3-1/usb-modeswitch.copyright")
[/LIST]
     Download Source Package [usb-modeswitch]("http://packages.debian.org/source/sid/usb-modeswitch"):        

[LIST]
[*][[usb-modeswitch_1.1.3-1.dsc]]("http://ftp.de.debian.org/debian/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.3-1.dsc")
[*][[usb-modeswitch_1.1.3.orig.tar.bz2]]("http://ftp.de.debian.org/debian/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.3.orig.tar.bz2")
[*][[usb-modeswitch_1.1.3-1.debian.tar.gz]]("http://ftp.de.debian.org/debian/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.3-1.debian.tar.gz")
[/LIST]
           **Maintainer:**


[LIST]
[*][EMAIL="didier@raboud.com"]Didier  Raboud[/EMAIL]     ([QA Page]("http://qa.debian.org/developer.php?login=didier%40raboud.com"))
[/LIST]
  **External Resources:**

 
[LIST]
[*][Homepage]("http://www.draisberghof.de/usb_modeswitch/")  [["]www.draisberghof.de]]("http://www.draisberghof.de)
[/LIST]
             **Similar packages:**

     
[LIST]
[*][usb-modeswitch-data]("http://packages.debian.org/usb-modeswitch-data")
[*][usbmount]("http://packages.debian.org/usbmount")
[*][ozerocdoff]("http://packages.debian.org/ozerocdoff")
[*][linux-wlan-ng]("http://packages.debian.org/linux-wlan-ng")
[*][ifplugd]("http://packages.debian.org/ifplugd")
[*][usbutils]("http://packages.debian.org/usbutils")
[*][ifupdown-scripts-zg2]("http://packages.debian.org/ifupdown-scripts-zg2")
[*][zd1211-firmware]("http://packages.debian.org/zd1211-firmware")
[*][usbip]("http://packages.debian.org/usbip")
[*][x10]("http://packages.debian.org/x10")
[*][usbmgr]("http://packages.debian.org/usbmgr")
[/LIST]

***********************************************************************************************
   Canonical does not provide updates for usb-modeswitch. Some updates may be provided by the Ubuntu community.

---

### Post by AlanR8 on 2009-11-19
You can't just say it won't connect without giving additional details such as hardware etc!

Personally I've found absolutely NO trouble with wireless broadband. In fact I'm sitting in my sad hotel room as we speak connected to the web via my Nokia Navigator mobile phone that's in turn connected to this Sony laptop via bluetooth!

My son got a Blackberry Storm 2 last weekend and it took all of 2 minutes to get on the web via his phone and bluetooth.

That doesn't say to me that "mobile broadband can't connect".......

---

### Post by alexfish on 2009-11-19
> **AlanR8 said:**
> You can't just say it won't connect without giving additional details such as hardware etc!

Personally I've found absolutely NO trouble with wireless broadband. In fact I'm sitting in my sad hotel room as we speak connected to the web via my Nokia Navigator mobile phone that's in turn connected to this Sony laptop via bluetooth!

My son got a Blackberry Storm 2 last weekend and it took all of 2 minutes to get on the web via his phone and bluetooth.

That doesn't say to me that "mobile broadband can't connect".......

Hi 
The devices with usb massstorage onboard are the specific devices / the one I'm on at present is a vodaphone topup and go
     this device configured and connected no problem with Ubuntu 9.04 without the usb-modeswitch been installed

   In Ubuntu 9.10 this is not the case 
    
         to access certain devices in some cases requires the download of the usb-modeswitch / related item ndiswrapper 
          
        extract from site

       Introduction

USB_ModeSwitch is (surprise!) a mode switching tool for controlling "flip flop" (multiple device) USB gear.

Several new USB devices (especially high-speed wireless WAN stuff, there seems to be a chipset from Qualcomm offering that feature) have their MS Windows drivers onboard; when plugged in for the first time they act like a flash storage and start installing the driver from there. After that (and on every consecutive plugging) this driver switches the mode internally, the storage device vanishes (in most cases), and a new device (like an USB modem) shows up. The WWAN gear maker Option calls that feature "ZeroCD (TM)".

As you may have guessed, nothing of this is documented in any form and so far there are no official Linux drivers available (with the notable exception of Option products). On the good side, most of the known devices work out of the box with the available Linux drivers like "usb-storage" or "usbserial" (in recent kernels quite a lot of devices are acknowledged by the "option" module). That leaves the problem of the mode switching from storage to modem or whatever the thing is supposed to do. 
 
      some of the searches head by " mobile broadband can't connect " .

   Do  you feel the heading should be different , if so please advise 
.............................................................................

      @Alexfish

---

### Post by AlanR8 on 2009-11-20
That's why I use my mobile phone!

Why would I want to pay about £15 - £25 pm for a dongle when I can achieve the same result with my phone? The Nokia Navigator is 3.5 G and that was the key reason I bought it. I got Vodafone to tweak my package to include free unlimited web access and that's it.

---

### Post by alexfish on 2009-11-20
> **AlanR8 said:**
> That's why I use my mobile phone!

Why would I want to pay about £15 - £25 pm for a dongle when I can achieve the same result with my phone? The Nokia Navigator is 3.5 G and that was the key reason I bought it. I got Vodafone to tweak my package to include free unlimited web access and that's it.

point taken ,  my two sons have similar to yours, there great , but did not serve my       purpose so I opted for the dongle  / a lot of people use them so there has to be a reason.

    so for linux user they can have drawbacks , , , as described at the site mentioned
       " http://www.draisberghof.de/"

 its worth a read

---

### Post by alexfish on 2009-11-25
[COLOR=Navy]
[/COLOR] [SIZE=3][COLOR=Navy]RE : Ubuntu Tweak ; 

This is What I use to Clean up My system etc/etc  / Installing and using at your own risk /But the site is Worth a visit / [/COLOR]

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

From the Menu Package Cleaner Here are the options

Clean Package

Clean Cache

Clean Config

Clean Kernel


[/SIZE]

---

### Post by AlanR8 on 2009-11-25
Yesterday, I was working with a colleague who's also paying his 15 squid per month for a 3 mobile dongle. He uses the dreaded Vista but the redeeming fact is that he's also got the Nokia Navigator phone. 

I sorted him with his Nokia connection within a couple of minutes, yes I still remember how Doze works! He's impressed but is concerned about Vodafone's "fair usage" policy as he tends to stream media whilst away from home. Time will tell.

So, having sorted that out, and whilst our delegates were doing some work on their own, we are trainers, I asked if I could try his 3 dongle in my machine as I'd heard of people having connection issues.

His dongle is the one on the end of a short wire. I plugged it in and the LED started to blink on and off, but nothing changed on the desktop. 

I then went into Network Connections and clicked Mobile Broadband and then clicked Add. 

The wizard kicked off, recognised the dongle correctly (I assume) and I clicked through. I had to add a user name and password, both "web" without the punctuation, saved then clicked connect.

Immediate connection.

---

### Post by alexfish on 2009-11-25
> **AlanR8 said:**
> Yesterday, I was working with a colleague who's also paying his 15 squid per month for a 3 mobile dongle. He uses the dreaded Vista but the redeeming fact is that he's also got the Nokia Navigator phone. 

I sorted him with his Nokia connection within a couple of minutes, yes I still remember how Doze works! He's impressed but is concerned about Vodafone's "fair usage" policy as he tends to stream media whilst away from home. Time will tell.

So, having sorted that out, and whilst our delegates were doing some work on their own, we are trainers, I asked if I could try his 3 dongle in my machine as I'd heard of people having connection issues.

His dongle is the one on the end of a short wire. I plugged it in and the LED started to blink on and off, but nothing changed on the desktop. 

I then went into Network Connections and clicked Mobile Broadband and then clicked Add. 

The wizard kicked off, recognised the dongle correctly (I assume) and I clicked through. I had to add a user name and password, both "web" without the punctuation, saved then clicked connect.

Immediate connection.
what happen to the flashing blue light
Thanks Alan

---

### Post by alexfish on 2009-12-04
[SIZE=3][COLOR=Navy] RE:Ubuntu linux on the move 
[/COLOR] 
[SIZE=1]>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>[/SIZE]
[/SIZE] 
[SIZE=2][COLOR=Navy]This One Is Worth Worth A Goole [/COLOR][/SIZE][SIZE=2]

[/SIZE]  
[LIST]
[*][SIZE=2][Introduction]("http://www.pcurtis.com/ubuntu-mobile.htm#intro")[/SIZE]
[*][SIZE=2][Initial Configuration required to use any modem]("http://www.pcurtis.com/ubuntu-mobile.htm#initial_config")[/SIZE]
[LIST]
[*][SIZE=2][Providing users with the privileges to use modems, access the internet by a modem and root privileges  for configuration (sudo)]("http://www.pcurtis.com/ubuntu-mobile.htm#priviledges")[/SIZE]
[*][SIZE=2][Finding and Monitoring Devices and Connections - System Logs]("http://www.pcurtis.com/ubuntu-mobile.htm#connection_monitoring")[/SIZE]
[/LIST]
 
[*][SIZE=2][Classic Dial up Modems on land Lines]("http://www.pcurtis.com/ubuntu-mobile.htm#dum")[/SIZE]
[LIST]
[*][SIZE=2][Basic Modem Connection Software - Network Manager]("http://www.pcurtis.com/ubuntu-mobile.htm#network_manager")[/SIZE]
[*][SIZE=2][Network Monitor]("http://www.pcurtis.com/ubuntu-mobile.htm#network_monitor")[/SIZE]
[/LIST]
 
[*][SIZE=2][Connecting via Mobile Telephones with inbuilt modems ]("http://www.pcurtis.com/ubuntu-mobile.htm#mobile_telephone")[/SIZE]
[LIST]
[*][SIZE=2][Bluetooth connection to a Phone Modem]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth")[/SIZE]
[LIST]
[*][SIZE=2][Bluetooth - basics and pairing]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth_basic")[/SIZE]
[*][SIZE=2][Creating a Bluetooth Phone Dial-Up Network Device]("http://www.pcurtis.com/ubuntu-mobile.htm#bt_device")[/SIZE]
[/LIST]
 
[*][SIZE=2][GPRS Access via Mobile Phone]("http://www.pcurtis.com/ubuntu-mobile.htm#gprs")[/SIZE]
[*][SIZE=2][Using Windows Mobile Devices as Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#xda")[/SIZE]
[/LIST]
 
[*][SIZE=2][PPP Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")[/SIZE]
[LIST]
[*][SIZE=2][The gnome-ppp dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")[/SIZE]
[LIST]
[*][SIZE=2][User Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")[/SIZE]
[*][SIZE=2][Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")[/SIZE]
[*][SIZE=2][Adding the initial Signal Strength to the gnome-ppp connection log ]("http://www.pcurtis.com/ubuntu-mobile.htm#signal_strength")[/SIZE]
[/LIST]
 
[*][SIZE=2][Netspeed Applet to monitor connection speed and data flow ]("http://www.pcurtis.com/ubuntu-mobile.htm#netspeed")[/SIZE]
[*][SIZE=2][Firefox 3 and PPP connections - fixing Firefox starting in Offline Mode]("http://www.pcurtis.com/ubuntu-mobile.htm#firefox_offline_fix")[/SIZE]
[/LIST]
 
[*][SIZE=2][Mobile Broadband - PCMCIA Cards and USB Sticks]("http://www.pcurtis.com/ubuntu-mobile.htm#vfconnect")[/SIZE]
[LIST]
[*][SIZE=2][Vodafone Mobile Connect PCMCIA Card (legacy section but with some useful background) ]("http://www.pcurtis.com/ubuntu-mobile.htm#vfconnect")[/SIZE]
[LIST]
[*][SIZE=2][Testing with AT commands via the Serial Port Terminal (of general use)l]("http://www.pcurtis.com/ubuntu-mobile.htm#at_commands")[/SIZE]
[*][SIZE=2][Connections to card using wvdial (gnome-ppp is a front end to wvdial making it largely redundant) ]("http://www.pcurtis.com/ubuntu-mobile.htm#wvdial")[/SIZE]
[*][SIZE=2][PCMCIA Card Eject Script (of general use) ]("http://www.pcurtis.com/ubuntu-mobile.htm#pcmcia_eject_script")[/SIZE]
[/LIST]
 
[*][SIZE=2][Vodafone Mobile Connect Broadband package with Huawei E220 USB Modem]("http://www.pcurtis.com/ubuntu-mobile.htm#vmc_usb")[/SIZE]
[LIST]
[*][SIZE=2][Vodafone Mobile Connect Software]("http://www.pcurtis.com/ubuntu-mobile.htm#vmc")[/SIZE]
[*][SIZE=2][Workrounds for Device detection problems  under Hardy due to mode switching feature ]("http://www.pcurtis.com/ubuntu-mobile.htm#usb_modem_detect")[/SIZE]
[*][SIZE=2][Using the Huawei USB Modems wth gnome-ppp]("http://www.pcurtis.com/ubuntu-mobile.htm#huawei_gnome-ppp")[/SIZE]
[*][SIZE=2][Use with the Network Manager Applet 0.7 under Ubuntu 9.04 Jaunty Jacalope ]("http://www.pcurtis.com/ubuntu-mobile.htm#huawei_jaunty")[/SIZE]
[/LIST]
 
[*][SIZE=2][NZ Telecom Broadband USB T-Stick]("http://www.pcurtis.com/ubuntu-mobile.htm#tstick")[/SIZE]
[*][SIZE=2][Sharing Mobile Broadband - the Edimax Wireless 3G Broadband Router 3G-6200n]("http://www.pcurtis.com/ubuntu-mobile.htm#edimax")[/SIZE]
[/LIST]
 
[*][SIZE=2][Other Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#softmodem")[/SIZE]
[LIST]
[*][SIZE=2][Conexant Soft Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#softmodem")[/SIZE]
[*][SIZE=2][COLOR=#008c00]**[all variants]**[/COLOR][/SIZE][SIZE=2]                          [How To : Conexant  or Rockwell Modems Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1375694")[/SIZE]
[/LIST]
 
[*][SIZE=2][Monitoring Data Transfer]("http://www.pcurtis.com/ubuntu-mobile.htm#datamon")[/SIZE]
[*][SIZE=2][Communications Requirements Table]("http://www.pcurtis.com/ubuntu-mobile.htm#communications_requirements")[/SIZE]
[*][SIZE=2][Reader Feedback]("http://www.pcurtis.com/ubuntu-mobile.htm#feedback")[/SIZE]
[/LIST]
[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

added  tip

Unlocking your modem will enable all the bands the 3G modem hardware is capable of!

---

### Post by alexfish on 2009-12-07
Details of man usb_modeswitch:

SB-MODESWITCH(1)                                            USB-MODESWITCH(1)

NAME
       usb-modeswitch &#8212; Switching tool for controlling "flip flop" USB devices

SYNOPSIS
       usb-modeswitch [-hvpVPmMrdHn]  [-c filename]

DESCRIPTION
       This  manual  page  was written for the Debian distribution because the
       original program does not have a manual page.

       Several new USB devices have their proprietary Windows drivers onboard,
       especially  WAN  dongles.  When plugged in for the first time, they act
       like a flash storage and start installing the driver from there. If the
       driver  is  already  installed,  the  storage device vanishes and a new
       device, such as an USB modem, shows up. This  is  called  the  "ZeroCD"
       feature.

       On  Debian, this is not needed, since the driver is included as a Linux
       kernel module, such as "usbserial". However, the device still shows  up
       as  "usb-storage" by default. usb-modeswitch solves that issue by send&#8208;
       ing the command which actually performs the  switching  of  the  device
       from "usb-storage" to "usbserial".

OPTIONS
       These  programs  follow  the  usual  GNU command line syntax, with long
       options starting with two  dashes  (`-').   A  summary  of  options  is
       included below.

       -h           --help
                 Show summary of options.

       -v           --default-vendor [nr]
                 Vendor ID to look for (mandatory).

       -p           --default-product [nr]
                 Product ID to look for (mandatory).

       -V           --target-vendor [nr]
                 Target Vendor (optional, for success check).

       -P           --target-product [nr]
                 Target Model (optional, for success check).

       -C           --target-class [nr]
                 Target Device Class

       -m           --message-endpoint [nr]

       -M           --message-content [nr]
                 Command to send (hex as string)

       -r           --response-endpoint [nr]
                 If given, read response from there

       -d           --detach-only
                 Whether to just detach the storage driver

       -H           --huawei-mode
                 Whether to just apply the Huawei mode

       -S           --sierraMode
                 Whether to just apply the Sierra mode

       -O           --sonyMode
                 Whether to just apply the Sony mode

       -R           --resetUSB
                 Whether to reset the device in the end

       -c           --config [filename]
                 Load different config file

       -Q           --quiet
                 Don't show progress or error messages

       -W           --verbose
                 Print all settings before running

       -s           --success [nr]
                 Check switching result after [nr] secs

       -I           --no-inquire
                 do not get device details (default on)

       -i           --Interface
                 Select initial USB interface (default: 0)

       -u           --Configuration
                 Select USB configuration

       -a           --AltSetting
                 Select alternative USB interface setting

AUTHOR
       This manual page was written by Didier Raboud [email]didier@raboud.com[/email] for the
       Debian system (and may be used by others).  Permission  is  granted  to
       copy, distribute and/or modify this document under the terms of the GNU
       General Public License, Version 2 any later version  published  by  the
       Free Software Foundation.

       On  Debian systems, the complete text of the GNU General Public License
       can be found in /usr/share/common-licenses/GPL.

                                                             USB-MODESWITCH(1)

---

### Post by alexfish on 2009-12-14
This is a small     update to HSOconnect that allows it to work with the iCon 515 as     sold by Orange. or 5X5

Tested On Ubuntu 9.10

[**Re: Option iCON 515m wireless USB modem (Orange)** ]("http://ubuntuforums.org/showthread.php?t=1351612")

---

### Post by alexfish on 2009-12-17
Test Page
 Please Do Not Post Question About This

**What is GPRS?**

GPRS stands for **General Packet Radio Service**, and is a protocol for passing data over a mobile phone network. Here's what you need to know about GPRS:
 
[LIST]
[*]GPRS replaced dial-up mobile phone     Internet access, offering faster browsing of Internet content and     email. It's an "always on" service".
[*]GPRS on a [COLOR=#000080][SIZE=2]Mobile     Phone or USB Dongle [/SIZE][/COLOR]doesn't use a phone number to     connect, it uses something called an [COLOR=#000080]APN     (Access Point Name).[/COLOR]
[*]With GPRS, you don't pay for your     on-line time per-minute, you pay for the amount of data you     transfer.
[*]GPRS has now been largely superseded by faster data network     services known as 3G
[/LIST]
 


        Ubuntu 9.10  USB Dongle  New Version  With Qualcom chip and how it is seen by Linux
         To Find The Type Of Device You Have
 
[LIST]
[*]Boot up the computer without the     device
[*]Select From  / System menu Select     / Administration / Disk Utility
[*]A window will appear showing what     types of Disks That Are Connected to The system
[*]Look at This Screen Carefully
[*]Insert The USB dongle
[*]Notice what happens
[*]In general it shows up as a      MMC Storage
[*]Then a CD Drive With An /  ISO image
[*]Rt click / Safely Remove / the CD     Disappears
[*]To Find The Type of  Device : From the Terminal Type in this Code  :  lsusb
[/LIST]

---

### Post by alexfish on 2009-12-18
Re :Problems  Getting Connected Ubuntu 9.10

 I have Been Up Dale and Down Dale With This One 

  This is what I Have Done
  Run the Update Manager 

Rebooted  


Then  from the Boot Menu :Select &#8220; Kernel Linux 2.6.31-14-Generic &#8220;  

Up and running First Boot // No Problems

  USB Broadband Worked  First Time  

   Sounds And Video  Work To 
  
{I Think to do with the  // Qualcomm  Chip on board the device //  and  Configuration of the device when it boots in}

Updating :It is reasonable to assume as of 4th Feb 2010 everything seams to be "   	 	 	 	 	reasonably stable " with    	 	 	 	 	exception of the resolvconf : always disable the wired or wireless connections whilst using these devices

---

### Post by alexfish on 2009-12-19
Ubuntu 9.10

RE: NEW VODAFONE MOBILE BROADBAND  [SIZE=3][COLOR=Navy]The Paper [Solve][/COLOR][/SIZE]...:P

My Dongle is a New Vodafone /

I decide to open up The Dongle / Please Don't Try This Unless You Know What you are doing

This is What I discovered /Having taken all the bits apart /? Don't try this /


DO THIS 
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Inside the case There is a Connection Like the Type on a Slide Switch , except this one does not slide

The Solution ??????

I place a [SIZE=3][COLOR=Navy]pi[/COLOR][/SIZE][SIZE=3][COLOR=Navy]ece of paper over the connection[/COLOR][/SIZE] and re assemble the device

GUESS WHAT , THE DONGLE NOW WORKS ///  :lolflag:This may work on other dongles , but have not tested

Now BURN'T OUT THIS IS NOT ADVISABLE:-({|=#-o
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

---

### Post by pdc on 2009-12-19
do you feel like posting a photo?

---

### Post by alexfish on 2009-12-19
> **pdc said:**
> do you feel like posting a photo?

Hi 
Sunday Or Monday Hopefully

Below Is A Better Solution I Hope

Also get the latest updates for the device via vodafone / Now working 98% on Ubuntu 9.10. kernel - 2.6.31-17

---

### Post by alexfish on 2009-12-21
RE : Web Browser Not Connecting To The Server

Try Setting The IPv4 : Automatic (PPP) Address only  ; You need the address of the server you want

   if you get connected with the method below then make a note of the address from the connection info Re Primary DNS , then use it in the above

  if you use a open server address Check to see if the backend of the system is working ie synaptic
  
   you can set up to different connections  by having different Address only 

This Hopefully will Avoid the Below?


Note settings for IPv4  :Automatic (PPP)

DNS details for "IPv4 Automatic (PPP) Adress only ", and other details  can be found a File called "serviceproviders.xml"  Screenshot below

Can You AlsoTry This


**Add in /etc/modprobe.conf:**           

**[B]options usb-storage delay_use=1               (or 10, or other)   5 is a good bench mark**[/B] To start

 From The log file Viewer You Can Check If There is A connection to The Secondary Server Which is The one to look for , if only see primary then your only connected locally
 

Adjust the Value Till it Looks Like This

 kernel: [  294.723705] usb 1-5: configuration #1 chosen from 1 choice

 [COLOR=Navy]kernel: [  294.746196] option 1-5:1.0: GSM modem (1-port) converter detected
 kernel: [  294.746512] usb 1-5: GSM modem (1-port) converter now attached to [COLOR=Black]**[SIZE=2]ttyUSB0[/SIZE]**[/COLOR]
[/COLOR]
 [COLOR=Navy]kernel: [  294.748622] option 1-5:1.1: GSM modem (1-port) converter detected
 kernel: [  294.748902] usb 1-5: GSM modem (1-port) converter now attached to **[SIZE=2][COLOR=Black]ttyUSB1[/COLOR][/SIZE]**[/COLOR]

if you a ZTE device and it has flipped correctly then you will possibly see  [COLOR=Navy]**[SIZE=2][COLOR=Black]ttyUSB2 [/COLOR][/SIZE]**[/COLOR]this is OK

 kernel: [  294.752541] scsi8 : SCSI emulation for USB Mass Storage devices
 kernel: [  294.754201] scsi9 : SCSI emulation for USB Mass Storage devices

 [COLOR=Navy]kernel: [  299.755772] scsi 8:0:0:0: [SIZE=2][COLOR=Black]CD-ROM [/COLOR][/SIZE]           HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
 kernel: [  299.757881] scsi 9:0:0:0:[SIZE=2][COLOR=Black]Direct-Access [/COLOR][/SIZE]    HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2[/COLOR]

[COLOR=Navy] kernel: [  299.781429] sr2: scsi-1 drive
 kernel: [  299.781995] sr 8:0:0:0: Attached scsi generic sg4 type 5
 kernel: [  299.782669] sd 9:0:0:0: Attached scsi generic sg5 type 0
 kernel: [  299.802756] sd 9:0:0:0: [sdc] Attached SCSI removable dis[/COLOR]k

 pppd[8879]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
pppd[8879]: pppd 2.4.5 started by root, uid 0
 pppd[8879]: Using interface ppp0

 pppd[8879]: Connect: ppp0 <-->** [SIZE=2][COLOR=Black]/dev/ttyUSB0[/COLOR][/SIZE]**  (or **[SIZE=2][COLOR=Black]ttyUSB2[/COLOR][/SIZE]**)

 [COLOR=Navy]kernel: [  324.448138] PPP BSD Compression module registered
 kernel: [  324.475252] PPP Deflate Compression module registered[/COLOR]

 pppd[8879]: Could not determine remote IP address: defaulting to 10.64.64.64

 pppd[8879]: local  IP address 10.91.124.131
 pppd[8879]: remote IP address 10.64.64.64
[COLOR=Navy]
 pppd[8879]: **[SIZE=2][COLOR=Black]primary.. [/COLOR][/SIZE]**  DNS address 10.206.65.68
 pppd[8879]: [COLOR=Black]**[SIZE=2]secondary[/SIZE]**[/COLOR] DNS address 10.206.65.68

 If it is connecting to **[COLOR=Black]TTYUSB[1][/COLOR]**[COLOR=Black]  you will get errors [ unplug the device and start again] 

[SIZE=3][COLOR=Red]*******Still Got Problems : look here************[/COLOR]

[http://tldp.org/HOWTO/PPP-HOWTO/c1337.html](http://tldp.org/HOWTO/PPP-HOWTO/c1337.html)

[/SIZE] '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Thes are  handy Terminal commands, play around with and see what they are doing

Code:

[/COLOR][/COLOR]ls -al /dev/ttyU*

tail /var/log/messages
[COLOR=Navy][COLOR=Black]
[/COLOR][/COLOR]/sbin/route -n

dig "providername"  IE : dig [COLOR=Navy][COLOR=Black]custard.bris.ac.uk[/COLOR][/COLOR]

You may want to write an alias's ie for  ls -al /dev/ttyU* or put it in a launcher on the desktop as one tends to use it quite often!
[COLOR=Navy][COLOR=Black]
Other Codes:

ifconfig -a
route -n
uname -a
lsmod
strings `which pppd`|grep -i mppe|wc --lines
dmesg | tail -n 25
ping -c 5 custard.bris.ac.uk
iptables -L -n

some need root permisions
[/COLOR] [/COLOR]

---

### Post by alexfish on 2009-12-28
RE : ZTE MF627 HSDPA Modem..

[B]
Removed:[/B]
reference to http  [www.greenhughes.com](www.greenhughes.com)

---

### Post by alexfish on 2010-01-13
Hi
latest 

**Latest Download** for USB_MODESWITCH  / If you are a Novice Please Seek Help

See post   #[**1**]("http://ubuntuforums.org/showpost.php?p=8349637&postcount=1")

---

### Post by alexfish on 2010-02-03
[SIZE=2]RE :Huawei modem e220/e270[/SIZE]

lsusb

Bus 001 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem 
 
 In the wireless section this device will also show up as a "Mobile broadband (HUAWIE technologies HUAWIE Mobile)"
 
According to information this  device has three known modes of operation
 
[LIST=1]
[*]mobile broadband (Shows in Ubuntu)
[*]act as usb wireless (Shows in Ubuntu)
[*]connection to hot spots
[/LIST]
 This may be the reason for the strange behaviour of the device and also the multiples of the device as seen by the device manager . Not to mention the the problems with the resolvconf
 
Information from windows files
 
wwdfdb DeviceList
 &#8722;
 wwdfdb Device id="253"
 wwdfdb:Mfg Huawei /wwdfdb:Mfg
 wwdfdb:Model E160 /wwdfdb:Model
 
wwdfdb: Device id="254"
 wwdfdb: Mfg Huawei /wwdfdb:Mfg
 wwdfdb: Model E169 /wwdfdb:Model
 
[DRIVER] 
 WLAN=0
 

 DEFAULT_TIMEOUT=10
 

 VALUE=11.030.01.07.04

                                 How to check for Problematic modem devices
 

 install Device Manager
 

 look at the usb device listings , for one device you may see two or three devices listed  and possibly a mass storage device this is normal
 

 but may be problematic if  
 

 part of that device  shows up as Unmanaged
 

 or more than three devices are listed for the one device
 

 more than one device shows up and only one device is connected
 

 This can lead to spasmodic identification of the ports and connection problems with Modem Manager and Network Manager , hence the Quotes " Unplug the modem and plug it back in again "
 

 This part is not totally conclusive as sometimes the device is identified and the correct port is been accessed ,  verify  with Network Manager / Connection Information / . if the interface , &#8220;look at the tty*X&#8221; , where X is the port number , if the port number varies then it may be a problematic device , well maybe most probably, don't blame Linux , blame the device

Also if wvdial is set to use a particular port then it may also fail at times , as a quick fix  install the (Gnome ppp , then get it to detect the modem or rerun the wvdial config again ). don't always work with ZTE device
or if the modem has more than one control line , if you have three ports or more and the connection fails say on port 1 then try port 2 ,
 

  If you have one of these devices and constantly have problems with it then you could try SAKIS3G as mentioned in the first post, this has it's own port probing , and includes a copy of  USB modeswitch ,Set up and usage at your own risk, but is recommended if you have a problematic device . Failing that ,  I know What I would do with a Problematic Device.

---

### Post by alexfish on 2010-02-11
How to update the Network Manager database.  
 

 

 On the Ubuntu system there should be two files  “serviceproviders.2.dtd” and “serviceproviders.xml”
 

 The “serviceproviders.xml” is the actual database used by the NM
 

 Prior to updating the database to suite your requirements Please Read All Legal info etc at the site.   and the how to
 

 I accept no responsibility for any of the forgoing . Therefore use at your own risk


   	 	 	 	 	 	  Contents
 
[LIST=1]
[*][Service 	Provider Database]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Service_Provider_Database")

[LIST=1]
[*][License]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#License")
[/LIST]
 	
[*][How 	to Contribute]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#How_to_Contribute")

[LIST=1]
[*][Checkout/Clone]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Checkout.2BAC8-Clone")
[*][Adding 		and Updating Information]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Adding_and_Updating_Information")

[LIST=1]
[*][Adding 			a New Country]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Adding_a_New_Country")
[*][Adding 			a New Service Provider]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Adding_a_New_Service_Provider")
[*][Multiple 			Access Points (GSM)]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Multiple_Access_Points_.28GSM.29")
[/LIST]
 		
[*][Before 		Submitting Your Changes]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Before_Submitting_Your_Changes")
[*][Diff]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Diff")
[*][Submit 		Your Patch]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Submit_Your_Patch")
[/LIST]
 	
[*][Full 	XML Specification]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Full_XML_Specification")

[LIST=1]
[*][Document 		Type Definition]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Document_Type_Definition")
[*][Elements]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Elements")

[LIST=1]
[*][serviceproviders]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#serviceproviders")
[*][country]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#country")
[*][provider]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#provider")
[*][name]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#name-1")
[*][gsm]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#gsm")
[*][network-id]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#network-id")
[*][apn]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#apn")
[*][username]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#username")
[*][password]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#password")
[*][dns]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#dns")
[*][gateway]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#gateway")
[*][cdma]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#cdma")
[*][sid]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#sid")
[/LIST]
 		
[*][Other 		Information]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Other_Information")
[/LIST]
 	
[*][Discussion]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Discussion")

[LIST=1]
[*][Example 		XML file]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Example_XML_file")
[/LIST]
[/LIST]
   	 	 	 	 	 	  [http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Service_Provider_Database](http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders#Service_Provider_Database)

---

### Post by pradeepthundiyil on 2010-02-15
Hi,

For those who are not able to connect using mobile broadband. 

I also had the same issue, but I resolved it. 

DO the following to connect using USB modem

DOwnload and Install Gnome-PPP, using different computer or other OS if it is dual boot.

CLick ->Settings -> Detect modem in Gnome -PPP

Enter username and password.

Click COnnect.. 

Good Luck..

---

### Post by alexfish on 2010-03-02
The on going saga of the Network Manager failing to return the NS1 and NS2
IE the modem connects but the Browser and updates etc fail to connect

Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30  ( or any thing above the default value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10). 
 ipcp-max-failure 30

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP)  instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

I will be monitoring the outcome of this change.


Also try this from a recent post / but also has roots from the past / please read the thread
  	 	 	 	 	 	  

 [http://ubuntuforums.org/showthread.php?t=1426409](http://ubuntuforums.org/showthread.php?t=1426409)
 

 

Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute
 
if this is done then replace the #  in front of the    	 	 	 	 	

replace the # in front of the  " ipcp-max-failure 30 " do not use both lines


also the replacedefaulte  has failed a few times after a fresh boot , but has proved quite successful

---

### Post by alexfish on 2010-04-09
Disconnection problem
 

 
[LIST=1]
[*]When using the network manager my 	modem Occasionally  disconnects after a period of time, then refuses 	to  reconnect.
[/LIST]
 

      This could be coursed by the modem receiving an SMS text , what happens is the modem may be switching to text mode ,then the system will indicate that there is no carrier , once this happens then a time-out will occur IE it is disconnected from the Bus, also the modem may be remaining in the text mode.
 

 If you have Wammu installed which is a GUI for Gammu then it is quite easy to check if any SMS texts have been received,it may be an important message from your ISP ,Wammu is also handy for sending SMS texts if your service provider allows such a service.
 

 The only way to get the modem to work after the above happens or after using Wammu or Gammu is to disconnect and reconnect the modem, or respond to the request of your ISP
 

  The above is not conclusive but have checked an a few occasions

---

### Post by alexfish on 2010-05-21
**Modem Firmware upgrades: **
  Some Manufactures and Providers are providing firmware updates to meet requirements of win7 , if you accept these updates be prepared for some devices to be no longer recognised in Linux .  
 

  I can only suggest this , if the device is working , leave as is , or ask the question " If  I upgrade the firmware , will it still work with linux “

---

### Post by ajeesh cherian on 2010-08-01
Hi,
 

 I am using Ubuntu 10.04 LTS. Please let me know how to configure Idea Netsetter 3G (Huawei E1550) so that I can connect to 3G or EDGE network.
 

 When I go to “Network Connections > Mobile Broadband > Add > Setup a mobile broadband connection” the device is not listed there. Under “Computer” the device is detected as CD/DVD drive.
 

 How can I change the configuration so that the system detects the hardware and load drivers for the same. Any help would be greatly appreciated.
 

 Thanks
 Ajeesh Cherian

---

### Post by bapoumba on 2010-08-10
Closed by request.

---

