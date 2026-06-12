---
title: "Possible fix for no network connection in 10.04"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by pterosky on 2010-08-13
EDIT: Tweaking Network Manager in Startup Applications only seemed to worked -- today it didn't...
Using a network card, not the one integrated in the motherboard, did!

My fresh 10.04 64-bit install didn't automatically connect my wired network connection; The two green balls were rotating, but not connecting. After reboot I had to manually disconnect the network cable, re-insert it and select "eth0" from the connection icon in the upper right top panel.

I can't remember where, but I read that 4GB of RAM on a  64-bit machine can make Ubuntu "too fast", so that the network process isn't completed during boot.

I had previously added Audacious to my Startup Applications, but it didn't start up after boot. Adding this in the "Command" box fixed it: ```
bash -c 'sleep 5; audacious'
```

And it turns out it also can fix the Internet connection, so far at least: Go to Preferences -> Startup Applications -> Network Manager -> click Edit. Then change "Command" from ```
nm-applet --sm-disable
``` to ```
bash -c 'sleep 5; nm-applet --sm-disable'
```

This is only a temporary workaround, until the bug is fixed, but it is better than the unplug/replug routine 8o)

---

