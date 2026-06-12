---
title: "How To Permanently Turn Off WiFi"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by birkopf on 2010-12-16
I would like to turn off permanently wifi on my ubuntu 10.10 64bit. 

- I know of right click on networking icon, but I need to do it every time system starts.
- I also know of "ifconfig wlan0 down" but this again need to be done every time. 

What should I do do turn it off permanently (disable) ???

---

### Post by wojox on 2010-12-16
Deactivate the driver?

---

### Post by birkopf on 2010-12-16
> **wojox said:**
> Deactivate the driver?

I don't want to mess with wifi drivers. Especially on Atheros. 

- Can I simply deactivate (disable)  the module/hardware  ? 
Or maybe there is program which can switch it off ?

---

### Post by Mosabama on 2010-12-16
you can add the wireless module to the blacklisted modules file.

/etc/modeprobe.d/blacklist.conf

---

### Post by grahammechanical on 2010-12-16
Have you tried Edit Connections and delete your wireless connection. Then it most certainly will not connect.

You could also remove network manager from Startup Applications. Then it would not load when you boot. You will also lose wired connections as well. Look under System>Preferences>Startup Applications.

Why not change your User permissions so that you login without permission to access networking, modem or Internet.

regards.

---

### Post by 73ckn797 on 2010-12-16
> **grahammechanical said:**
> Have you tried Edit Connections and delete your wireless connection. Then it most certainly will not connect.

This would work.

---

### Post by birkopf on 2010-12-17
> **73ckn797 said:**
> This would work.

I don't want to get rid of wired connection. I just want to turn off WiFi.

I don't use windows sine 5-6 years, but there, on XP was a Devices manager and I could simply right click on wireless card, choose disable and that was it. 

I want to deactivate Wifi, that could be easily reactivated (later on when required). Wired connection needs to stay.

---

### Post by 73ckn797 on 2010-12-17
> **birkopf said:**
> I don't want to get rid of wired connection. I just want to turn off WiFi.

I don't use windows sine 5-6 years, but there, on XP was a Devices manager and I could simply right click on wireless card, choose disable and that was it. 

I want to deactivate Wifi, that could be easily reactivated (later on when required). Wired connection needs to stay.

That fix will accomplish exactly what you want. You can disable or enable wireless.

---

### Post by birkopf on 2010-12-17
> **73ckn797 said:**
> That fix will accomplish exactly what you want. You can disable or enable wireless.

I want to disable Wireless Card (module) not only disabling connecting to network.

---

### Post by Y_Ernst on 2010-12-17
Perhaps you could add a script disableWIFI.sh to your autostart program. 
Something like: 

#!/usr/bin/bash
ifconfig wlan0 down

Than change the user to root and add the S and x flag. If the S flag does not work move the script into /etc/ini.d
 
update your runlevels:

update-rc.d [YOUR SCRIPTNAME] defaults

---

### Post by Mosabama on 2010-12-17
> **birkopf said:**
> I want to disable Wireless Card (module) not only disabling connecting to network.

Why dont you just add the module name in the blacklist.conf file then ?

---

### Post by 73ckn797 on 2010-12-18
> **birkopf said:**
> I want to disable Wireless Card (module) not only disabling connecting to network.
Have you tried disabling the wireless card in BIOS?  If this is an integrated WiFi card.

---

### Post by kevdog on 2010-12-19
I'm not trying to be a jerk here, but the most easy solution has been mentioned.  Just prevent the kernel module (not driver), from loading during boot.  Depending on what module you are using, you could do this in any number of ways.  If you did nothing to set up your kernel module in the first place, just add the name of the module to the blacklist, and it will not be loaded at boot.  If at any time in the future you want it back, just delete the line in the blacklist file -- and Viola -- you are back in business, or simply load the module with a modprobe statement on the ***mand line.

---

### Post by birkopf on 2011-06-16
From ubuntu 11.04 there isn't a problem. Once you right click on network manager icon and "untick" wireless it doesn't load after restart.

---

