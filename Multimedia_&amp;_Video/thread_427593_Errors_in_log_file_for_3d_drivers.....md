---
title: "Errors in log file for 3d drivers...."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by mithridate on 2007-04-29
Hello Ubuntu community, although this is my first post i have been coming here for some time looking for information on problems i might share with other uses.   What a fantastic wealth of information these forums are.

And so its my turn to post a issue, not huge in magnitude mind you.

I'm running Kubuntu 7.04 and been quite a noobie, i have finally got round to investigating the log files for any errors that might need attention and in the x.org log and there are 21 warning messages and 3 error messages.  i have googled some of these but haven't really come up with anything.

I'm not running Beryl or anything else apart from the standard KDE and have not installed Ati's proprietary drivers either.  I dont experience any video problems (although i haven't got round to playing 3D games or anything else that is intensive) but i would like to find the root to these error messages.


**[COLOR="SandyBrown"]Warning Messages [/COLOR]**
	warning	RADEON: No matching Device section for instance (BusID PCI:1:0:1) found

	warning	RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled

	warning	RADEON(0): DRI init changed memory map, adjusting ...

	warning	RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000

	warning	RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf07ff000

	warning	AIGLX: 3D driver claims to not support visual 0x23

	warning	AIGLX: 3D driver claims to not support visual 0x24

	warning	AIGLX: 3D driver claims to not support visual 0x25

	warning	AIGLX: 3D driver claims to not support visual 0x26

	warning	AIGLX: 3D driver claims to not support visual 0x27

	warning	AIGLX: 3D driver claims to not support visual 0x28

	warning	AIGLX: 3D driver claims to not support visual 0x29

	warning	AIGLX: 3D driver claims to not support visual 0x2a

	warning	AIGLX: 3D driver claims to not support visual 0x2b

	warning	AIGLX: 3D driver claims to not support visual 0x2c

	warning	AIGLX: 3D driver claims to not support visual 0x2d

	warning	AIGLX: 3D driver claims to not support visual 0x2e

	warning	AIGLX: 3D driver claims to not support visual 0x2f

	warning	AIGLX: 3D driver claims to not support visual 0x30

	warning	AIGLX: 3D driver claims to not support visual 0x31

	warning	AIGLX: 3D driver claims to not support visual 0x32




**[COLOR="Red"]Error Messages: [/COLOR]**
	error	xf86OpenSerial: Cannot open device /dev/input/wacom

	error	xf86OpenSerial: Cannot open device /dev/input/wacom

	error	xf86OpenSerial: Cannot open device /dev/input/wacom


These were obtained from the  KsystemLog viewer.

EDIT: silly me, i should have said video card is a ATi X850 XT (AGP) 

Many Thanks

---

