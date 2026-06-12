---
title: "Switching Between 2 Wireless Cards"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by syga on 2009-08-29
I have a Dell laptop with a internal wifi card and also use a high power usb wifi card with a external antenna.

Depending on where I am, I need to switch between the 2 cards. I'm looking for a way to get the internal card to turn off while using the usb card. 

I tried turning the internal card off by the keyboard, but network manager is still picking up signals and tries to connect. 

I don't really want to blacklist anything if I don't have to. 

Is there a simple utility that will get newtwork manager to disregard my internal card when I don't want it on?

---

### Post by tgalati4 on 2009-08-30
Program a hotkey to run a script: (Let's call it rabbitears.sh)

Assume your CAT5 is eth0, Wireless 1 is eth1, Wireless 2 is eth2

---------------------- rabbitears.sh-------------

#/bin/sh
#Script to turn off internal wireless
ifconfig eth1 down
ifconfig eth2 up
/etc/init.d/networking restart

---------------------------

sudo chmod +x rabbitears.sh

Assign hotkey:  Alt-F6 (Preferences--Keyboard Shortcuts)

sudo /home/syga/rabbitears.sh

Assign Alt-Shift-F6 to run a script that does the opposite.

---

