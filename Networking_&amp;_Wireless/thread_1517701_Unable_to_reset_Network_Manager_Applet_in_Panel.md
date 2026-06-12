---
title: "Unable to reset Network Manager Applet in Panel"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by shanmugamt on 2010-06-25
Accidentally I removed the NM Applet from the panel and I am trying to reset it. When I right-click on the panel and "Add to Panel", I couldn't see Network Manager. Hence I couldn't connect to the available wireless network. 
I am able to add Network Monitor, which is similar to Network manager, but this just displays info about current network.
Any help to reset my Network Manager on Panel would be much appreciated.
Thanks,
Shan

---

### Post by _Mark_ on 2010-06-25
This may work for you add a notification area to the panel, should be empty, then in a terminal run
> nm-applet --sm-disable

Then that should put NM into that notification area, is a bit of guess work so may not work

---

### Post by shanmugamt on 2010-06-25
This didn't help me.
Here is the result:

$ nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2472): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by _Mark_ on 2010-06-25
Ok either reboot or in terminal
> sudo killall nm-applet

and then start it again with the previous command

---

### Post by Iowan on 2010-06-25
> **shanmugamt said:**
>  When I right-click on the panel and "Add to Panel", I couldn't see Network Manager. Try adding a "Notification area".

---

### Post by shanmugamt on 2010-06-27
Great Iowan.  Thanks much..This solved my problem....
Thanks everyone..

---

