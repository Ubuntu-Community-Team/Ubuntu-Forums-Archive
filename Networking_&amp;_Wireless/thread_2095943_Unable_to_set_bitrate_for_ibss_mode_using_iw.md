---
title: "Unable to set bitrate for ibss mode using iw"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by jlanza on 2012-12-18
Hi,

I'm using Ubuntu 12.04.1 64bit with a TPLINK TL-WN821 v3. I'm creating an adhoc/ibss network and want to change the bitrate of the network.

First of all I disable wireless from the network manager in order to be able to execute my commands.

These are the commands I execute on both ends:

```

        master$ sudo ifconfig wlan0 down
	master$ sudo rfkill unblock wifi
	master$ sudo iw dev wlan0 set type ibss
	master$ sudo iw dev wlan0 set bitrates legacy-2.4 1
	master$ sudo ifconfig wlan0 up
	master$ sudo iw dev wlan0 ibss join adhoc_linux 2462
	master$ sudo ifconfig wlan0 1.2.3.4 up
	master$ iperf -s -u -l 1472

	slave$ sudo ifconfig wlan0 down
	slave$ sudo rfkill unblock wifi
	slave$ sudo iw dev wlan0 set type ibss
	slave$ sudo iw dev wlan0 set bitrates legacy-2.4 1
	slave$ sudo ifconfig wlan0 up
	slave$ sudo iw dev wlan0 scan | less
	slave$ sudo iw dev wlan0 ibss join adhoc_linux 2462
	slave$ sudo ifconfig wlan0 1.2.3.5 up
	slave$ iperf -c 1.2.3.4 -u -b 100M -l 1472 -t 25 -i 1
```

As you can see I want to set the speed to 1 Mbps. However I don't know why I get 25Mbps which is more or less the maximun speed for 802.11g (theoretically 54 but in reality is something like 30)

Any help is more than welcome.

Regards

Edit:
I have also tried by using:
```

sudo iw dev wlan0 ibss join adhoc_linux 2462 basic-rates 1
```

But I get the same behaviour.

---

