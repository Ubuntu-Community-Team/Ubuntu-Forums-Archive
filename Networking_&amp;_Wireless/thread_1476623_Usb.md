---
title: "Usb"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by zerobytes2003 on 2010-05-08
I prefer not to add to the posts when there is so much out there but I have been searching these forums for the last two days and can't seem to find the answer to this question.  I'm thinking it's got to be something simple that I'm just missing.  

I'm running a brand new install of Lucid and trying to get a usb Netgear MA101 to work.  Here's what has happened so far:

At first, the card was not recognized at all and there were no wireless options in the Network Manager Applet

After fiddling with ndiswrapper from the live cd I got the two xp drivers installed (netm101a and netm101r)

After restarting the system wireless options were added to Network Manager Applet but continue to be greyed out except for "create a wireless network" and "connect to a hidden network."  Neither of which will connect to an existing network.
lsusb shows the network card correctly connected
ndiswrapper -l shows the drivers and the device is present
dmesg shows the driver (netm101a) driving the device accurately

How do I get the list of available wireless networks and connect to mine?  I have a dualboot of xp that will find it just fine :(  It's like everything is working it's just not shooting out into space to find the available networks.  Obviously, I'm not so hot with networking which has made my conversion to linux a long rough road...Thanks in advance for any help.

zb2k3

---

### Post by zerobytes2003 on 2010-05-08
So I uninstalled everything and then reinstalled everything.  Tried each of the two drivers individually and reset my system a couple times.  One of the times I reset it something must have clicked because now I get all of the available wireless networks in the applet dropdown.  

Unfortunately, I'm still stymied because it won't connect to any of the networks.  It pulls up everything like I should be able to connect but after entering my WEP key it just searches and searches until it fails.  I know it's not the router or the card because my Windows boot (and other windows machine) work fine as well as my 9.04 eeebuntu netbook (which I'm writing this on).  Any ideas?

---

