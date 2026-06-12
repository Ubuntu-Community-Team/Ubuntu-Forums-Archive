---
title: "odd behaviou in network applet: home no, college yes"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by ubunny on 2009-07-14
Jaunty 9.04 user.

This isn't an error just quirky behaviour as I have a workaround.

I have the Network Manager nm-applet that auto loads but does not connect to my home wep wifi with the supplied information.  So I run a script with iwconfig and dhclient calls plus the wep key and that works.  Network Manager doesn't work at home but it does connect at college with mschapv2 information setup just fine.

There's no reason why one should work and the other requiring a script.  Note I have to turn nm off (uncheck Enable Wireless) before the script can work.

anyone else experience this?

cheers

---

### Post by ubunny on 2009-07-14
any way to disable "Enable Wireless" on boot up for the nm-applet?  I have to keep unchecking it in order to run my script to connect.  If instead it was disabled on startup then I could have my script run on startup as well, removing a manual step.  (script works, nm-applet doesn't at home only at college)

I see that nm-applet has a switch --sm-disable but I can't find any other information regarding other switches.  

How to uncheck Enable Wireless so it saves this setting.  If I save the session it doesn't save this state change.  Any hints?

oh, and what does -sm-disable do anyway?

Cheers

---

