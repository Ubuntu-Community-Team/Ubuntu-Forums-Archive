---
title: "No Networking Devices Found"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by CrimsonSkyZS on 2006-06-25
Hi, I just installed Dapper Drake 6.06 LTS on my new laptop with IPW3945 and a realtek 8111 networking devices.  During installation it informed me that there was no netowrking devices found.  When it started up i found that my wired is working fine.  I then proceeded to compile and install the ipw3945 drivers but then i read that they are supported under 6.06 lts, and fond that the ipw3945 process is running on my system, but lo-and-behold no wireless card appears anywhere.  Gnome network manager also does not find any kind of networking device.

---

### Post by Apple 101 on 2006-06-25
I just used this method for connecting to my wireless lan and got it running in about 2 minutes (after the downloading of the packages had finished).

1. Find the Windows .inf and .sys files for your wireless card.  Put them together in your home folder.
2. Install the *ndisgtk* package and open it from the System --> Administration --> Windows Wireless Drivers.
3. You'll need to locate the .inf file for the programme.  It will install and recognise your wireless card.
4. Install the *wlassistant* package.
5. Open it from Applications -->Internet --> Wireless Assistant
6. Go through the options - graphically. 

The assistant detects your network, strength, whether it has encryption, and lets you get connected even with password keys.

---

