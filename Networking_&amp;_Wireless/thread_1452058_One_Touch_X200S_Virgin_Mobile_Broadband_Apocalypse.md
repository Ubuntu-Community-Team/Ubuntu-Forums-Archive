---
title: "One Touch X200S Virgin Mobile Broadband Apocalypse"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by mrjohnc on 2010-04-11
Hi All

Serious help needed. I can't get my sister new computer (she needs for work) to work with her mobile broadband dongle (details at bottom of post). The light on the dongle flashes green when plugged in, it recognises the connection in mobile broadband network connections, but won't connect (i checked connect automatically, it doesn't come up as an option in the top panel network thingy either. 

Googled a solution that works for other people, not for me. The solution is for ubuntu 8.

[http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html](http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html)


Any help would be greatly appreciated. I've been using Ubuntu for a year or so but not that experienced in fixing problems. 

The wifi and screen brightness settings are't working either but that isn't really a problem, assume it will get fixed in an update soon.

Cheers

John


Samsung N210
Ubuntu 10.04 Beta 2 (updated from 9.10, dongle didn't work in 9.10 either)
Virgin Media Mobile Broadband Dongle. TCT Mobile Ltd, One Touch X200S

---

### Post by spiky001 on 2010-04-11
hi did you set it up in network manager? by right click net manager then select mobile broadband then the add button? this is how I done mine but it was on 3 network

---

### Post by mrjohnc on 2010-04-11
> **spiky001 said:**
> hi did you set it up in network manager? by right click net manager then select mobile broadband then the add button? this is how I done mine but it was on 3 network

Yep I've done that, not working. In Network Tools there is an unknown device, is it that it can find the driver? It comes up in Network Connections though as Virgin Mobile Broadband though.

---

### Post by spiky001 on 2010-04-11
have a look here i,m sorry i cant be more help 

[http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html](http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html)

---

### Post by mrjohnc on 2010-04-11
> **spiky001 said:**
> have a look here i,m sorry i cant be more help 

[http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html](http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html)

No, tried that, doesn't work, thanks for your help anyway.

---

### Post by spiky001 on 2010-04-11
Have you hardwired laptop and done updates, theres not alot about it on google

---

### Post by mrjohnc on 2010-04-11
> **spiky001 said:**
> Have you hardwired laptop and done updates, theres not alot about it on google

Yep, it's all up to date. Guess it a pretty new computer so there will be a few hiccups.

---

### Post by mrjohnc on 2010-04-11
Maybe I should reinstall back to Ubuntu 8 and try the fix then update?

---

### Post by pdc on 2010-04-11
can you tell us what

> lsusb

and 

> dmesg | grep ttyUSB

gives you?

If you copy and paste these into a terminal, and copy and paste the results back here please

---

### Post by mrjohnc on 2010-04-12
ok so lsusb gives me

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:219b Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1bbb:f000 T & A Mobile Phones 
Bus 001 Device 004: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and dmesg | grep ttyUSB gives me nothing, it just goes back to the prompt thing.

I've been doing some digging and it seems like at least part of the problem is the dongle has a memory card reader in it and the computer sees that not the mobile broadband modem. any ideas how to?

---

### Post by mrjohnc on 2010-04-12
when i put in just dmesg i get a lot of stuff, too much to post here, i tried but it said it was too much

---

### Post by alexfish on 2010-04-12
Hi mrjohnc

looking at the id info from lsusb command this could be the same device as an "                           Alcatel X200/X060S "

Also the device ID's if correct would indicate the device needs to be switch from storage device to modem

to find out if the device can be recognised as a modem try the below

Boot up the computer without the device

If a device or file etc appears on the desktop when it is connected then right click on the device and use the eject command from the menu or safely remove, Check the device ID's with the lsusb command from the terminal before and after the  eject command, if there is a change in the ID's then it should be recognised by the Network Manager, if so follow the wizard and enter the correct info.

if this does not work 

You could try the latest usb_modeswitch package from here


                                 
[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[URL="http://packages.debian.org/sid/usb-modeswitch"]Package 
[/URL][/SIZE]
[*][SIZE=2]the above will self install
[/SIZE]
[/LIST]
  
[LIST]
[*][SIZE=2]**Or From     Draisberghof ,Latest Download**[/SIZE][SIZE=2] / If you are a     Novice Please Seek Help

The latest release version is [/SIZE][SIZE=2]**1.1.1**[/SIZE][SIZE=2].     The tar archive contains the source and a i586 binary (32 bit, GCC     4.4.1). I used libusb-0.1.12 but the "compat" library from     libusb-1.0 is now working smoothly too.Changes and updates to the     config database may happen more often than new releases; most of the     valuable knowledge about devices is contained in these files. So you     better use the latest version linked here if it is newer than the     latest program release.[/SIZE]
[/LIST]
 
[LIST]
[*]Download     [usb-modeswitch-1.1.1.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.1.tar.bz2"),     dated from 2010-03-17; a Debian (Xandros/Ubuntu) package should be     available soon at the [Debian     Repository]("http://packages.debian.org/usb-modeswitch"). Many architectures are supported there (like amd64     or ia64).
[*]Load the latest     [usb-modeswitch-data]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100322.tar.bz2")     package (2010-03-22). It contains the device database and the rules     file, including full paths. Use this version only with releases from     1.1.0 upward !
[*]The latest [usb_modeswitch.setup]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup")     (formerly known as usb_modeswitch.conf, 2010-03-16); this is a     reference to all device setups and contributors; you can use it as a     starting point if you want to make a new device working.
[*]Don't forget [libusb]("http://libusb.wiki.sourceforge.net/")     if you don't have it. In your distribution, there is most likely a     package named "libusb-dev" or "libusb-devel".     Choose the legacy version (0.1.12) or the compatible package from     libusb-1.0, at the time of writing it had the version number 0.1.13.
[/LIST]
 there should be no need to install any of the libusb for ubuntu

Once installed the device id's should change

Also for checking the device use these commands from the terminal

Code:
dmesg | grep -e "modem" -e "tty" 

this will only give the modem and the lines use by it + may indecate if any drivers have been loaded

to monitor what is happening in real time, from a separate terminal, also use this before the device is connected

Code:

tail -f /var/log/syslog

**tail** is a command which outputs the last 10 lines of a file, with  the -f option it continues to monitor the file and keeps outputing any  further additions appended to the file in real time.



regards

alexfish

---

### Post by mrjohnc on 2010-04-12
It works

Thanks very much. I'm hesitant to say this definitely all you need to do to make it work, i've downloaded a few other little programs and done some editing of files, some of which i can't remember what i did.

Thanks everybody

John

---

### Post by pdc on 2010-04-12
well done mrjohnc and well done to alex;

...... so ..........

did you try the eject command firstly?

If not, did you install usb_modeswitch; did that all go smoothly? did you do any configuration of it yourself?

can you tell us what you get on 

> dmesg | grep -e "modem" -e "tty"  now?

---

