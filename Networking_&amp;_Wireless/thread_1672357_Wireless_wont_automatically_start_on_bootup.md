---
title: "Wireless wont automatically start on bootup"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by dmitton on 2011-01-20
I have a new HP G62-352CA with the Realtek 8191SE wireless.  I am  running Ubuntu 10.10 everything works fine except every time I restart  the computer I have to press fn f12 to restart the wireless.  Is there a  way to have it default on at startup?  I am kind of new so please dumb  it down for me.   Thanks for any help you can provide..

---

### Post by rage_311 on 2011-01-20
Ubuntu uses a network interfaces config file to store the configuration for all of your network interfaces.  It's likely that your wlan interface is not setup to automatically start in that file.

This file's location: /etc/network/interfaces

You'll want to get into your terminal and type: ```
sudo nano /etc/network/interfaces
```
Look for an entry in that file for a wlan interface (probably wlan0).  You should see an entry dedicated to the configuration of that interface, similar to: ```
iface wlan0 inet dhcp
```

My guess is that there isn't a line that says ```
auto wlan0
``` above that.  If it's not there, add it.  Then Ctrl+O to write out, press Enter to save to the same file, then Ctrl+X to exit the editor.  Give that a whirl.  If this isn't your problem, you may have to wait for someone more knowledgeable to reply!  Good luck.

---

### Post by grahammechanical on 2011-01-21
The keyboard fn f12 key combination is there to save battery power on a laptop by not having the wireless adapter using power when it is not needed. It gives you a little control over the power usage of the machine. I do not think that an operating system can override that key combination.

Many have had issues with wireless not re-starting after hibernation or when the battery has completely drained down. Often, the solution is a failure to remember to activate the wireless adapter by using the fn f12 key combination or any other method used by the particular laptop.

It seems that when power becomes very low the machine will start to close down certain parts of the hardware. These do not always automatically re-activate once the battery is re-charged or the mains supply plugged in. Manual activation is needed.

Regards.

---

### Post by dmitton on 2011-01-21
None of the wireless info is in this file.  Could it be stored in a different location?
When I run the commands you told me all I see is;

auto lo
iface lo inet loopback


Where would I find all the startup info like turn on number lock and such?

Thanks again for your help

---

