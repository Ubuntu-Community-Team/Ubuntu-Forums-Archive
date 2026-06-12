---
title: "VNC issue after Jaunty upgrade."
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by ausher on 2009-04-26
I can connect to my server over the internet with no issue. Once connected everything looks normal but it doesn't appear that anything is registering, mouse or keyboard. However, if I disconnect my VNC session and reconnect, those keyboard strokes now appear. So in order to navigate my home server I have to constantly be disconnecting and reconnecting. 

Any ideas? It only seemed to start happening after I did the upgrade to 9.04 the other night.

p.s. I have tried using multiple VNC viewers with the same result.

---

### Post by guaguo on 2009-04-26
Fresh Jaunty install.

Same happens to me.

Really movements works on host, but doesn't appear on client window.


I've tested with 2 near PC's, so I can see movement on host.

Tested with Ubuntu and Windows clients, same happens

---

### Post by thesnizz on 2009-04-26
Yeah, it has to do with compiz.  If you disable the advanced visual effects (in the System -> Preferences -> Appearance) VNC will work again.  It's a bit frustrating since compiz could be enabled and still have VNC work in previous releases though.

Hoping whatever the issue is gets sorted out.

---

### Post by ausher on 2009-04-26
> **thesnizz said:**
> Yeah, it has to do with compiz.  If you disable the advanced visual effects (in the System -> Preferences -> Appearance) VNC will work again.  It's a bit frustrating since compiz could be enabled and still have VNC work in previous releases though.

Hoping whatever the issue is gets sorted out.

Thanks, that solved it :)

---

### Post by fastpakr on 2009-05-05
Has anybody run into a resolution for this?  I'm surprised that this regressed from Intrepid to Jaunty.

---

### Post by edam on 2009-05-08
Here is the [bug report on launchpad]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126") for this issue.

---

### Post by mattgyver83 on 2009-05-08
Installing the x11vnc package should help you make a connection and use beryl if you really want but you might need to use a different service, like tightvncserver and start both per your sessions.

Hope that works for you.

---

### Post by krunge on 2009-05-08
BTW, if you use x11vnc as a workaround, **be sure** to supply "-noxdamage" to its command line.

This makes sure it avoids the problem of no or slow screen updates due to the Xorg and/or compiz bug that is causing all of this.

---

### Post by SoftwareExplorer on 2009-05-20
If you need to get in remotely and have a command line, this work around was listed on the bug report:
on the terminal of the remote machine 
```

gconftool -s -t string /desktop/gnome/applications/window_manager/current /usr/bin/metacity
gconftool -s -t string /desktop/gnome/applications/window_manager/default /usr/bin/metacity
```

Then restart ```
sudo init 6
```

This will turn off compiz and restart the machine. Of course vnc won't work after a restart until you login, unless ubuntu logs in automatically...

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by guaguo on 2009-06-09
jmap82:

The script always turns off compiz for me, even if vnc is not running.

Thanks in advance, good work.

---

