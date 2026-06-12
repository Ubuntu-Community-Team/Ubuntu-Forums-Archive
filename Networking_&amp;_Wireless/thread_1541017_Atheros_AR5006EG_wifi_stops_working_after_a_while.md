---
title: "Atheros AR5006EG wifi stops working after a while"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by missingno on 2010-07-28
Previously my wifi has worked just fine in 10.04, but as of recently I keep losing my connection after leaving my laptop on for a while (and this happens sooner and sooner each time, used to be daily, now it's every few hours), I can no longer see any networks at all, and I have to reboot to get it working again. I haven't even installed or removed any packages lately, so I'm not such what might've caused this to break all of a sudden.

---

### Post by missingno on 2010-07-28
I tried installing the Windows drivers through ndisgtk, but that only prevented me from getting a connection in the first place. And even after uninstalling it and rebooting, I still can't get any connection anymore. Help!

---

### Post by missingno on 2010-07-28
Correction: turns out I have an AR5001 according to sysinfo. But now that I can't get a connection it's too late to try downloading it's Windows drivers...

Does anyone know how I can fix the config so I can at least get the intermittent connection I had before?

EDIT: Wait, looks like those are the same thing. Still, I need to figure out how to reset the damage I've apparently just done.

---

### Post by missingno on 2010-07-29
A wild BUMP appears! With Zubat-like frequency, too.

After some searching, I found some posts addressing this and managed to get back to where I was, but didn't solve the original problem.

These commands got me back to having a connection upon booting, but it still drops eventually (reentering these doesn't help). Looks like it's missing one of the modules.

```
david@david-laptop:~$ sudo modprobe -rv ath5k[sudo] password for david: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
david@david-laptop:~$ sudo modprobe acer-wmiWARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
david@david-laptop:~$ sudo modprobe -v ath5kWARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.32-21-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
```

[This patched kernel](http://ubuntuforums.org/showpost.php?p=9202462&postcount=3) didn't solve anything, but it did break Compiz. I reinstalled 2.6.34 from the repositories.

Finally I saw that the following packages might help: linux-backports-modules-headers-lucid-generic and linux-backports-modules-wireless-lucid-generic, but they didn't appear to fix anything.

---

### Post by missingno on 2010-07-30
Anyone?

---

### Post by missingno on 2010-07-31
After more searching, I saw two more potential solutions posted that might help. I installed Madwifi which gives me a connection upon booting, but still disconnects later. Then I tried Wicd, didn't help either.

I'm at my wit's end here...

---

### Post by missingno on 2010-08-01
I went and completely reinstalled 10.04.

It still keeps disconnecting.

---

### Post by Dolgoth on 2011-05-06
I am having the exact same problem.

Have exactly the same machine and a complete noob to linux.

like trying to use 11.04 but haveing teething problems with this and a bit with graphics.

---

