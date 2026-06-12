---
title: "IPW3945 - blinking diode in Maverick 10.10"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by LastHunter on 2010-10-12
Hi,
I had a problem with still blinking wifi diode indicating my network adapter generates some traffic. I fixed it in previous Ubuntu versions (10.04, 9.10) with this file (/etc/network/if-up.d/iwl-no-blink) and diode was blinking only when connecting to wifi network, which means once a day in the morning :)

```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for direc in /sys/class/leds/iwl-phy*X
	do
		echo none > $direc/trigger
		# never trigger blinking for TX, RX
	done
	
	for direc in /sys/class/leds/iwl-phy*radio
	do
		echo none > $direc/trigger
		# never trigger blinking for radio
	done

	for direc in /sys/class/leds/iwl-phy0*assoc
	do
		echo phy0assoc > $direc/trigger
		# do trigger blinking during association
	done
fi

```

But this method stop working after upgrading to Ubuntu 10.10. I suppose that these referenced directories (/sys/class/leds/iwl-phy*) were moved somewhere else and I don't know where.

Please help, this blinking is very distracting and work is really uncompfortable. Thanks :)

---

### Post by mistercrunch on 2010-10-12
Hi. Same problem here on a HP DV6-1050us. I had a similar fix in place but it doesn't work anymore.

My temporary fix: black electrical tape over the light.

---

### Post by laptoplinux on 2010-10-29
I had the same problem with my Dell Latitude D820.  Found the fix here:

[http://georgia.ubuntuforums.org/showthread.php?t=966511&page=9]("http://georgia.ubuntuforums.org/showthread.php?t=966511&page=9")

But I think what I did was a little different from what they said there.

Basically, I went into the file /etc/modprobe.d/wlan.conf (might have had to create it, can't rememeber), and then added the line:

options iwlcore led_mode=1

saved the file and then restarted the computer.  That fixed the light for me.

---

