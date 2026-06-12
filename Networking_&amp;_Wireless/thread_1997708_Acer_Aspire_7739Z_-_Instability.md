---
title: "Acer Aspire 7739Z - Instability"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2012-06-05
All,

We, converted my new laptop to Ubuntu.  Originally tried 10.04 but no driver support, so started upgrading versions.  Finally we are at 12.04 and everything but the WiFi, which I need 100% of the time have been stable, but the WiFi, is not.  They best we have gotten is 10 days without it dying, and right now all the patches have it totally screwed and we can not get it to come up and stay up.

We are having to use the wired connection to work on it.  We added TeamViewer as RDT as it is only RDT we know that works on both Windows and Linux and need it to work with XP in VirtualBox.

The Network Manager was so unstable that we installed Wicd to get WiFi networking to work and this was when we finally got the 10 days.

Now what happens is the WiFi comes up and first page is accessed on FireFox and quikly, then either the system acts like DNS is lost or PROXY is installed (with TeamViewer and other TCP/UDP functions working) or it totally kills the connection.

We can plug in the wired connection to try to keep working on this but even that gets tossed after 15-20 minutes and we have to reboot.

This Aspire says it using it's own proprietary Nplify 802.11 b/g/n WiFi chip, but running lshw shows it as "Centrino Wireless-N 100" Intel, so guessing the "Nplify 802.11 b/g/n" designator is Acer's mod to BIOS for this chip set.  Anyway this is sooo unstable that I'm hoping some of you have some insight as the 2 of us have almost considering going back to WinDUHS for this.

The one thing we see that might get us free, is both show on IRQ 11 and if we were able to change IRQ for one, the issues might go away.

Anyway please let us know if you have insight on this issue.  We have been fighting this since February.

Thanks!

OMR

---

### Post by praseodym on 2012-06-05
The driver **iwlwifi** is buggy. Deactivate the N-Mode via

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by OldManRiver on 2012-06-07
> **praseodym said:**
> The driver **iwlwifi** is buggy. Deactivate the N-Mode via

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

praseodym,

Kudos bro, did this and been working all morning for last 4 hours steady as a rock.  We did not think about disabling "N"!

Thanks much!

OMR

---

