---
title: "won't  stop creating ad-hoc network"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by wikityler on 2010-08-26
I'm running Lucid on my Gateway NV54 laptop with an Atheros AR928X wnic. Ever since I created an ad-hoc network a week ago, the network manager defaults to recreating this network rather than connecting to the wired or wireless connections it is set to automatically connect to. If I've manually chosen to connect to a specific network, after resuming from suspend or hibernation it will instead recreate the ad-hoc network. Despite being deleted from the wireless connections list, the ad-hoc network is still listed in the drop down box of available wireless networks.

How do I prevent network manager from creating this ad-hoc network?

---

### Post by quixote on 2010-08-28
This extremely basic function is for some reason idiotically complicated in ubuntu.  I ran into this a couple of years ago, hopefully the fix I found will still work.  (The problem arises because gnome has the braindead default of assuming the *last* connection you defined is the one you want all the time.)

Open a terminal (Applications > Accessories > Terminal) and type```
gconf-editor
```In the window that opens, look in the left pane and navigate down to: / > system > networking > wireless > networks.  That should list all the networks to which you have established connections.  Select the adhoc connection you don't want, select each of the various items like bssids, essid, etc., right-click, and choose unset.  That stops nm-applet from thinking the connection exists.  There may be simpler ways these days, but that was the only thing I ever found.  Maybe you could alter "timestamp" to be earlier than a connection you actually want.  I've never tried that.

---

### Post by wikityler on 2010-08-29
Thank you so much! The procedure was a bit different for me, but it appears to have worked.

[IMG]http://imgur.com/oqt1I.png[/IMG]

---

### Post by quixote on 2010-08-29
Glad it worked.  That's a very annoying issue, and I'm kind of surprised to hear it's still around, lo, these many moons later!  You'd think this would be a priority for the devs, especially since there can be legal issues with hopping onto, say, your neighbor's wireless.  In my case, I'd be using his (unsecured!) wireless and not even notice sometimes for hours, since the whole process was so seamless.

---

