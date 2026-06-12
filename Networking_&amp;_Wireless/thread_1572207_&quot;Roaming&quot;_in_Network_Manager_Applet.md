---
title: "&quot;Roaming&quot; in Network Manager Applet"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by funfrank on 2010-09-10
I have a weak wireless signal from my neighbor's router that we share.  Ubuntu's default driver for my wireless card would connect to the router, but traffic through a web browser was slow.  I installed the windows driver with NDIS and it solved the problem.  However, sometimes NDIS has trouble connecting to the router.  Worse, if the network does not show up when I start the computer, the network will not appear until I restart the computer from the other room where the signal is stronger.  Typically, I turn on the computer in the other room and connect (with three bars) and then drag my computer to the other room where my desk is (with one bar).  Everything is fine then.  But I'd prefer to be able to refresh my available network list if I don't connect at start-up.  The ubuntu driver refreshed automatically.  I'd like the same thing to happen with my (almost) fully-functioning NDIS driver as well.  I'm not sure what this refresh is called.  I tried searching the forums under "roaming" or "refresh" but I came up empty.  Can anybody either give me a suggestion on how to solve the problem, or point me in the direction of a relevant search?

Karmic Koala, NDIS atheros

---

### Post by MaindotC on 2010-09-10
Ask your neighbor to kick up the transmission power.  It should be easily configurable in the access point's (what you call a router) settings.  Any chance you could run a cable to it - like do you live on top of your neighbor or is this like across the street?

---

### Post by funfrank on 2010-09-11
No chance with the wire.  He has his son do technical things like kick up the power of the access point, and his son is presently away at school.  

What is strange is that I cannot refresh a list of available access points in gnome network manager applet with my ndis driver.  If network manager does not see the ssid at start-up, I need to restart my cpu.  Anyway to set network manager to "roaming" or auto-refresh, or something similar?

---

### Post by MaindotC on 2010-09-11
It's difficult to say if this is a bug in ndiswrapper or NetworkManager or both.  It's not that you need to restart your computer, but restarting ALSO restarts something else which happens to interact with the network settings.  You can try restarting NetworkManager.  I have found a way to do that but I know it's not THE correct way, just A way to do it so either google "restart network manager" or proceed at your own risk.

Restart NetworkManager using the following command in a shell:```
sudo service network-manager stop
sudo service network-manager start
```Now when I did this, I got the wireless-looking icon with a red exclamation point and when you left-click on the icon it shows the wired and wireless interface as "Device not managed."  To fix this, edit the /etc/NetworkManager/nm-system-settings.conf and find the line that says: "managed=false" and change it to true, then restart networking:```
sudo nano /etc/NetworkManager/nm-system-settings.conf
sudo service networking restart
```

You should be able to simply restart network-manager without editing this file but I'm not sure how to get it to save that setting each time.  Until you get a more definite answer this should refresh that network listing for you.  You can also get a wifi-extender to repeat the wireless signal throughout your place.

---

