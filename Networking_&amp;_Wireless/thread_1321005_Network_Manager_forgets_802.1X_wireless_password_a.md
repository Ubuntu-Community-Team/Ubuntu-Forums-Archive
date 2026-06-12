---
title: "Network Manager forgets 802.1X wireless password after"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Potters Son on 2009-11-09
Hi. The 802.1x wireless at my university is patchy -- I frequently lose it and get it back -- but that isn't the problem I'm reporting right now.

Sometimes, when my computer drops the wireless network, it isn't able to reconnect. In past versions of Ubuntu, all I had to do was disable and re-enable wireless. If I let it search for the wireless network too long, it would give up trying to connect. But now (9.10 Karmic Koala), I observe that when Network Manager gives up, it erases my 802.1x password for that network. Any ideas?

P.s. I looked up the log for Network Manager, and it looks like wpa_supplicant is deleting my password randomly. I don't know why, though. I've attached a portion of my daemon.log, starting at a point when I know the password was there. (I stripped out my hostname and username, of course.)

---

### Post by rainbowFish on 2009-11-10
Same problem here.

---

### Post by Potters Son on 2009-11-19
Bump.

I was kinda hoping someone would post an explanation for this phenomenon, whether it was some new "feature" (like qemu upstream dumping support for kqemu, which I rely on, but that's beside the point) or a bug recently created trying to fix something else. Maybe it's something just wrong with my system, in which case I'd just do a reinstall.

I'm getting pretty sick of having to dis/reconnect my networking, re-entering my passwords and certificate information, and restarting the Network Manager applet after it crashes. That's right -- it simply disappears from the system tray after it "forgets" my network password and tries to reconnect. (By the way, the command to restart it is:
```
/usr/bin/nm-applet
```

Should I file this as a bug? If so, where?

---

### Post by namluc on 2009-11-19
I've been having the same problems, read this thread it may help

[http://ubuntuforums.org/showthread.php?p=8348265#post8348265](http://ubuntuforums.org/showthread.php?p=8348265#post8348265)

---

### Post by Potters Son on 2009-11-22
Wicd doesn't do 802.1X (at least, for wired networks), which I need for school.

---

### Post by joee92 on 2010-01-02
I too am experiencing this problem.  The details for me are:

Whenever NetworkManager can't connect (due to distance from my AP, cosmic rays, or who knows what) after a few tries, it gives up and says "unable to connect to network <SSID>".  Fine.

But NetworkManager has also cleared the password.  Pull down its menu to select my SSID manually, and it (too) quickly repeats the OSD message about being unable to connect to the network.

To fix, I have to go into  Edit Connections, scroll down to my SSID, Edit, enter keyring password, wait for Wireless Security tab to appear, and replace the password that NetworkManager seems to have erased.

---

### Post by joee92 on 2010-01-04
I have found a much less painful workaround for the problem I was experiencing:

```
sudo service network-manager restart
```

---

### Post by Potters Son on 2010-02-06
Still deletes the entries for me.

I was having it work wonderfully for me the past month -- I set the encryption method from PEAP to TTLS, so the connection was never timing out and the password never got wiped ONCE. And then, I had to do a clean reinstall, and then the problems started up again. What the heck?

---

### Post by LanoxxthShaddow on 2010-03-05
I am experiencing the exact same error, both with my university 802.11X WPA2-Enterprise login and with a local WPA2 Access point. In both cases it seems that network manager forgets/clears the password and I have to reenter it manually. Additionally it show the respective wirless name with status "last used: never" in the edit connections dialoge.  This is very annoying. I just commented on bug #318286, but im not sure if its related. Has anyone else reported a bug so far?

---

### Post by Rick Deckard on 2010-03-13
I recently upgraded to karmic and immediately started to get random disconnections with my USB wi-fi card (D-Link DWL-G122), network manager kept 'forgetting' the password etc...

...so, I replaced network-manager with 'wicd - wired and wireless network manager' (package = wicd) and voilà, the connection is now stable. :D

As a bonus, the interface is nicer than network-manager too (IMO).

---

