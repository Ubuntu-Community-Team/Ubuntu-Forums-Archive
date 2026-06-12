---
title: "where'd my network manager go?"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by Cam42 on 2009-10-09
I'm trying to connect my sisters' (ed)ubuntu desktop to our WiFi, but on her account, the network manager is not in the systray. I've configured our network in the network connections window, got our WPA password in, but I can't connect. I can connect just fine on my admin account. I'm gonna check now and make sure that I've enabled them to connect to the internet.

---

### Post by Cam42 on 2009-10-09
Attached is the error I get when logging on.

---

### Post by t0mppa on 2009-10-09
From the screen shot it looks like you've disabled the top panel and haven't added the Notification Area to the bottom panel, where Network Manager resides.

---

### Post by Cam42 on 2009-10-09
Whoops, forgot to say that the Top panel is on autohide, and there is the Notification Area up there.

---

### Post by t0mppa on 2009-10-09
Ok, then open up a terminal and run **ps ax | grep nm-applet** to see, if the Network Manager itself is running. It should display something along the lines of: ```
$ ps ax | grep nm-applet
 3930 ?        S      0:09 nm-applet --sm-disable
22181 pts/0    S+     0:00 grep nm-applet
``` if it's found. If it only shows the grep, then it's not running and you can start it by pressing Alt + F2 and typing in *nm-applet* and clicking *Run*.

Also, to find out what service is hoarding port 5800, run **sudo netstat -anp | grep 5800**.

---

### Post by Cam42 on 2009-10-09
It would seem that the problem was fixed after I logged out instead of fast user switching.

---

