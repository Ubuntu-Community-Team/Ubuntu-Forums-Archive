---
title: "ELO Touch Systems Touch Screen Monitor Trouble"
date: 2009-03-03
forum: Multimedia Software
---

### Post by elesjuan on 2009-03-03
Wasn't sure if this was the right place to post my problem.

I've just installed Ubuntu 8.10 on an Athlon 64 4000+ w/1gb PQI 2,2,2,2.5 ram, Nvidia GeForce ti4200 dual display card.

Basically here is what I'm attempting to accomplish.  I'd like the primary display output on my ELO Touch Systems USB Touch Screen 15" monitor which is mounted in my media center, the second output would be hooked to my 50" HDTV.  While I know this isn't "HD" out of DB15M-S it'll work for what I'm wanting to do.  Basically I'd like to control MythTV on the touch screen monitor and have what I'm playing display on the large TV while playing through my home theater system.

The Touch screen works after the install, but I can not for the life of me get it calibrated.  Basically I hooked it all up like I wanted it and started the install.  Installation took care of everything except the Y plane of the touch is reversed....  I touch in the center and tahts where the mouse goes, go down and the mouse moves up.

I've spent about 15 hours on google searching for a solution, downloaded drivers directly from ELO, their calibration program just crashes on me.  I likely don't have some libs installed that it requires, but doesn't really give me specific info about dependencies.  

Anyone have any ideas how to get a calibration program functioning?

---

### Post by mikey.duhhh on 2009-03-23
I'm having some problems with this, too.  Here is what someone who's installed over 50 of them has told me:  

> You should not need any kernel drivers to enable touch screen input
through the serial port.  You just need the elographics driver for
X.org (which should be part of the core distribution).

Section "InputDevice"
   Identifier      "Touchscreen"
   Driver          "elographics"
   Option          "Device"                "/dev/ttyS1"
   Option          "MinX"  "412"
   Option          "MaxX"  "3689"
   Option          "MinY"  "551"
   Option          "MaxY"  "3535"
   Option          "UntouchDelay"  "10"
   Option          "ReportDelay"   "10"
   Option          "SendCoreEvents"        "true"
EndSection

Sorry for not getting back to you sooner.

Section "ServerLayout"
   Identifier  "Simple Layout"
   Screen      "Screen 1"
   InputDevice "Mouse1" "CorePointer"
   InputDevice "Keyboard1" "CoreKeyboard"
   InputDevice "Touchscreen" "SendCoreEvents"
EndSection

One other section that might be of interest is this module section

Section "Module"
       Load        "dbe"

       SubSection  "extmod"
               Option    "omit xfree86-dga"
       EndSubSection

       Load        "freetype"
EndSection

I don't recall why we put it in, but I am sure there was a reason.

However, if you have downloaded, compiled, and installed the unified elo driver there is a control panel that will perform calibrations.  Just cd to /etc/opt/elo and run ./cpl and the panel should open.

I haven't had access to the computer with the touch screen this weekend.  I'll probably be able to get to it tomorrow sometime.  E-mail me if you need more help.  And when I get this working properly I plan on posting a how-to.

---

### Post by prsmk on 2009-05-29
The USB drivers provided on Elo website are closed source drivers(non GPL). Non GPL USB drivers are not allowed in the Linux kernel beyond 2.6.25. You cannot use those drivers with Ubuntu 8.10 or 9.04, as they have kernel versions beyond 2.6.25.

Contact Elo's Tech support and request a driver for Ubuntu 8.10 distribution.

[http://www.elotouch.com/Forms/Support/tech_sup_us.asp](http://www.elotouch.com/Forms/Support/tech_sup_us.asp)

Hope this helps.


> **elesjuan said:**
> Wasn't sure if this was the right place to post my problem.

I've just installed Ubuntu 8.10 on an Athlon 64 4000+ w/1gb PQI 2,2,2,2.5 ram, Nvidia GeForce ti4200 dual display card.

Basically here is what I'm attempting to accomplish.  I'd like the primary display output on my ELO Touch Systems USB Touch Screen 15" monitor which is mounted in my media center, the second output would be hooked to my 50" HDTV.  While I know this isn't "HD" out of DB15M-S it'll work for what I'm wanting to do.  Basically I'd like to control MythTV on the touch screen monitor and have what I'm playing display on the large TV while playing through my home theater system.

The Touch screen works after the install, but I can not for the life of me get it calibrated.  Basically I hooked it all up like I wanted it and started the install.  Installation took care of everything except the Y plane of the touch is reversed....  I touch in the center and tahts where the mouse goes, go down and the mouse moves up.

I've spent about 15 hours on google searching for a solution, downloaded drivers directly from ELO, their calibration program just crashes on me.  I likely don't have some libs installed that it requires, but doesn't really give me specific info about dependencies.  

Anyone have any ideas how to get a calibration program functioning?

---

