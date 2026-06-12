---
title: "Ubuntu 9.10 WI-FI Connections Problem"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by grkor on 2009-11-09
I installed new version of Ubuntu: "Ubuntu 9.10 The Karmic Koala" on my Windows XP Laptop.

NetworkManager IS installed. However, it does NOT even show an option for "Wireless Networking".

Right click shown only:
"Enable Networking" (checked)
"Connection Information" (grayed out, inactive)
Edit Connections
About

"Wired"
and
"Wireless" Options are MISSING.

Left click produces only:
"Wired Network"
"disconnected" (grayed out)
VPN Connections

How can I get back "Wireless" item on the NetworkManager (Applet 0.7.996) menu to appear again(as it DID WORK before in Earlier Ubuntu Version: Ubuntu 9.04 Jaunty Jackalope - released in April 2009) to be able to establish and control access to my WI-FI home network.

Thank you!

Gregory Korzon

---

### Post by Skrip on 2009-11-12
Hello, i have the same problem with you... did you solved it?

---

### Post by Flightmare on 2009-11-12
What's your laptop brand/model?
What network card is inside it?

Probably, your driver isn't loaded. So if you can specify your network card it won't be much of a problem becouse the driver is in the kernel allready.

---

### Post by andydch on 2009-11-12
same problem
since i install karmic koala, the wifi hotspot can't detect automatically like Jaunty before

anybody has solution for this?

---

### Post by Skrip on 2009-11-13
i think this is my model of card

Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

if it is not this how can i get the Card model..

---

### Post by grkor on 2009-11-14
> **Skrip said:**
> Hello, i have the same problem with you... did you solved it?No luck. Nobody helped me yet. This is a rather nasty problem as I cannot access internet now via WI-FI anymore and had to switch back to Windows Vista... :icon_frown:

---

### Post by grkor on 2009-11-14
> **Flightmare said:**
> What's your laptop brand/model?
What network card is inside it?

Probably, your driver isn't loaded. So if you can specify your network card it won't be much of a problem becouse the driver is in the kernel allready.

Laptop is HP Pavillion tx1000, AMD Turion 64x2 Windows Vista Home Premium.

WI-FI Card is:

Broadcom 4321 AG 802.11 a/b/g draft-n WI-FI Adapter
Windows Driver: Broadcom v. 5.10.38.26 dated 10/22/08

How do I make Ubuntu 9.10 "recognize"/"find" my network card after all?

---

### Post by drewsus on 2009-11-14
Try connecting to your router with an Ethernet cable then go to Menu -> System -> Admin -> Hardware Drivers, and then enable your broadcom driver
Disconnect your Ethernet cable and have a go at wireless. 
Might have to restart, but most likely not (and actually, in regards to wireless problems I find it better to shutdown and then turn it on rather than restart).
Let me know if that helps.
dRewsus

---

### Post by Skrip on 2009-11-15
I have tried that but it not found any drivers even not for my nvidia as it did in previous versions of ubuntu...

---

### Post by Dale61 on 2009-11-15
I was experiencing a similar problem - happily surfing, then after x amount of time, wireless connection would drop out, unable to reconnect unless I rebooted - but have found (hopefully) a solution in another thread.

[http://ubuntuforums.org/showthread.php?t=1326114]("http://ubuntuforums.org/showthread.php?t=1326114")

Refer post #6.

---

### Post by Skrip on 2009-11-15
> I have made the experience that uninstalling that crappy network-manager and installing wicd instead solved all wireless problems.

You mean this solution? and if yes... can you tell step by step how to do that...

---

### Post by Skrip on 2009-11-15
Well how can i install WICD ??

---

### Post by panvorax on 2009-11-15
I'm trying to get 9.10 onto my toshiba P300 and wireless is out of action in much the same way as the many posters here have described. Strangely, when I load the live CD on my toshiba A300 it works just fine.
 I ditched vista on the P300 because it was as buggy as a can of cockroaches. The A300 still runs vista with no issues. Does this mean my hardware to blame for the failure of karmic to find wireless connectivity? Jaunty works fine on the P300. I'm happy to stay with Jaunty but the cloud is of interest and I'd love to give the Koala a go.

---

### Post by Dale61 on 2009-11-15
> **Skrip said:**
> Well how can i install WICD ??

I installed it via Ubuntu Software Centre.

I then unchecked the box for Network Manager in Startup Applications.

I then rebooted, and so far, all is sweet.

---

