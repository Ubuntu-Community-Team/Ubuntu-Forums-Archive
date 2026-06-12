---
title: "Needhelp with SMCWUSBS-N3 Wireless USB Dongle"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by rashid_sohaib on 2010-11-18
Hi folks,

This is my first post on this forum. Please do excuse me if I commit any faux-pas unknowingly.

I am using Ubuntu 10.10 desktop (latest updates) on an Acer Veriton 1000 desktop. I purchased a SMCWUSBS-N# Wireless USB Dongle recently and have been struggling to get it to work. NM-APPLET simply does not show any Wireless option at all. I have tried all the various posts / suggestions that I could Google and I am still nowhere. 

Last night I manually loaded the RT3370sta driver. Now iwconfig does show the card on ra0. However, NM-APPLET still does not show any Wireless option at all. 

Surprisingly "iwlist ra0 scan" command at the Terminal does show alll the available Wifi connections.

I would appreciate all the help I can get.

===
Rashid

---

### Post by grahammechanical on 2010-11-19
You may already have done this but then again you may not have. Disable and enable networking. Right click the icon and select enable networking and click. Wait a few minutes. Then repeat to enable networking again. This is like switching networking Off and then On. It allows network manager to up date it knowledge of itself. Sometimes you need to shutdown and reboot for changes to take effect.

Regards.

---

### Post by Hippytaff on 2010-11-19
It's always worth trying
```

rfkill unblock all

```
 
and looking into -
 
does the usb dongle need modeswitching? if ```
 lsusb 
``` recognnises your dngle as a storeage device then look into usb_modeswitch
 
do some drivers need blacklisting? sometimes when ralink drivers are installed other drivers need blacklisting due to driver conflicts.
 
:-)
 
Let us know how you get on :-)

---

### Post by rashid_sohaib on 2010-11-19
Thanks grahammechanical & Hippytaff for your responses. 

Here's what I did tonight:

[LIST=1]
[*]Decided to install the Windows Driver for SMCWUSBS-N3 using ndiswrapper
[*]Installed wicd
[*]Rebooted
[*]wicd is able to see the ra0 interface and the USB Wifi dongle and successfully scans all available AP
[*]However, when I try to connect to my AP - it says bad password (trust me, I am keying in the correct password bcoz the same password works from my laptop)
[*]I get the same result for WEP as well as WPA1 & WPA2 - bad password
[*]Network Manager (NM Applet) still cannot detect the ra0 at all
[/LIST]
Regards
- Rashid

---

