---
title: "wpc54gs not working after updates"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by unknownerror on 2006-06-16
I had my linksys wpc54gs w/ speedboost working for a little while. It worked last night but not this morning. Last night downloaded all the updates that there were to download and something must have messed up my wireless card settings. I don't know what to do now ... do I need to reinstall or is there something easier for me to do?

---

### Post by DarthMandeep on 2006-06-16
Were you using ndiswrapper to get it working? If so, make sure you blacklist the bcm43xx driver since the two conflict. Just run "sudo rmmod bcm43xx" to unload the driver and add "blacklist bcm43xx" to your /etc/modprobe.d/blacklist file to prevent it from loading on startup.

---

### Post by unknownerror on 2006-06-16
I didn't use ndiswrapper I actually used bcm43xx

---

### Post by unknownerror on 2006-06-16
I figured it out if anyone else is having the same problem make sure you have the windows driver and use the same comands you used with bcm43xx put place it in 2.6.15-25-386 NOT 2.6.15-23-386

---

