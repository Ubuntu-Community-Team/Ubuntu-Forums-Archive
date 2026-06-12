---
title: "Atheros 9170 USB based devices on 11.04"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by nbound on 2011-06-05
Trying to use these devices in 11.04 results in slow internet (~15kb/sec max), if usable at all.

**This affects all versions of 11.04** - to the best of my knowledge.

*This guide assumes the connection itself has been set-up already.*

Ubuntu loads two drivers module at boot:
[LIST]
[*]ar9170usb (old driver - 10.10 and before - soon to be deprecated)
[*]carl9170 (new driver - 11.04 - and only driver from kernel 3.0 onwards)
[/LIST]

The one we want is **carl9170**, so we must "blacklist" the other driver module so it will not run at startup.

To do this perform the following:
[LIST]
[*]Open a Terminal
[*]Type the following - ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` (or use kate/mousepad/etc. instead depending on what version of *buntu u have)
[*]Add a new line at the end of the document - ```
blacklist ar9170usb
```
[*]Save the file
[*]Close the Terminal
[*]Reboot
[/LIST]

After restart allow the connection to connect as normal. Check the driver being used in the connection information section of the network manager applet is carl9170.

If so try loading a web page, it will be much faster! (You also get access the the 802.11n speeds supported by your device - no more 54mbps max). 

The driver is still a little unstable like previous ar9170usb versions (dropouts, etc.). 

I previously found the driver module would cause my router to reboot when downloading torrents, to remedy this install:

**linux-backports-modules-cw-2.6.39-natty-generic**

via command line or synaptic, and then restart.










----------------
***_OLD:_*** **I've found torrents have a habit of killing the connection. *Any help on this would be greatly appreciated!*** Ive tried the latest firmware from Linux Wireless and it doesnt seem to have helped much, if at all - and I don't recommend newbies try this anyway. Ive seen it in both Transmission and on KTorrent, so doubt its application specific.

***_OLD:_*** ***Note**: Ive found this driver actually causes my router to turn off its wireless AP when trying to torrent, sit around for a minute or two, then it will come back up or (usually) the _entire router will reboot_(!!), works fine when using 10.10 on same pc*

***_OLD:_*** I would revert back to ar9170usb for stability, but its as slow as molasses in 11.04 :(

---

### Post by nbound on 2011-06-06
**OLD: **This may even affect standard browsing to a (much smaller) extent, will advise.

-Nope, seems ok (edit)

---

### Post by nbound on 2011-06-07
**OLD: **[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/793397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/793397)

---

### Post by nbound on 2011-06-17
**OLD: **Much improved results after installing compat-wireless-


linux-backports-modules-cw-2.6.39-natty-generic

---

