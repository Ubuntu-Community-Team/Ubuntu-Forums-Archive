---
title: "rt2500pci fails to connect until reloaded"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by ShaheedHaque on 2009-12-26
I have a headless server running Kubuntu karmic on 2.6.31-16-generic. It has a rt2500pci wireless card which I want to have come up on boot.

That does not work by default because after boot, an "iwlist scan" of wlan0 nearly always produces "No scan results". Sometimes, if I wait long enough, some results are returned. However, after reviewing [*this Slackware thread*]("http://www.linuxquestions.org/questions/slackware-14/latest-kernel-from-current-no-wireless-even-though-modules-loaded-724867/"), I tried the rmmod/modprobe sequence, and can confirm the card starts returning scan results promptly.

So, I configured /etc/wicd/wireless-settings.conf to have a prestart script like this:

```

beforescript = /etc/wicd/scripts/preconnect/reload_rt2500pci.sh

```

and that script looks like this:

```

#!/bin/bash
# Shell wrapper that restarts rt2500pci
/sbin/rmmod rt2500pci
/sbin/modprobe rt2500pci
/sbin/iwconfig wlan0 rate 54M
/sbin/ifconfig wlan0 up

```

(I probably don't strictly need the rate setting line, but given all the other threads on *that* topic, it is in there anyway).
This still does not fully solve the come-up-on-boot, but does ensure that wicd brings up the interface each time after-the-fact.

I'll probably look into some delay later, but this was enough of a step forward for me that I thought it worth posting.

---

