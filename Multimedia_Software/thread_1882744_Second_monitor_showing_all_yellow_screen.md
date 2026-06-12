---
title: "Second monitor showing all yellow screen"
date: 2011-11-17
forum: Multimedia Software
---

### Post by AlexBaranosky on 2011-11-17
Hello,

I recently decided to try to set my Ubuntu 10.04 desktop up with dual monitors.

I bought a new graphics card (Radeon HD 5450) and installed it.  I plugged my two monitors into the new card: my larger monitor via DVI and the other via VGA.  When I booted up Ubuntu showed my main monitor fine, but not the second. After going to System > Preferences > Monitors, and detecting the second, and setting it to "on", Ubuntu offered to change a config file, so I said "yes". Now the secondary monitor is showing only a single shae of yellow...

What can I do to correct this?

Thanks,
Alex

---

### Post by AlexBaranosky on 2011-11-17
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	3600 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by AlexBaranosky on 2011-11-17
Does anyone at least have a resource I could be directed to to help with this situation?  

Thanks!
Alex

---

### Post by AlexBaranosky on 2011-11-18
The odd thing is that the monitor that is showing as all yellow was working totally fine as my primary monitor just a day ago.  So it is highly unlikely that there is actually anything wrong with it.  

:confused:
:popcorn:

---

### Post by AlexBaranosky on 2011-11-18
Rebooted my computer, and at one of the boot menus reconfigured my monitors.  The secondary started to work, during the boot up process, but as soon as the purple Ubuntu screen showed, it showed nothing.  I then went to System > Preferences > Monitors and re organized the monitors.  After setting them up again, now my monitor is showing an all black background (it's on, just a solid black color)

---

### Post by AlexBaranosky on 2011-11-18
*bump*

---

### Post by AlexBaranosky on 2011-11-19
*bump*

---

