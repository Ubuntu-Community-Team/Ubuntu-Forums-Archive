---
title: "Detect modem prolink"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by ragonz on 2010-06-19
I've read so many posts discussing 'bout how to install prolink modem. I've followed all the posts instructions, but still none of them could help me to detect this modem.

I've done all the steps explained in this link
Code:

[http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html](http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html)

in which many people succeded by following those steps. i already installed the latest usb_modeswitch, wvdial, gnome-ppp and all the things explained on that link.

First of all, i do all the steps explained on that nmxlaxaman link n then i restart my laptop. After then, without modem being plugged, i check with lsusb command n return

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:c052 Logitech, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 004: ID 0000:0000
Bus 004 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

Then, i plug the modem n check again with lsusb command, n it returned

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:c052 Logitech, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 004: ID 1e0e:f000
Bus 004 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

there's a change in line 7, which means new device in usb port is detected. But after that, i check with wvdialconf command it says that no modem is detected. I try to check in network manager, but nothing deffrent. i dnt know what to do, some post said try to shut down the PC in 2 mins, n the modem will be detected. But not work on me. I just wonder that this modem is detected as new device in usb port but not being dtected as modem. Any suggestion?

Regards
Ragonz

---

### Post by alexfish on 2010-06-19
hi

according to the last listing the device shows it in an un-switched state

see below
########################################################
# Option iCON 210
# PROLiNK PHS100 (various looks)
# Hyundai Mobile MB-810
#
# One report of switching with DetachStorageOnly. Needs at least
# a second to settle before binding to usbserial
#
# Contributor: wahlm, Peter Kraker, Pakdhetimin Sekum

;DefaultVendor= [COLOR=Blue] 0x1e0e[/COLOR]
;DefaultProduct= [COLOR=Blue]0xf000[/COLOR]

;TargetVendor=   0x1e0e
;TargetProduct=  0x9000

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="555342431234567800000000000006bd000000020000000000000000000000"

# only for reference and 0.x versions
# ResponseEndpoint=0x01

;ResponseNeeded=1

you need to find the 

;TargetVendor=  [COLOR=Blue] 0x1e0e[/COLOR]
;TargetProduct= [COLOR=Blue] 0x9000[/COLOR]

this is not showing in the first listing so I am puzzled by this output

maybe the Modeswitch forum may help

Also of note the device may be an option Icon Device

so while at the usb-modeswitch Site look down till you find the Pharescape Site , They also have a forum , they specialised in Option Icon drivers

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")

HSO driver questions and HowTos consult the fine [Pharscape]("http://www.pharscape.org/") site!

hope this helps

regards

alexfish

---

### Post by ragonz on 2010-06-20
Thx 4 ur replay, i'll try to post this thread on that forum.

Best regards

---

