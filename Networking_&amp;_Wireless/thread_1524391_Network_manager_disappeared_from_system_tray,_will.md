---
title: "Network manager disappeared from system tray, will not appear if launched manually"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by michaelmestre on 2010-07-05
Dear Ubuntu users,

Following a crash (most probably due to the ATI proprietary driver), the icon for the network manager in Gnome disappeared from the system tray and I cannot connect to the internet anymore.

I tried to launch the manager from a terminal ; the process runs, but no visual indication of this is given.
I tried to remove and re-insert the indicator applet (which shows the battery and sound mixer correctly), but still no network.

The same problem exists in KDE : the network manager says "network not managed" or similar.

I suspect that this problem is linked to DBUS.
ifconfig shows the localhost network, and iwconfig shows an unassociated access point.

I use a recently updated version of Ubuntu 10.04

Thank you very much for your help..

---

### Post by flash63 on 2010-07-05
Hello,
> I tried to remove and re-insert the indicator applet (which shows the battery and sound mixer correctly), but still no network.
add the "notification area".

---

### Post by michaelmestre on 2010-07-05
It works, thanks a lot !!

---

### Post by Iowan on 2010-07-05
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread [SOLVED]. :)

---

