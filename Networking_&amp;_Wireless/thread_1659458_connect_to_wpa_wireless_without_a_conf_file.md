---
title: "connect to wpa wireless without a conf file"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by pokeyThePenguin on 2011-01-04
I'm interested in learning how to start a wireless connection via the terminal rather than the NetworkManager applet. Every resource I've found on this subject talks about how you need to make a .conf file, then use wpa_supplicant. Is there a way to establish the connection without having to a create any file whatsoever? What are the steps for establishing the connection?

From what I've read, establishing a WEP connection is as simple as calling iwconfig and then dhclient. Are there similar steps for WPA2?

---

### Post by PatchesTheCaveman on 2011-01-04
This is not possible.  You must create a wpa_supplicant.conf file with the WPA configuration.

The complexity* of the WPA mechanism is such that any command line process for configuring WPA would be extremely complex and need to be repeated quite frequently.  Thus its better suited to a configuration file.

*Yes, for most of us it's just a password (technically a "pre-shared key") but WPA-Enterprise presently has eight different certified authentication protocols that Linux must support.

---

### Post by iponeverything on 2011-01-04
PatchesTheCaveman is right, though there is a tool to manipulate Network Manager from the command line. 

google around for cnetworkmanager.

also, setting up the configuration file for wpa_supplicant is not hard.

---

