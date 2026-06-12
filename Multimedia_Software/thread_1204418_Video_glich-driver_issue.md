---
title: "Video glich-driver issue"
date: 2009-07-04
forum: Multimedia Software
---

### Post by Sankou on 2009-07-04
I just recently install Ubuntu 8.04 and I'm dual booting with windows xp64. I'm trying to get my video card drivers install correctly and i'm running into a lot of issues. I have a Radeon 4670. I know it can handle anything I throw at it, but I think I installed the drivers wrong. When I log in the the screen glitches a bunch. It stays on a blank screen for about 3 minutes and just spazzes out. Black bars jump around the screen and it freezes up a bit.  Then it logs me in. Once I'm logged in, the video works okay, but not good. Compiz runs like crap-wobbly windows are glichier than anything I've ever seen. When I installed the drivers, I downloaded the .run file from the ati web site and installed it. I was just wondering if there is a way to uninstall all the video drivers except the ones that Ubuntu comes with be default and start again.

---

### Post by pme 72 on 2009-07-06
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

You can try that. Hardy 64 bit worked fine for me with a Radeon xpress 200 integrated card and a Radeon x1550 add on card (both open source and proprietary drivers for both cards) but when I upgraded to an HD4550 the card was not recognized. I tried the open source driver, the radeonHD driver and also the proprietary fglrx driver with no success. To be fair I was having an issue with the start up screen displaying the Ubuntu logo improperly and I probably made some errors trying to repair that. I am not an old pro at this. I finally gave up on my 8.04 64 bit installation. The HD4550 was recognized by 9.04 Jaunty.

---

### Post by mindviper on 2009-07-09
My Ubuntu 8.10 64bit and I got radeon 4670.

[http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-amd64.iso](http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-amd64.iso)

I installed the ati driver from the ubuntu system > administration > hardware driver window, proprietary fglrx driver. Works fine. Few glitches when watching h.264 video. I believe it's called the tearing effect. No such major problems as what you described.

I think it was even suggested for Radeon 4670 somewhere to install Ubuntu 8.10 or later. That 8.04 is too old.

---

