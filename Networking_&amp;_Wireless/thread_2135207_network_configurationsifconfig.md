---
title: "network configurations/ifconfig"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by flyingsliverfin on 2013-04-13
I was just wondering about the differences between the "network connections" i have set up in my network preferences and what shows up under ifconfig... I'm probably just confused because the default wired connection is called auto eth0 and ifconfig only shows eth0. I guess my question is, where are the different configurations I have set up under network connections stored/enabled? So for instance, if I use a static connection I've called "static" under wired network connections with a custom MTU of 1400, and then I check on ifconfig what options I have, it only shows up eth0 with mtu 1492. Does ifconfig only show lower level devices or something similar?

---

### Post by steeldriver on 2013-04-13
Set up where? Are you talking about your /etc/network/interfaces file? If so, 'auto' isn't part of the name, it's an instruction to bring the interface up automatically at boot time

Or are you talking about the GUI nm-applet?

---

### Post by flyingsliverfin on 2013-04-13
Sorry not to include that, the configurations/settings/profiles I've made are under that networking drop down (top right corner) -> edit connections 

yeah, just checked what nm-applet was, that's the one (didn't know it was called that!)

---

### Post by steeldriver on 2013-04-13
Ah OK gotcha, well the nm-applet allows you to define multiple connections for the same interface (eth0, wlan0 etc.), whereas ifconfig will show the values that are currently (or most recently) in use - the various connection defs get stored under /etc/NetworkManager (in 12.04 it's /etc/NetworkManager/system-connections/xxx but the exact directory structure may be different in other versions I think). You will need 'sudo' to view them as they are rw for root only because they may contain wifi credentials and so on.

Other tools you might want to play with are nm-tool and nmcli - they are more tuned to the way network-manager does things than ifconfig

---

