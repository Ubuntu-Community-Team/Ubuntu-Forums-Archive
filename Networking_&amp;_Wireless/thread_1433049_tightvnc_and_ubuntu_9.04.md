---
title: "tightvnc and ubuntu 9.04"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by L1nuxNewb1e on 2010-03-18
I recently bought a new dell that came with windows 7. I downloaded and installed Tightvnc to connect to my Ubuntu 9.04 machine. I can connect ok, but when I click on any icons to open a folder or mouse over an icon there is no response. If I want to see whats inside a folder I have to close the connection and log back in to see the updated screen. I've tried sending update request, but nothing happens.

---

### Post by jrssystemsnet on 2010-03-18
First question: are you on the same network with both machines, or are you connecting across the internet?  (If you're connecting across the internet, first try across a LAN to make sure it's not an internet problem.)

Second question: have you tried a different VNC client?  I've had a lot of issues with tightvnc in the past; I recommend RealVNC (the free version) from [http://www.realvnc.com](http://www.realvnc.com) for use on Windows machines.

---

### Post by L1nuxNewb1e on 2010-03-18
I am on the same LAN. I've tried tightvnc and ultravnc. I had the same problem with both. I checked my Ubuntu box thinking I didn't set something, but everything seemed ok. I'll try realvnc. I hope it works. Thanks!

---

### Post by sparky-steve on 2010-03-18
> **L1nuxNewb1e said:**
> I recently bought a new dell that came with windows 7. I downloaded and installed Tightvnc to connect to my Ubuntu 9.04 machine. I can connect ok, but when I click on any icons to open a folder or mouse over an icon there is no response. If I want to see whats inside a folder I have to close the connection and log back in to see the updated screen. I've tried sending update request, but nothing happens.

This is likely to do with effects.

Go to System, Preferences, Appearances, on the Visual Effects tab, select NONE, and try again.

This is a known bug, and I've seen a few clever workarounds on this forum.

---

### Post by jrssystemsnet on 2010-03-18
> **sparky-steve said:**
> This is likely to do with effects.

Go to System, Preferences, Appearances, on the Visual Effects tab, select NONE, and try again.

This is a known bug, and I've seen a few clever workarounds on this forum.Huh... interesting.

FWIW, I connect to my Ubuntu 9.10 amd64 workstation with effects enabled from a Windows XP client using RealVNC without issue.

I also use [Xrdp](http://ubuntuwiki.net/index.php/Xrdp,_installing) on the Ubuntu station so that I can connect with Remote Desktop, which is significantly snappier over the internet (and which allows me the choice of controlling the active local session or a "clean" session on the Ubuntu box, with no effects and a lower screen resolution, at time of connection).

---

