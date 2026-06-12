---
title: "ATI radeon Xpress 200 brightness problem"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by supsup on 2006-06-03
After installing Ubuntu, my screen's brightness is extremely high. Changing the  brightness on the monitor does not help. 
I tried fglrx and oss drivers. Some correction could be done by gamma settings.
Does anyone has this problem? and solution of cause.

---

### Post by lych on 2006-09-21
Hi,

I'm experiencing the same problem with my Radeon Mobility X600 video card and LCD screen. Also tried both default and fglrx drivers - nothing helps, brightness on my screen is still VERY high. 

Right now I've set Gamma 0.5 (it is 1 by default) in the "Monitor" section of my /etc/X11/xorg.conf config, however this is not desired solution. With less gamma it is of course more convenient to watch the screen, however when watching pictures - all pics seem to be too brigh anyway, but when watching movies - picture is too dark.

When using Fedora Core 4,5 there was no such problem. Brightness was ok, but in Ubuntu - i'm having enormous bright screen.

I've heard there should be some options for "backlighting" for monitor, have anybody heard about that?

Also I tried to "sudo  /usr/sbin/dpkg-reconfigure xserver-xorg xserver-xorg-core", answered many questions - but still no luck.

Any help on this matter would be very appreciated.

BTW, SupCup, did you solve this problem somehow?

---

### Post by Pawel on 2006-09-21
Hello!

Do you have TV connected to your computer ?
If yes - try to unplug it and turn on your computer.
The same problem is on Radeon 9200 series but only on fglrx drivers.
But - if it works on FC - i don't know what may cause the problem.
BTW:
 THIS may helps:
[http://www.taupro.com/wiki/ChemBook/LCDdisplayPowerConfiguration](http://www.taupro.com/wiki/ChemBook/LCDdisplayPowerConfiguration)

---

### Post by lych on 2006-09-21
> **Pawel said:**
> Hello!

Do you have TV connected to your computer ?
If yes - try to unplug it and turn on your computer.
The same problem is on Radeon 9200 series but only on fglrx drivers.
But - if it works on FC - i don't know what may cause the problem.
BTW:
 THIS may helps:
[http://www.taupro.com/wiki/ChemBook/LCDdisplayPowerConfiguration](http://www.taupro.com/wiki/ChemBook/LCDdisplayPowerConfiguration)



Thank's for reply.

Actually I do not connect anything to my laptop.
Also I've noticed that when using "fglrx" driver - it is even more brighter that with default "ati" one.
And thank's for the link, I'll check it out.

---

### Post by lych on 2006-09-21
Okey, I've seen that link..
BlankTime, StandbyTime, SuspendTime and OffTime are not actually connected to my problem.
The only interesting thing is in adjusting of brightness via ASUS ACPI module:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
brdown (LCD Brightness Down)
    echo 1 > /proc/acpi/asus/brdown (decrease LCD brightness by one)

brn (LCD Brightness Control)
    echo {0..15} > /proc/acpi/asus/brn (set absolute brightness of LCD display)

brup (LCD Brightness Up)
    echo 1 > /proc/acpi/asus/brup (increase LCD brightness by one)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

But as for my, I have Intel 915GM/PM MB, and brighness adjusting works fine using Function Buttons. 
Yes, they could increase/decrease brightness, however probably I described my issue incorrectly and maybe my problem coserns Contrast adjustment, but not brightness. 
You know, when watching some pictures - all light objects on the pic conflow with the white colour. It is like lack of Contrast on the screen...

---

### Post by diskotek on 2007-11-01
i'm having same problem with ati radeon x200 on feisty fawn. 
OnScreenDisplay of my monitor works flawless, but it still doesn't give me any satisfaction. sometimes it looks like an over-exposed photograph!

---

### Post by diskotek on 2007-11-05
still no gain

---

### Post by rmjokers on 2007-11-07
I have this problem with a radeon Xpress 200 desktop system. When I upgraded from feisty to gutsy, the flat panel suddenly became extremely bright and the fonts are almost unreadable. The standard ubuntu theme is brown and bright white rather than light gray. I cant see many of the UI elements, such as button and tab borders. The fonts look horrible, even with sub pixel hinting because the white is overwhelming the hinting leaving them blurry and blocky. Changing monitor settings helps some, but the fonts still look terrible.

I also tried installing Fedora Core 8 (rc3) and I have the same problem. I am guessing they use the same version of the ATI X driver. Installing the FGLRX driver through the restricted driver manager fixes the display problem, but I would rather not use this driver. Has anyone filed a bug report for this problem?

---

