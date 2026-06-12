---
title: "Wirelesss problems using  kubuntu 9.04"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by jcook23 on 2009-09-14
[B]Configuration:
Wireless Device -- NETGEAR WNDA3100
NDISwrapper -- NOT installed
Operating System -- KUBUNTU 9.04 (with KDE 4)
NO Internet Connection, but I do have a 2GB USB JumpDrive

[/B]Greetings all,

I've wrestled with this since yesterday and last night I was FINALLY able to get my wireless adapter (WNDA3100) to be recognized by Kubuntu using the AR9170 driver, and using the steps listed in the thread below:

[http://ubuntuforums.org/showthread.php?t=1150835](http://ubuntuforums.org/showthread.php?t=1150835)

The problem now is that even tho I've got the device recognized and the Wireless tab in KNetworkManager now enables me to add a new Wireless Network, NOTHING happens! I've attempted to put the settings for my wireless network into the Manager, but it just sits there and looks at me.

Here's more or less what it looks like:

* lsusb : shows the Netgear, Inc as it should.
* iwconfig : shows an output for wlan0 that looks normal.
* sudo iwlist scan : DOES show a scan of all available wireless networks, including my own.
* nm-system-settings.conf : currently shows "ifupdown: managed=false" (but I can change that if you think it's relevent)

The network I'm attempting to connect to is a secure (WPA) network, but like I've said, I can't seem to get the KNetworkManager to connect to it.

Anyone have any suggestions? I'm at my wits end. I'll try anything.

---

### Post by AvixK7 on 2009-09-25
I'm getting the same problem, I connect to my wireless network no problem with Gnome. But with KDE 4.3 (jaunty), Knetworkmanager lets me add wireless connections (even gives me the signal strength) but refuses to connect once I input and save the connection info.

Thanks for your time :)

---

