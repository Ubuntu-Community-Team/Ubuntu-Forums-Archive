---
title: "Modems don't work with Ubuntu 8.04...HELP!!!"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by sillyboy on 2009-01-15
:confused:  I have tried 3 different modems.  Nothing works with 8.04!  I just hooked up a Rosewill RNX 56 USB modem.  I just want to use the modem as a fax.  Ubuntu does not see it.  Ubuntu did not see the USR hardware modem I just sent back either. I installed Gnome PPP, and it can not find the modems either.  What do I need to do to get a modem to work in Ubuntu 8.04?? Please help.......

Thanks

---

### Post by cdtech on 2009-01-15
What do you get from the terminal using:
```
lsusb
```

---

### Post by sillyboy on 2009-01-15
Here is what comes up cdtech.  I am new at this (Ubuntu and all Linux).  I'm trying to break away from Windows.  Thanks

Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 04e8:3272 Samsung Electronics Co., Ltd 
Bus 005 Device 003: ID 04e8:326c Samsung Electronics Co., Ltd 
Bus 005 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 004: ID 0572:1321 Conexant Systems (Rockwell), Inc. 
Bus 004 Device 003: ID 0bc2:3000 Seagate RSS LLC 
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by ieee488 on 2009-01-15
**some** modems do work in Ubuntu 8.04
I have one.

Try reading [https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems) instead of thrashing about.

---

### Post by jessejazza on 2009-01-15
Generally winmodems don't work in linux. I have one that i think has found a driver as ubu 8.04 seemed to install it but i have a problem with the settings.

I have five winmodems.... all conexant... and all need different drivers - i'm just about to chuck them out. In windoze one of them wouldn't work with the recommended drivers and eventually i found one that did. It is can be hard enough finding drivers in windoze and simply not worth the time.

With linux and to save yourself grief just get a serial port hardware modem - they plug in and work. I bought a couple for £10 - BT enabler. I use them for faxing and in reserve for the time when broadband fails... if one day.

---

### Post by sillyboy on 2009-01-16
Hi jessjazza,Thanks

I have a Cen-Dyne 56K RS-232 external modem that is serial port (or parallel port) ready.  I had it hooked up to the serial port and....Ubuntu could not find it.  This modem is just about universal for working with anything.

---

### Post by jessejazza on 2009-01-18
I thought mine didn't work at first! Ubuntu doesn't need to show it has found it - it will simply work. serial device COM1 = ttys0 ? Perhaps the configuration is not right on your machine 'setserial' is the app you may need to use.

How are you faxing - efax-gtk? That is the easiest to use but you may have to set the modem class explicitly and other params correct.

Settings--Modem--Modem class [explicitly set class 1 or class 2 rather than auto which leaves it to the software to select]
Settings--Params--Other params [enter -oh which means control by hardware only i.e. modem itself talks to other modem/fax machine that you're dialling]. Should work under software control but hardware control is quicker.

If you join the email group list efax-gtk you may even get Chris Vine the man himself! sorting you out.

If using hylafax i suggest you try efax-gtk first or dial up an isp number but i think efax-gtk is easiest. I convert files to send to pdf [rather than setting up as socket] and it works fine.

Hope this helps

[apologies for not seeing your reply earlier - this forum is so large i miss some posts]

quick google should sort out any probs - i just looked at this one first on the list. YOUR MODEM WILL WORK! Better one than mine i'd say.
[https://www.linuxquestions.org/questions/mandriva-30/help-configuring-cendyne-rs232-modem-171068/](https://www.linuxquestions.org/questions/mandriva-30/help-configuring-cendyne-rs232-modem-171068/)

it's just a setting somewhere

---

### Post by figjam on 2009-05-21
> **sillyboy said:**
> 

Bus 004 Device 004: ID 0572:1321 Conexant Systems (Rockwell), Inc. 


This is the crux of the matter. The normal Conexant drivers will not work with this one, since its not one of the 'standard' HSF modems.

How to detect the modem and install the driver using the installer

    * Download the installation program (cnxtinstall.run) 
[http://www.linuxant.com/drivers/dgc/archive/cnxtinstall.run](http://www.linuxant.com/drivers/dgc/archive/cnxtinstall.run)

    * Open a terminal window. (If you don't know how to do this, press ALT-F2 and in the dialog box that will appear, try entering one of the following commands: xterm or konsole or gnome-terminal)
    * Use the cd command to access the directory where the cnxtinstall.run file was downloaded.
    * Finally, enter the sh cnxtinstall.run command to run the installer.

It will run and detect the right stuff. It will also prompt to download the most appropriate set of drivers. 

Once done, run 'sudo hsfconfig' to set the modem up.

You may need to reboot before running 'sudo hsfconfig'

This worked for after spending countless hours trying to get this fixed.

-=F

---

