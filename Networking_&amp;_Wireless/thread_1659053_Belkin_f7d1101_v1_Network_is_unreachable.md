---
title: "Belkin f7d1101 v1 Network is unreachable"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by itsmilesdavis on 2011-01-03
Hello, all.

My ubuntu installation was running fine with the Belkin F7D1101 v1 after using this install method:

[http://georgia.ubuntuforums.org/showthread.php?t=1522815](http://georgia.ubuntuforums.org/showthread.php?t=1522815)

But, after allowing ubuntu to autoupdate many programs (don't remember which ones), the device stopped working.

I checked all of the commands in the link above.  They are all still functioning.  dmesg throws no errors, but it terminates with 

<code>ADDRCONF (NETDEV_UP): wlan0: link is not ready</code>

Are there any network files which may have been overridden from autoupdate?

iwconfig wlan0 shows "Access Point: Not-Associated"

Help?  What output can I show you to help me find the problem?

---

### Post by PatchesTheCaveman on 2011-01-03
It sounds like your RF kill switch is enabled.  Download the rfkill package through the Ubuntu Software Center or Synaptic or on the terminal:
```
sudo apt-get install rfkill
```

Then, open a Terminal and run it:
```
sudo rfkill list
```

Does your wireless show up as hard or soft-blocked?

If it's hard-blocked, flip your wireless switch.  This might be a physical switch on your laptop, a discrete button, or an Fn key combination.

If it's soft-blocked, run this command to unblock it:
```
sudo rfkill unblock 0
```

Also note that in order for *iwconfig* to return useful information, you must run it as a superuser:
```
sudo iwconfig
```

---

