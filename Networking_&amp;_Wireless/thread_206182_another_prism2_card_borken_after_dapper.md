---
title: "another prism2 card borken after dapper"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by Random Babble Generator on 2006-06-29
i'll keep it short

machine's an hp omnibook 500. onboard wifi uses prism2_usb module and _worked like a charm_ in breezy (after a bit of prodding with linux-wlan-ng). dmesg says:

hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
hfa384x_drvr_start: cmd_initialize() failed, result=-5
prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5

the only other "interesting" thing in dmesg output is this:

**** SET: Misaligned resource pointer: cfc493e2 Type 07 Len 0

it appears near the pci lines, but i don't even grok this oh so helpful message. 

i upgraded a month ago and tried everything i googled (not much) and thought up (not very much either) and i'm at my wits end. 

before someone tells me to use ndiswrapper - why i should muck around with windriver emulation, when in breezy my wifi "just worked"? i'd rather plow dapper and downgrade - it will solve a few other irritating problems too. 

so, any ideas?

---

### Post by az on 2006-06-29
Often, when I remove my prism2_usb device to use on another box, I have this sort of trouble.  I have to plug it in and out two or three times before the thing works fine again.  It then goes for months without problems.

You obviously cannot plug and unplug it....

What happens when you run

sudo ifdown wlan0

and then sudo ifup wlan0
?

Also, maybe the firmware for the device was shipped in proviousl versions ( I don'T think so, but I am not 100 percent sure).  Some devices have buggy primary firmware and uses secondary firmware.  There is a linux-wlan-firmware package in Universe that can download (obviously, you need to be connected) the firmware from intersil.

[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware)

---

### Post by Random Babble Generator on 2006-06-29
[QUOTE=azz]

You obviously cannot plug and unplug it....

[/quote]

true.

> 

What happens when you run

sudo ifdown wlan0

and then sudo ifup wlan0
?



apart from "Ignoring unknown interface wlan0=wlan0.", nothing. 

> 

[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware)

installed the package, got the drivers, created and installed a .deb file, rebooted - no change. same things in dmesg.

is there any additional magic needed for making the new firmware work?

---

### Post by az on 2006-06-29
[QUOTE=Random Babble Generator]is there any additional magic needed for making the new firmware work?[/QUOTE]
Not that I know of.  How did you get the thing to work in Breezy?  Did you edit your /etc/network/interfaces file or run a hotplug script?

---

### Post by Random Babble Generator on 2006-06-30
[QUOTE=azz]Not that I know of.  How did you get the thing to work in Breezy?  Did you edit your /etc/network/interfaces file or run a hotplug script?[/QUOTE]

i just loaded prism2_usb module (with 'prism2_doreset=2' option) and prodded it with wlanctl-ng [iface] lnxreq_ifstate ifstate=enable. it started after that. 

but, but - i just looked carefully and it seems that, dmesg error message notwithstanding, the module actually loads, only the interface moved from wlan0 to wlan1. i have _no idea_ why doing ifconfig -a didn't occured to me earlier. ><  i wonder now if it was the installation of a new drivers or if the interface was there all the time. if it was, well - d'oh.

i still cannot connect to access point, but the one i'm trying to reach now is a bit wonky. i'll try to get to the known-good one later on and then we'll see if it works.

---

### Post by Random Babble Generator on 2006-06-30
IT WORKS! :D

*does a happy dance*

i have _no idea_ if it was just me being dumb and not looking around after the interface, or was it this package of azz working its magic. the strange errors persist in dmesg, so - well, i dunno.

anyway, if it was the package, be advised that the package installation gives you only the script (/usr/bin/linux-wlan-ng-build-firmware-deb), which you must launch to get a package. the script needs gcc, subversion and fakeroot to run, and it gives you the raw .deb file (mine is called linux-wlan-ng-firmware-files_0.2.3-1ubuntu7_all.deb) to manually install. running the package gave me strong debian flashbacks. :)

but no matter, i have my wifi now. dapper has been spared from removing. 

azz - thanks _heaps_ for your kind help. :)

---

