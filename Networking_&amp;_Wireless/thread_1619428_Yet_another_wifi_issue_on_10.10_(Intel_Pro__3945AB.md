---
title: "Yet another wifi issue on 10.10 (Intel Pro  3945ABG)"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by ndxtg on 2010-11-11
As title said, wifi randomly drops on Ubuntu 10.10 32bit. I just upgraded from 9.04 to 10.10 (clean install) and face this issue.

There was a fix for Broadcom but not Intel Pro, so I just type some descriptions here in hope that the developers may have some clues on fixing it. 

_ Wifi randomly drops for no reason.
_ The card works fine on WinXp (dual boot) so the device is not faulty. (laptop intel pro card, details is at bottom of this thread)
_ The network was normal, no heavy load (about ~10KB/s) so this eliminates network overloading.
_ Comparing to 9.04, the wifi signal is way weaker.
_ Happens on both WPA and WPA2 network.
_ This message appears in /var/log/messages every time the connection drops
> [12819.337348] cfg80211: Calling CRDA to update world regulatory domain
[12819.344599] cfg80211: World regulatory domain updated:
[12819.344605]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12819.344612]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12819.344619]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12819.344625]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12819.344631]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12819.344637]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


_ Output hardware info
> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:d3:03:2c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.0.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f8900000-f8900fff


---

### Post by jshuford on 2010-11-11
Try: Encore ENUWI-G2... Work's out of the box!

---

### Post by ndxtg on 2010-11-11
> **jshuford said:**
> Try: Encore ENUWI-G2... Work's out of the box!

:confused: usb wireless stick is cool, but it's better if we can use our current wireless card that comes with the laptop :popcorn:

---

### Post by jshuford on 2010-11-11
I agree, but I am done "trying" to get WiFi working in ubuntu!

---

### Post by gsoundsgood on 2010-11-14
same problem here... connection basically works, but it disconnects you for no apparent reason for a few seconds, then it gets back working...

---

### Post by ndxtg on 2010-11-26
Now I can confirm that this is not a card nor network problem, it's Ubuntu's problem.

I have swapped it with a Atheros AR5001 card using 2 different drivers:

ath5k: still randomly disconnects and cannot re-connect unless reboot
ndiswrapper: using Windows driver - same symptom

so it's seem to be appeared on both Intel & Atheros cards (no matter which driver is used)


dmesg or /var/log/messages shows in loop: wlan1 is being reset

---

### Post by Yeeha on 2010-11-28
I have Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02), i was unable to connect or stay connected before too. What worked for me was: sudo rfkill block bluetooth. But that has to be done at every boot, i dont know how to make it permanent.

---

### Post by bkratz on 2010-11-28
Directions that will probably help you are in the response to this thread

[http://ubuntuforums.org/showthread.php?p=10097837#post10097837](http://ubuntuforums.org/showthread.php?p=10097837#post10097837)

---

### Post by Yeeha on 2010-11-28
Atlast, thx!

---

### Post by cruach on 2010-12-23
Hi!

I have a similar problem - 10.10. Intel 3945ABG - with intermittent wireless. Boot under XP, no wireless problems.

But this only happens with one router. At home I use my landlord's wireless router - no problems under Ubuntu. Right now I'm visiting my parents, and I have the intermittent wireless problems with Ubuntu. 

Any suggestions?
Thanks :)

---

