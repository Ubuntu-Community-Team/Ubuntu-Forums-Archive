---
title: "Foxytunes no longer working with Amarok?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by DeaconBlues on 2008-04-06
Hi,

I've been using Ubuntu Gutsy Gibbon for 3 months now and love it. After my first install I also downloaded and installed KDE to give it a try. I found out that I preferred Gnome so I reverted back to that, but still had components of KDE installed.

Anyway, I was using Amarok, controlled by Foxytunes in Firefox no problems with my old installation.

A coupla weeks ago I did a total Gutsy re-install in order to partition my drives better, now that I'm more used to the Linux file system.

I only have Gnome installed this time: no KDE, apart from Amarok and KTorrent. Now when I go to install Foxytunes and select my music player Amarok is missing from the list of supported players :( :confused:

Is this because I need to install KDE again, or is there a problem with the latest versions of Firefox/Foxytunes?

I'm using Firefox v 2.0.0.13 and Amarok v 1.4.7 is this helps.

Thanks.

---

### Post by raph0001 on 2008-04-25
It seems that Foxytunes depends on libstdc++5. Try to install libstdc++5, then uninstall Foxytunes and reinstall it.
```
sudo aptitude install libstdc++5
```

---

### Post by wiigee on 2008-05-08
thanks a bunch, works great now! =)

---

### Post by maphilli14 on 2008-05-20
Yes, most excellent!!!

---

