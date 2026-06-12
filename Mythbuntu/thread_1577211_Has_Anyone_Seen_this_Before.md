---
title: "Has Anyone Seen this Before?"
date: 2010-09-18
forum: Mythbuntu
---

### Post by mattneub on 2010-09-18
Just built a single backend/frontend machine and installed Mythbuntu with one pcHDTV 5500 capture card, muddled through and eventually got it all working initial install.

However whenever machine is turned off and I go to "Watch TV" I get a message, *"MythTV is currently using all inputs, but there are no active recordings."*

I can only get past this if I go to the backend settings and and remove/reinstall the capture card, then it will work fine again until the machine gets turned off.  This is a workaround but it would be nice if this didn't need to happen every time I turned the machine off.

Any thoughts?

---

### Post by ian dobson on 2010-09-18
Hi,

Sounds as if the backend is starting too early (before the tuners are up). If that's the case then just change the startup configuration file /etc/init/mythtv-backend.conf so that the start on line looks like this:-

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)

The udev-finish event means that the startup controller (upstart) only starts the backend after udev has finished.


Note: This information is good for 10.04, older versions don't use upstart for starting mythtv-backend.

EDIT: If your running 10.04 then maybe go over to using the autobuilds/fixes branch, the fix is already in it with many others :) Have a look here: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Regards
Ian Dobson

---

