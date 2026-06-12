---
title: "Wireless mysteriously stopped working"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by eriqjaffe on 2009-05-29
The other day, my laptop just stopped detecting networks.  I'm running Openbox & Wicd on Jaunty, and that setup had worked just fine since I set the system up.

iwconfig detects my card:

```
eth1	IEEE 802.11h  ESSID:"q-home"  Nickname:"Prism I"
	Mode:Managed  Frequency:2.437 GHz  Access Point:  00:0C:41:D3:58:41
	Bit Rate:2 Mb/s  Sensitivity:1/3
	Retry short limit:8  RTS thr:off  Fragment thr:off
	Encryption key:off
	Power management:off
	Link Quality=92/92  Signal level=5/153  Noise level=112/153
	Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Wicd (both 1.5.9 and 1.6.0b3) doesn't detect any networks at all.

When I try to scan with "sudo iwlist eth1 scanning", I get:

```
eth1     Failed to read scan data : Resource temporarily unavailable
```

The darnedest thing is that sometimes, for no readily apparent reason, it **does** work.  In fact, while I was typing this post, I was able to successfully scan and connect from the terminal.  Rebooting broke it again.

Sometimes, I can manually connect by entering

```
sudo iwconfig eth1 essid q-home key <my key here>
sudo dhclient eth1
```

...but sometimes I can't.  It's the erratic nature that's the most frustrating.

The card works fine and is rock solid when I use it in a Windows laptop.  I suppose there's a chance that it's the PCMCIA slot(s) in my laptop that are the cause, but I feel that's unlikely.

If anybody has any tips, I'd appreciate it.

---

### Post by kilgore9 on 2009-05-29
I have similar problems with WICD running Hardy.  It will work fine one day, and stop working the next day.  I usually seem to be able to get it back by logging into the router once and restarting the router.  I don't know why but more often than not it works after that.  

At the wiki page for WICD ([http://wiki.ubuntuusers.de/WLAN/Wicd](http://wiki.ubuntuusers.de/WLAN/Wicd)) it shows how the /etc/network/interfaces file should look.  I noticed yesterday that my file had some other info in it.  I made my file look like the one on the wiki page and am hoping that solves it. That is my latest attempt.

But to be honest, I've been dealing with this problem for months with no success.  I can only connect wirelessly at home, wicd is shy i guess with other networks, but even at home it doesn't always work.  mysterious!

---

### Post by eriqjaffe on 2009-05-31
Well, the problem is fixed.  I'm still not quite sure what broke, although I'm pretty darn sure it was Wicd.  Wireless worked just fine from the Live CD, and a fresh install cleared things up.

Glad I keep my /home on a separate partition!  :)

---

