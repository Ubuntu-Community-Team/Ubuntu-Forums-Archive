---
title: "Connect to wireless network without taskbar"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Jaded Misanthrope on 2009-06-07
I am currently in the process of changing around how my installation of Ubuntu looks, and if possible I would like to do away with the upper taskbar with, amongst other things, the system tray containing wireless status, date, etc. I can circumvent everything there except the wireless connection -- I am completely dependent on the wireless icon in the taskbar to connect to the Internet.

Is there a way to connect to the Internet wirelessly using either the terminal or a GUI application that doesn't depend on the taskbar?

---

### Post by Crafty Kisses on 2009-06-07
You can scan for wireless networks by running the following in the Terminal:
```
sudo iwlist scan
```
Then from there you can see what networks you can connect to, once you see your network, you can connect by running:
```
iwconfig eth1 essid <your_accesspoint_essid_here>
```
Now if you have an encryption on your router, the command is a bit different, you would run:
```
iwconfig eth1 key <your_key_here>
```
That should get you connected to your network through the Terminal.

---

### Post by Jaded Misanthrope on 2009-06-09
> **Codename said:**
> You can scan for wireless networks by running the following in the Terminal:
```
sudo iwlist scan
```
Then from there you can see what networks you can connect to, once you see your network, you can connect by running:
```
iwconfig eth1 essid <your_accesspoint_essid_here>
```
Now if you have an encryption on your router, the command is a bit different, you would run:
```
iwconfig eth1 key <your_key_here>
```
That should get you connected to your network through the Terminal.

What would I do if I require a password to access my router? I've tried running the first command followed by the second with my password in place of <your_key_here>, but to no avail.

---

### Post by superprash2003 on 2009-06-10
are you talking about the wireless key or the router access password ( the one you use when you try to access your router configuration using a web browser)?

---

### Post by kerry_s on 2009-06-10
once you get your commands down you can script it.

---

### Post by Jaded Misanthrope on 2009-06-10
> **superprash2003 said:**
> are you talking about the wireless key or the router access password ( the one you use when you try to access your router configuration using a web browser)?

Sorry, I meant the wireless key used to actually access the Internet, not the router config.

---

