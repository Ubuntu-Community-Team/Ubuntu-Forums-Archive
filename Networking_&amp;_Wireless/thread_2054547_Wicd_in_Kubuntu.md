---
title: "Wicd in Kubuntu"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by stratprof on 2012-09-07
Hello to all.

I recently installed Kubuntu 12.04 on my Dell Latitude E6420.

I'm new to KDE and have what many will no doubt think is a newbie question.

I need to connect my laptop in a university setting. The university wants us to use use its "secure" wireless network, one based upon WPA/WPA2 Enteprise and PEAP.

I have connected many Win 7 and Macs to the secure network, but the same configuration does not work on Kubuntu. I suspect PEAP is the culprit.

Wicd seems to offer a wide range of PEAP-related configuration options. I'd like to test it on Kubuntu but I'm so new to KDE that I don't know either how to install it (what's a plasmoid?) or what to remove to ensure the Wicd doesn't conflict with the network managed bundled in the distro. I'd be very grateful for related guidance.

Many thanks,

Harold

---

### Post by dargaud on 2012-10-01
Yes, wicd works better and is more reliable than the KDE network manager. And it's better to uninstall the later. I'm not sure how I did it but I remember it took a few tries. Check what is installed with something like this: ```
sudo aptitude search net | grep manag
i   network-manager                 - network management framework (daemon and u
p   network-manager-kde             - transitional package for plasma-widget-net
i   plasma-widget-networkmanagement - Network Management widget for KDE Plasma w

```
And carefully remove what may (!) not be necessary.

---

