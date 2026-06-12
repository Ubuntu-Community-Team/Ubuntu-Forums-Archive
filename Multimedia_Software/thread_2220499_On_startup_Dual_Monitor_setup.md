---
title: "On startup Dual Monitor setup"
date: 2014-04-28
forum: Multimedia Software
---

### Post by uwe-bungto on 2014-04-28
_**For Ubuntu Studio 14.04LTS**_

On start up My dual monitors were cloned, ie same screen on both.
I think I have a simple way of preventing this if it is not wanted.

Open Settings manager,  click on ARandR. Setup the screen the way you like it. Save the layout call it what ever; "screen" for example . The file can be found in  your home/.screenlayout/screen.sh

Open Sessions and Startup -> Application Autostart -> add

Locate the screen.sh  file in .screenlayout.
This will be added to autostart.

If everything works your default screen should be availabe on start up.

---

