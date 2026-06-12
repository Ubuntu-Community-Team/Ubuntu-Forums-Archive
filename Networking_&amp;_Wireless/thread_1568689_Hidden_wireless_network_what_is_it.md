---
title: "Hidden wireless network: what is it?"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by ANew on 2010-09-05
Can anybody give a clue what the network is it:

SSID:  00:00:00:00:00:00
Name:  "<hidden>"

it is shown only in "iwlist" output and only with
usb wifi adapter (not shown with internal atheros card).

????:confused:

---

### Post by ANew on 2010-09-09
Nobody replied :(

---

### Post by kerry_s on 2010-09-09
it's just what it says, the router is setup to not broadcast it's name.
mine is setup that way.

---

### Post by ANew on 2010-09-10
What pussles me is that this network is visible only with
usb wifi adapter, with internal atheros card it never
shows up.

Any ideas about this?

---

### Post by walt.smith1960 on 2010-09-10
> **ANew said:**
> What pussles me is that this network is visible only with
usb wifi adapter, with internal atheros card it never
shows up.

Any ideas about this?

Do you have "broadcast SSID" turned off on your router?  If you do, that network should not show up without special software.  Once I have typed my SSID and password, network manager will remember it.  I can then open network manager, click on "Connect to hidden wireless network", then click on "connection" and the top box.  My hidden wireless network is listed because I've logged onto it previously.  I hope this is what you're asking about.

---

### Post by bkratz on 2010-09-10
> **ANew said:**
> What pussles me is that this network is visible only with
usb wifi adapter, with internal atheros card it never
shows up.

Any ideas about this?

Could it be that the usb wireless card simply has a better receiver than the internal, or the internal's antenna is disconnected or the polarization of the signal is simply vertical and the internal cards antenna is in a different plane?

---

