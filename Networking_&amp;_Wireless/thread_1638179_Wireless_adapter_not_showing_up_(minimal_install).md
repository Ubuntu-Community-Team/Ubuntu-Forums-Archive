---
title: "Wireless adapter not showing up (minimal install)"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by mrmylanman on 2010-12-05
Hey all,

I have a laptop that I don't use anymore so I figured I would use it for trying to get used to the command line in Linux.  The lspci line for my WiFi adapter is:

> 02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

When I run iwconfig to see if my adapter is getting picked up I only get an output for the loopback interface and my Ethernet port.  I installed the following packages which I thought would be enough to get it working:

> b43-fwcutter, broadcom-sta-common and broadcom-sta-source

I was able to get it working in a regular Ubuntu installation, but it doesn't seem to pick it up in this install.

Does anyone have any tips/advice?  I went with the minimal install because I wanted to see how lightweight I can get the OS.

Thanks!

---

### Post by mrmylanman on 2010-12-06
Some new information as I did some additional digging and working:

I installed the bcmwl-modaliases and bcmwl-kernel-source packages and now it shows up.  However when I run iwlist scan I get "Failed to read scan data : invalid argument"

Restarting networking does nothing to rectify this.  I did some other commands like "iwlist eth1 txpower" and it shows it is transmitting at 24dBm, so the card appears to be working.  I still cannot associate with an AP though.

Also, for what it's worth the light for WiFi is orange on my laptop (which generally means it is off, although it's apparently transmitting).

---

### Post by TBABill on 2010-12-06
Please post output of ```
lsmod | grep "b43\|ssb\|wl"
```

And try ```
sudo modprobe wl
```

---

### Post by mrmylanman on 2010-12-06
Thank you for the response.  The output of the first command is:

> wl 1959533 0
lib80211 5058 2 lib80211_crypt_tkip,wl

Sorry for the formatting, I am transcribing it from my laptop onto my desktop.

I did modprobe wl after that, and it seems to be repeating the same behavior.

---

### Post by TBABill on 2010-12-06
Output of ```
sudo rfkill list
```

---

### Post by mrmylanman on 2010-12-06
> **TBABill said:**
> Output of ```
sudo rfkill list
```

Here's the output of that command:

> 0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: no

---

### Post by TBABill on 2010-12-06
And you may have to ```
sudo apt-get install build-essential linux-headers-generic
``` and ```
sudo apt-get build-dep linux
``` then ```
sudo modprobe wl
```

Note: probably no need for doing these since we won't need to build from tar.gz if we can get your current wl driver going.

---

### Post by TBABill on 2010-12-06
Ok, soft blocked is a problem. ```
sudo rfkill unblock all
``` then ```
sudo modprobe wl
```

---

### Post by mrmylanman on 2010-12-06
You sir are a gentleman and a scholar.  Solved my problem!  I appreciate it a ton!  Marking as solved :-)

---

### Post by TBABill on 2010-12-06
Anytime!! Very glad to help and happy that you are up and running. Enjoy Ubuntu!!

---

### Post by mrmylanman on 2010-12-06
> **TBABill said:**
> Anytime!! Very glad to help and happy that you are up and running. Enjoy Ubuntu!!

Yeah I have been enjoying it through Gnome for a while now, which I'm learning makes everything just so much easier.  It worked in network manager, however I want to dive deeper into the CLI and see what else I can get going (a thread in the desktop environments forum inspired me), and network-manager wasn't so much an option then lol :-P

Thanks again!

---

