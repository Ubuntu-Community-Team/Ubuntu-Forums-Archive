---
title: "How to use the HUAWEI E176 USB Modem in ubuntu 8.04?"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by frobayoh on 2010-04-25
Hello for everyone.

I have an usb modem (HUAWEI E176), for to get conected to internet. I want to know what do I have to do for getting conected to internet using this modem in linux.

I have all the necesary information (phone number, pin, operator and more) and, I have installed Ubuntu 8.04.

Thanks.

---

### Post by alexfish on 2010-04-25
Hi
 

 there is a thread here the devices may differ but the basics are the same , the important bits are the ID's of the device ( if you get stuck consider contacting GeorgeVita he has a lot of experience with 8.04)
[http://ubuntuforums.org/showthread.php?t=1091189](http://ubuntuforums.org/showthread.php?t=1091189)
 
if the device is  not recognised
 

 try usb mode switch  
 

 latest debian this is easiest for a novice
 

 [http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)
 

 

 Source

 [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)
 

 if you are a novice at this seek help
 

 The latest release version is **1.1.2**. The tar archive contains only the source. I used libusb-0.1.12 but the "compat" library from libusb-1.0 is now working smoothly too.
 **Important:** you need the data package as well !!
Changes and updates to the configuration data may happen more often than new releases; most of the valuable knowledge about devices is contained in these files. That's why it is provided separately.
 
[LIST]
[*]Download     [usb-modeswitch-1.1.2.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.2.tar.bz2"),     dated from 2010-04-18; a Debian (Xandros/Ubuntu) package should be     available soon at the [Debian     Repository]("http://packages.debian.org/usb-modeswitch"). Many architectures are supported there (like amd64     or ia64).
[*]Download the [usb-modeswitch-data]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100418.tar.bz2")     package (2010-04-18 . It contains the device database and the rules     file, including full paths. You can use this package with program     releases from 1.0.3 upward, but the latest devices and features may     require the most recent program release too.
[*]Only for reference: the latest     [usb_modeswitch.setup]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup")     (formerly known as usb_modeswitch.conf, 2010-04-18  this is a     collection of all device setups with their respective contributors;     you can use it as a starting point if you want to make a new device     working.
[*]Don't forget [libusb]("http://libusb.wiki.sourceforge.net/")     if it's not on your system. In most distributions there is most     likely a package named "libusb-dev" or "libusb-devel".     Choose the legacy version (0.1.12) or the "compatible"     package from libusb-1.0; last time I checked it had the version     number 0.1.13.
[/LIST]
 


 consider installing  
 

 gnomeppp this is a front end to wvdial
 

 if you get connected and gain experience:
 

 also consider upgrading the network manager gnome (ver x) and also make sure the network manager (daemon matches) IE network manager ver = network manager gnome and  check dependencies
 

 lists are here
 

 [http://packages.ubuntu.com/search?keywords=network-manager](http://packages.ubuntu.com/search?keywords=network-manager)
 

 

 Keep copies of the downloads in case it goes wrong IE download your original version NM as well
 

Read everything and digest before committing


Regards


alexfish

---

