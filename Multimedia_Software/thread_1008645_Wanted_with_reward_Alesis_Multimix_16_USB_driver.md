---
title: "Wanted with reward: Alesis Multimix 16 USB driver"
date: 2008-12-11
forum: Multimedia Software
---

### Post by havedampton on 2008-12-11
Hello!

I'm a professional musician who DESPERATELY wants to use my linux system to record using my Alesis Multimix 16 USB 2.0 mixer/audio interface, but alas, there is no linux driver provided by Alesis.  There IS, however, a Mac driver available here:

[http://www.alesis.com/contentmgr/showdetails.php/id/10166]("http://www.alesis.com/contentmgr/showdetails.php/id/10166")

and older mac drivers here:

[http://www.alesis.com/contentmgr/showdetails.php/id/1175/tt/5]("http://www.alesis.com/contentmgr/showdetails.php/id/1175/tt/5")

I'm no computer genius, but I believe the Mac OS is basically a linux OS with some proprietary additions/subtractions so to my feeble understanding, wouldn't the Mac driver just need a slight bit of "rewiring" to be able to work with linux?

Any help would be greatly appreciated, and there's an older 10GB ipod waiting at my house for anyone who can make this work for me along with a link on EVERY one of my websites AND credit on any albums recorded (along with free copies, of course.)

PLEASE-- I DON'T WANT TO USE WINDOWS!!!!!

---

### Post by albinootje on 2008-12-11
Because i was curious about it, i searched in a search-engine.
This [http://tracker.ardour.org/view.php?id=2466](http://tracker.ardour.org/view.php?id=2466)
doesn't look good. See comment (0005390)

Some months ago a friend of mine brought along some mixer.
I wanted to try it with Ubuntu, i plugged it in, and after a little while i could record something in audacity. (I think i had to do "sudo update-usbids before it was properly recognised)

I don't remember the brand name from that mixer, but i assume that usb 1.x for some mixers could work in Linux.

I think your options are :
1) ask the company to provide more details and write a driver for Linux.
2) find a programmer who writes a Linux driver by somehow reverse-engineering communication (in MacOSX or MS-Windows) with the mixer.
The programmer will need physical access to such a mixer as you have.
For example here's a programmer who writes Linux drivers for cash
[http://www.bitwizard.nl](http://www.bitwizard.nl) (check : Linux Device Driver Service)
3) buy an apple computer and use both MacOSX and Linux
4) try the Hackintosh on your pc and see whether it works with that
  (I think this is risky legally speaking, even when you have a MacOSX
  license)
5) get a mixer-device which is supported well by Linux

Using the MacOS driver in Linux is not an option unless the source code of that driver would be open source. And i assume that using the windows driver with Ndiswrapper in Linux wouldn't work because my impression is that Ndiswrapper focuses on wifi cards, but i could be wrong of course.

---

### Post by razy60 on 2008-12-12
Have you looked into **Ubuntu Studio**, its specifically designed with media content(to a professional level from what i have read) in mind, so may have the drivers and or  links you require.:guitar:


Raz

---

