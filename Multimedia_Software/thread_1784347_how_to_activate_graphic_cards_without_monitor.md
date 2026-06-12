---
title: "how to activate graphic cards without monitor?"
date: 2011-06-16
forum: Multimedia Software
---

### Post by cc129 on 2011-06-16
Hi, I wonder is there any way to activate the graphic cards without a monitor?
It seems in xorg.conf, a "Device" had to be referenced by a "Screen" to have it activated.

I wonder is there any other way to activate a graphic cards without monitor connected to it?

Any suggestion would be very appreciated!!!!

---

### Post by BicyclerBoy on 2011-06-17
With nvidia cards (except tesla) you must have an attached monitor or forced monitor/x screen.

To force a non-existent monitor use can use the following in the /etc/X11/xorg.conf file

Option "ConnectedMonitor" "VGA"
you'll need the screen & device sections..

Tesla & Quadra can use
Option "UseDisplayDevice" "none"

You can do the same from terminal cmd using nvidia-settings with cmd options..

---

