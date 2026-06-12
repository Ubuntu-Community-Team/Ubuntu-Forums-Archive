---
title: "Network Manager? Where's that at?"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Jonatty on 2010-11-09
I never wanted to do this because I much prefer solving problems on my own, but I'd be lying if I said I wasn't a noob to Linux.  My bro-in-law got me a Dell laptop with Ubuntu 6.06 as a X-mas gift two years ago, and I've been coasting just fine using my D-Link wireless card, UNTIL...
I upgraded to 10.04 this past weekend, and I can't for the life of me, figure out this new "Network Manager" setup.  It makes it sound so easy in the Help screen, simply pull up Network Manager from the icon to select your wireless connection SSID and enter the password (just like I did in 6.06), but the problem is that THERE IS NO Network Manager icon.  Just the Network Connection icon where you can switch between eth0 and wlan0 (used to be ath0).  I can connect through wired connection directly into my router by selecting eth0, but when I choose wlan0: no good.  I know that all I really need to do is somehow open this elusive "Network Manager" screen so I can choose my wireless network and password, but at every turn I'm met with obstacles.  I've observed help threads that require keying in codes into the terminal: "nm-applet" or "/etc/network/interfaces" and the like, but nothing has solved the problem.  Please help, I just want to use my laptop again... wireless.
JK

---

### Post by zealibib slaughter on 2010-11-09
The network manager icon should be in the top taskbar next to the volume control applet in the notification applet.  If it isn't then open a terminal and type sudo NetworkManager and watch for any errors.  If none is given then it should appear.  If it says network manager is running then kill it via top and try to launch network manager again.

---

### Post by Jonatty on 2010-11-09
Zealibib,
Thank you for your reply.  I have, however, observed where the "Notification Area" is on my taskbar, and - get this - there's nothing there.  Not even a volume control.  Now, how do you "kill it via top" again?  You'll have to talk to me like a real noob.  Either way, I don't see why there isn't a Network Manager selection under System>Preferences or Administration or something... but there isn't?  Just an icon?  I know that in Ubuntu 6.06, all I have to do was click the icon that said "Manual Configuration", key in my password and I'd be good to go.  Is that the same as "Network Manager" in 10.04?  So far, I've found "Network Tools", "Network Connections", and "Connection Properties" which is the icon that DOES appear on my taskbar.  Still haven't found any Network Manager.  Apparently, this is a common problem in 10.04, and I wonder if I should just revert to 6.06...
Dismayed, JK

---

### Post by Jonatty on 2010-11-09
Nevermind!  I finally managed to open Network Manager and subsequently got my wireless working at last.  The nm-applet is still missing, but here's what I did.  I found another thread in which another user had upgraded and was having the same problem with the elusive Network Manager.  Finally, a suggestion came in to install "Wicd Network Manager" Application.  That saved me a lot of hassle, because I don't really need the icon applet, I just wanted to get my wireless working.  Yippee!
JK

---

