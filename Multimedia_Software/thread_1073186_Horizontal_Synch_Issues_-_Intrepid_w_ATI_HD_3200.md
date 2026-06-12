---
title: "Horizontal Synch Issues - Intrepid w/ ATI HD 3200"
date: 2009-02-18
forum: Multimedia Software
---

### Post by cberger on 2009-02-18
Folks,

I know ATI drivers suck.  However, went with a Foxconn mobo with integrated HDMI using ATI's HD 3200 chipset.  Going for low power consumption and a tight case without the need to add a video card.

Installed Intrepid and am very happy with installation and features.  Getting HDMI audio was a challenge, as well as some other items, but were resolved through Google searching.  Mythbuntu certainly has come a LONG way since 6 and 7.

That said, I'm stuck trying to get video without horizontal tearing.  As others have posted here and elsewhere, video without much movement works fine.  As soon as the images get "busy", horizontal tearing occurs (a portion of the screen lags behind another portion of the screen causing a noticeable 'rift' between the two).

I've tried the standard 'restricted-drivers' that come with the 8.10 repo for ATI.  I've also upgraded to the latest 9.1 ATI drivers following the Ubuntu installation guide.  No errors occurred during the upgrade.  After the upgrade, all seems fine with the exception that screen tearing still occurs.

As per the Ubuntu installation guide for the new ATI drivers, I've added an option line to the /etc/X11/xorg.conf file in the Device section:
'Section "Device"
'  Identifier "aticonfig-Device[0]-0"
'  Driver     "fglrx"
'  Option     "TexturedVideo" "on"
'  Option     "PCI:1:5:0"
'EndSection


I'm completely at a loss as it seems everything I do still results in this issue.  The issue appears in mplayer, xine and mplayer within Mythtv all playing content from a locally attached DVD drive.

Not to get too off topic, but I understand from other threads that using Xv support allows for smooth transitions in video content.  Not sure how I tell if Xv is used or if it's even available with the latest 9.1 ATI/AMD drivers.  Thought it was based on the ATI website.

Thanks in advance!
Clint

Dual core AMD64 X2 5400
Foxxconn A7GM-S AM2 780G HDMI
2GB Mushkin RAM
Folks,

I know ATI drivers suck.  However, went with a Foxconn mobo with integrated HDMI using ATI's HD 3200 chipset.  Going for low power consumption and a tight case without the need to add a video card.

Installed Intrepid and am very happy with installation and features.  Getting HDMI audio was a challenge, as well as some other items, but were resolved through Google searching.  Mythbuntu certainly has come a LONG way since 6 and 7.

That said, I'm stuck trying to get video without horizontal tearing.  As others have posted here and elsewhere, video without much movement works fine.  As soon as the images get "busy", horizontal tearing occurs (a portion of the screen lags behind another portion of the screen causing a noticeable 'rift' between the two).

I've tried the standard 'restricted-drivers' that come with the 8.10 repo for ATI.  I've also upgraded to the latest 9.1 ATI drivers following the Ubuntu installation guide.  No errors occurred during the upgrade.  After the upgrade, all seems fine with the exception that screen tearing still occurs.

As per the Ubuntu installation guide for the new ATI drivers, I've added an option line to the /etc/X11/xorg.conf file in the Device section:
'Section "Device"
'  Identifier "aticonfig-Device[0]-0"
'  Driver     "fglrx"
'  Option     "TexturedVideo" "on"
'  Option     "PCI:1:5:0"
'EndSection


I'm completely at a loss as it seems everything I do still results in this issue.  The issue appears in mplayer, xine and mplayer within Mythtv all playing content from a locally attached DVD drive.

Not to get too off topic, but I understand from other threads that using Xv support allows for smooth transitions in video content.  Not sure how I tell if Xv is used or if it's even available with the latest 9.1 ATI/AMD drivers.  Thought it was based on the ATI website.

Thanks in advance!
Clint

Dual core AMD64 X2 5400
Foxxconn A7GM-S AM2 780G HDMI
2GB Mushkin RAM

---

### Post by cberger on 2009-02-18
Sorry, submitted this request and posting the message hung.  Re-attached again and pasted my request.  Must have pasted twice....sorry!

---

