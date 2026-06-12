---
title: "Wifi on despite physical switch turned off"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by danduq on 2009-09-07
My Dell Latitude D620 laptop recently (past couple of weeks) started trying to connect to our Office WiFi - Even though the physical switch to control the WLAN card on the side of the laptop is off!

Through out the day I see the WiFi and Bluetooth lights on the laptop flickering away, and occasionally get Ubuntu notification messages saying that the WiFi network disconnected. I have to right-click my NM tray icon and deselect "Enable Wireless" every morning to stop it. 

Anyone know how I can put the physical switch on the laptop back in charge or enabling/disabling my WiFi?

Cheers!
--- 

lspci -v
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        Memory at ecfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945

NetworkManager Applet 0.7.0.100

Ubuntu Jaunty

---

### Post by danduq on 2009-09-08
Happened again this morning. I realised that I do not have any devices configured in my interfaces file, so I guess NM is doing all the work?
```
auto lo
iface lo inet loopback
```

I suppose I could add;
```
auto wlan
iface wlan0 inet dhcp

```

I will give it a try. When I'm in the office (most of the time) I don't use the WiFi, so don't really want it coming on.

Any other ideas greatly appreciated!

---

### Post by danduq on 2009-11-09
Sorry for anyone else having this problem and thinking "Resolved! Brilliant!" but I have upgraded to Karmic and no longer have the problem.

---

