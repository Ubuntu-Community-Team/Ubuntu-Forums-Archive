---
title: "Menus freeze when selected"
date: 2014-05-15
forum: Mythbuntu
---

### Post by dom7 on 2014-05-15
Hi,
I'm running the latest Mythbuntu 14.04 and I'm using a ATI HD 5450 PCI Express card.  I selected the Appearance to Auto and the Video to VAAPI but it still does not seem to run video acceleration - it seems to use the CPU and lock up.  I have installed fglrx ATI drivers and can run vainfo successfully.  When I select some menus in Myth it freezes now too - even when setting Appearance back to QT and Video to Normal.  I'm at a bit of a loss what to do after 3 mights trying to fix this.  I'd appreciate any help at all.  I have attached my log file from log grabber.  I'm on the verge of getting my chainsaw out to the media pc ....

Thanks.

Dominic.

---

### Post by dom7 on 2014-05-15
I'm wondering if its the same issue these guys are having. It sounds like it. If I press Escape after selecting a menu that is unresponsive it does go back to the main menu. Does anyone know a way around this? Cheers.
[http://ubuntuforums.org/showthread.php?t=1974836](http://ubuntuforums.org/showthread.php?t=1974836)

---

### Post by blm-ubunet on 2014-05-15
I would guess your openGL drivers are broken.
Do you need to use the legacy driver (AMD) with this h/w ?

errors in xorg.0.log w.r.t. glx loading
segfault in one log file..
what is with the alsa errors ? what are you using pcm_snoop for ?
Looks like you have old alsa cruft in asound.conf or similar..

The FOSS radeon driver has very good support for older AMD video cards, arguably better than fglrx.
VAAPI video decode requires you to select openGL video rendering.

The FOSS driver also supports VDPAU & IFAIK this works better* than VAAPI.
You didn't include any mythtv log files..

better*==more support in app & features work.

---

### Post by dom7 on 2014-05-15
Hi. I don't know what pcm snoop is. I also don't know what the alsqla errors are. Must be sound related ?,so it looks like you're recommending uninstalling the Catalyst drivers and installing the Radeon ones? 
Cheers

---

### Post by blm-ubunet on 2014-05-16
This suggests Evergreen is well supported..
[http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)

Lots of good news (for the older h/w) here
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)

Some good news threads here
[http://www.gossamer-threads.com/lists/mythtv/users/561027?search_string=radeon;#561027](http://www.gossamer-threads.com/lists/mythtv/users/561027?search_string=radeon;#561027)

---

