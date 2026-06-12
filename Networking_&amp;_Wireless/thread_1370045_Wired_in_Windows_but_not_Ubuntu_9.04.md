---
title: "Wired in Windows but not Ubuntu 9.04"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Rayve on 2010-01-01
I posted several hours ago with a slightly different problem ([http://ubuntuforums.org/showthread.php?t=1369752](http://ubuntuforums.org/showthread.php?t=1369752)).  After 5+ hours with Linksys (router) tech support, I had no router and no modem functionality at all, so I had no internet.  After talking with my ISP tech support, I can at least connect via my DSL modem if it is plugged directly into my desktop and I have Windows booted up... for some reason, Ubuntu is not recognizing it when I reboot into Ubuntu 9.04.
 
I read the community documentation about ADSL connection and will try that next, but was wondering if anyone had any pointers about what might cause this.  A few months ago when I made the switch from Windows to Ubuntu, I simply loaded up Ubuntu (the wireless router was working, but it said I had "Wired eth1" connection from my desktop) and it detected the connection without an issue.  Now, router out of the picture and modem directly into my computer, it isn't finding anything.

---

### Post by sgosnell on 2010-01-01
You might try opening System/Preferences/Network Connections, the Wired tab, and make sure everything is set correctly.  You can break ethernet by changing things there.

---

### Post by Rayve on 2010-01-01
sgosnell,

I actually just tried that before checking back here, and it worked!  I must have deleted the Wired automatic connection it made, so I just created a new one and had it "connect automatically" and "apply to all users".  I at least have internet again through Linux... I guess it's on to the wireless router now.  :)  Thanks!

As an aside: sudo pppoeconf recognized my ethernets but didn't have any luck setting up a pppoe even though that's what I use... will that be an issue in the future? (I never used pppoeconf before, but....)

---

### Post by sgosnell on 2010-01-01
I can't say, I've never actually used PPPOE.

---

### Post by peepingtom on 2010-01-02
Don't use pppoeconf if you want to continue using NetworkManager (networking icon in Notification Area aka "system tray"). If you must use PPPOE, configure it using the DSL or Dialup tab in the way you added the "auto" wired connection.

---

