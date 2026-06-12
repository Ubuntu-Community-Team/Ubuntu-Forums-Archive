---
title: "Belkin trouble"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by JohnCurtis on 2009-04-05
Hello :)
This is my first post on UbuntoForums.Org, hopefully I'll become an active community member.

I recently (well, today) installed [ubuntu] onto my computer. After an hour of pressing random buttons; my Belking Wireless G USB adapter lit up! I had internet connection!

The only problem is, I'm connected to my neighbours (they do not have a password for their network). I wanted too know how I could possibly connect to my own router.

Thanks in advance, 
John.

---

### Post by battlebison on 2009-04-05
I'm new to this too, so someone may need to come correct me if I'm wrong, but your router should have it's own ESSID. This is the name of the router as it shows up in a Windows "Connect To" dialogue box.

1. Go to Applications -> Accessories -> Terminal

2. ```
iwconfig
```
This will list your wireless connections. Any wired connections should say "no wireless extensions.", but your USB adapter should be listed with a bunch of stuff next to it. Look for ESSID:"default" or something along those lines to see what your current ESSID is set to. If this isn't the name of your router, then we're on the right track! If not, post back here. Also, make a note of what your USB adapter is called (ath0, wlan0, etc.)

3. ```
sudo iwconfig wlan0 essid "My Network"
```
Where "My Network" is whatever your network is called and "wlan0" is whatever the name of your adapter is.

Hope this works!

---

