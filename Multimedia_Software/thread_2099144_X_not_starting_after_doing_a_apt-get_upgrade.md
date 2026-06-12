---
title: "X not starting after doing a apt-get upgrade"
date: 2012-12-28
forum: Multimedia Software
---

### Post by kerryhall on 2012-12-28
Relatively fresh install of 12.04. I think apt upgraded my video drivers and broke everything. Booting up I get a black screen. I can't ctrl alt F1, that just gives a black screen too. I have to reboot via the REISUB trick.

I can't boot up into failsafe x mode either via failsafe menu, It just hangs after pressing enter. The only way I can get dropped to a prompt is by doing sysrq + REI after selecting that menu option. (what?)

Once I managed to get shell access, I took a look at the Xorg.0.log. I get:

"no screens found"

uh...what?

Tried removing xorg.conf entirely (made a backup of course) as recommended here:
[https://bbs.archlinux.org/viewtopic.php?pid=922218](https://bbs.archlinux.org/viewtopic.php?pid=922218)
No such luck. 

I can't post any error logs though because I can't get my damn system to boot with any way to access networking without the stupid gnome network manager. I can grep for relevant data though. Video card is a Geforce 460.

Thanks!!

---

### Post by kerryhall on 2012-12-28
Fixed by changing "vesa" to "nouveau" in /etc/X11/xorg.conf

So uh....why the $^&# is vesa no longer a fallback driver?

---

