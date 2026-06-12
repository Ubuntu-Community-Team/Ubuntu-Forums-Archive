---
title: "working fglrx driver but I also want failsafe graphics mode"
date: 2013-09-15
forum: Multimedia Software
---

### Post by Handssolow on 2013-09-15
I want a failsafe graphics gui to fall back on whilst I'm working with fglrx drivers for a Radeon HD7950. I've just put this in my son's desktop, it's a recent fresh install of 12.04 LTS 64bit on a SSD, initially with a Radeon HD7750. AMD Phenom x6 1090T, monitor a Liyama North America 23" X82380HS with 1920x1080 (16:9).

I'm using Ubuntu's Hardware Additional Drivers and with both cards each time I've noticed the message, drivers activated but not used. To work on this problem I'll probably need to purge the old fglrx driver bits and pieces and reinstall a fresh fglrx driver but I don't want to be left working with only a CLI. I've already purged fglrx once which got back a normal boot up but I'm thinking next time it wont and I've have no failsafe graphics GUI mode in reserve.

xorg.conf.failsafe file looks normal with the vesa driver specified.
var/log/Xorg.failsafe has-
module glx loaded
GLX extension
vesa loaded 
then
vesa ignoring device with bound kernel driver
Falling back to old probe method for vesa
unloadmodule vesa
screen (s) but none has a usable configuration
Fatal server error
no screens found

I've no graphics problem running a live CD of 12.04.
It's been reported that lightgm doesn't work so well with a SSD. Adding a 2 second delay in lightgm.conf didn't help.

Any suggestions?

---

### Post by Handssolow on 2013-09-16
Update, I bit the bullet, purged fglrx and re-installed (see link below), instead of using Hardware Additional Drivers. I did not reboot until I had removed and re-installed the driver.
I worked on the basis that if I lost the GUI in the process, another purge of fglrx would bring a GUI back.
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Part of the reason for the re-install was Hardware Additional Drivers had reported the fglrx driver activated but not in use. After the manual reinstall it shows it is activated and in use. fglrxinfo and the AMD Catalyst Control Centre seem to be no different than before. I conclude as others have done that it looks like here there is a bug in Hardware Additional Drivers, it reports that the driver isn't in use when it is.

Whlist not solved I have for now avoided needing to use a failsafe graphics mode. Moving on, there are other issues I have with the fglrx driver which I am working with.

---

