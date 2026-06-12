---
title: "no network after indicator install"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by voyy on 2012-09-11
Hi, I wanted to have nifty network indicator so I know how much upload/download goes through air all the time, fast google and I see "indicator-network" does basically what I wanted. 

> sudo apt-get install indicator-network

Requested restart so I did and after that there is not only no network connection but also nothing that would suggest I ever had it. No network tools, no "Network" in settings, system doesn't see my wifi card anymore, nothing. I proceed to fix my mistake by

> sudo apt-get remove --purge indicator-network

Restart, nothing has changed, no connection, no tools, no "network" in system settings, doesn't see my wifi card.

What do I do now, mind that, obviously, I have no internet.

---

### Post by dozdozez on 2012-09-11
try with wicd.

(in a terminal type wicd)

If you haven't it installed, install it.

if you like it, then you can configure xfce to start it at startup:

menu --> settings --> seettings manager --> application autostart 

 and there the tick of wicd network manager.

---

### Post by Epodx64 on 2012-09-11
do you get anything from ifconfig -a?

try running sudo /lib/recovery-mode/options/network

---

### Post by Epodx64 on 2012-09-11
wait you obviously have some kind of internet connection anyway you could just download the wicd .deb package and install it on your system with a usb drive or something?

---

### Post by voyy on 2012-09-11
> **dozdozez said:**
> try with wicd.

(in a terminal type wicd)

If you haven't it installed, install it.

if you like it, then you can configure xfce to start it at startup:

menu --> settings --> seettings manager --> application autostart 

 and there the tick of wicd network manager.

yeah, trying to instal it but instalation failed, looking now for new package

---

### Post by voyy on 2012-09-11
> **Epodx64 said:**
> 
try running sudo /lib/recovery-mode/options/network

> 
#sudo /lib/recovery-mode/options/network 
[sudo] password for v: 
start: Job is already running: dbus
start: Job is already running: network-manager


and that's it, just hang without end, I tried to start networking services manually but they didn't

ifconfig sees my cards so I'll just try to install wicd somehow. Had no idea that ******* package will replace all my network software...

and sorry for slow answers, hard to get some internet currently.

---

### Post by voyy on 2012-09-11
> **Epodx64 said:**
> wait you obviously have some kind of internet connection anyway you could just download the wicd .deb package and install it on your system with a usb drive or something?

yeah, doing it now

---

### Post by dozdozez on 2012-09-11
you can try nm-applet, maybe you have it already installed.

---

