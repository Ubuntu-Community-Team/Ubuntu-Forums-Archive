---
title: "Intel WiFi 4965AGN bitrate speed always sets to 1 Mb/s"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by lf610 on 2012-04-27
The wireless internet connection is very slow because the bitrate speed for my Intel 4965AGN wireless card according to Connection Information is at 1 Mb/s. I noticed this problem is also present in LM12 Debian Edition, LM12 LXDE, and I would bet it's present in every other Ubuntu or Debian derivative. Therefore it seems like it's a bug in a bunch of Linux kernels.

If I type this in the terminal, then it fixes it to 54 Mb/s: 
```
sudo iwconfig wlan0 rate 54M
```The problem is that I have to do this every time I reboot to fix the connection speed as it reverts back to 1 Mb/s. Any ideas for a permanent fix?

EDIT:
Thanks, your new script seems to have done the trick.

---

### Post by brainwash on 2012-04-27
Simply create a new script, which will be run everytime the wlan interface changes its state from down to up (reboot, suspend,..):
```
gksudo leafpad /etc/network/if-up.d/wlan-bitrate
```

Copy and paste this:
```
#!/bin/sh

if [ "$IFACE" != "wlan0" ]; then
  exit 0
fi

iwconfig wlan0 rate 54M
```

Don't forget to make the script executable:
```
sudo chmod +x /etc/network/if-up.d/wlan-bitrate
```

---

### Post by SeijiSensei on 2012-04-27
Though it sounds like you're pretty certain your connection is slow, I recently had the experience where the ath9k_htc driver reported a 1 MBit connection speed, but the actual speed was really 54 MBit.  I discovered the problem by running a test using [http://speedtest.net/](http://speedtest.net/).  When I upgraded to the 12.04 beta, the newer driver had fixed the problem.

The 4965 card has been around for so long now that I doubt this is your problem, but I thought I'd mention here for completeness.

I do see my speeds bounce up and down quite a bit over the course of the day.  I'm guessing it has to do with interference from other APs in my neighborhood.  There are always at least half-a-dozen if not more devices visible from my system at any time.  I would suggest, if you haven't tried it yet, that you pick a different frequency channel on your router, especially if you're using the router's default.  Channels 6 and 11, in particular, are common default settings and often heavily used.  You can see which channels are being used by your neighbors by running "sudo iwlist scan".

---

