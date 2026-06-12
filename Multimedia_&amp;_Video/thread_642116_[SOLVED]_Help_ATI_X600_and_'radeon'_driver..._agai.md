---
title: "[SOLVED] Help ATI X600 and 'radeon' driver... again"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Toshick on 2007-12-16
Hello all. I've spend a lot of time surfing the Net. There a lot of how-tos about proprietary ati drivers and a few manuals about open source. I've done everything regarding ubuntu's how-to but it still doesn't work. I have the following error:

Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".

Fatal server error:
no GLX visuals available

in Xorg.0.log no errors.

Can somebody help? 


I attched my .log files and xorg.conf
I needed to archived my .log file becouse it exceeded forums max. file size. 

Who knows what it can be?

Thank you in advance.

---

### Post by ahbrikaa on 2007-12-16
nice topic man thanks

---

### Post by acoustibop on 2007-12-16
So why not try the ATI proprietary fglrx driver, Toshick?  I'd recommend the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") guide for this.

---

### Post by vanadium on 2007-12-16
My ATI X600 radeon worked after a fresh install with the open source drivers. These do not properly support 3D acceleration, preventing one to run programs like celestia. In Gutsy, System - Administration - Restricted drivers manager allows to install the proprietary ATI driver with one mouse click. This allows me to run 3D applications. WHat did you try so that your system is currently broken? One way to rescue is sometimes to copy back your original /etc/X11/xorg.conf, so you can have a fresh start in trying to change the setup.

---

### Post by Toshick on 2007-12-16
I've tried proprietary driver already. I reinstall it 3 times per week, becouse a had title bars dissappeared, than i culdn't switch to another workspace and many others graphical artifacts with it. When i've installed open source driver i have everything work, but i can't enable DRI :(

---

### Post by Toshick on 2007-12-17
I've find solution for this. You should remove line:
. /etc/ati/ati-fglrx.sh  # Do not modify - set by ATI FGLRX
from /etc/profiles file.

But my Direct rendering is not working anyway, but it is another topic.
Thanks all for help and support. 
[SOLVED]

---

