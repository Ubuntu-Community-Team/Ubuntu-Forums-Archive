---
title: "No internet on 9.04 - but works on 8.04, 8.10; or XP"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Idir on 2009-05-24
Hi!
I just upgraded from Hardy Heron to Intrepid Ibex using the alternative CD install with the CD being virtually mounted, and then again I re-upgraded to 9.04, but then my internet connection stopped working.
It works just fine with Windows XP, which I'm using right now, though, and it worked using 8.04 or 8.10.
I tried to configure it using "pppoeconf" on the Terminal, which is how the settings were before the upgrade, and I tried it again on 9.04 and it seemed to work, but it doesn't - I tried "pon" to activate the connection on the Terminal, but it said that the "device is not recognized", which is what previous versions used to display when there was a connection problem from the ISP's side.

Then, I contacted my ISP and they said that they only fix Windows problems, and my connection on Windows is normal.

Any help would be appreciated, thanks!

---

### Post by The Toxic Mite on 2009-05-24
Are you using a wired or wireless connection?

If you are using wireless, can you post the results of the following Terminal code:

```
lshw -c network
```

(To get to the Terminal in GNOME, go to Applications > Accessories > Terminal)

Thanks

---

### Post by Idir on 2009-05-24
No, it's a wired connection, I think Ethernet. My modem is a ZTE ZXDSL 831.

---

### Post by Iowan on 2009-05-24
> **Idir said:**
> I tried to configure it using "pppoeconf" on the Terminal, which is how the settings were before the upgrade, and I tried it again on 9.04 and it seemed to work, but it doesn't  Try commenting out (or removing) the changes via terminal (in */etc/network/interfaces*?) and adding the connection via NM applet.  The new NM version *seems* to work better.

---

### Post by Idir on 2009-05-25
Hi!
But I did remove it and tried using the NM, but whenever I click "Apply" after choosing the connection settings, the connection gets deleted from the list.
Sometimes it doesn't, but the connection doesn't work anyway...

---

