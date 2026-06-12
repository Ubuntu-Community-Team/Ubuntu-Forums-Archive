---
title: "Help With Linksys Wireless-B Model WPC11 ver 4"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by funkadelic on 2006-04-23
I am very new to linux...

I have just installed Ubuntu 5.10 on a Dell Latitude CPt and would like to use my wireless card -- where do I start? A number of google searches have proven no help.

I have installed ndiswrapper, and manually added it to /etc/modules with no results.

No wireless connection is listed in System>Administration>Networking

Please help...

---

### Post by RoamenCota on 2006-04-26
download network manager through synaptic.  ^.^ gl

---

### Post by mpvano on 2006-04-26
Are you sure your notebook supports "cardbus" cards?
(This is DEFINITELY a CARDBUS-ONLY card and won't work in some older notebooks. Cardbus cards look just like pcmcia cards and fit the same socket but work completely differently.  Older machines don't support them, and some even confuse things by only supporting them in one socket.)

How exactly did you install ndiswrapper?
(The correct version is pre-installed with Ubuntu 5.10, if you tried any other way to install it, you may have corrupted the working version. It's possible to build one from source, but most of the FAQ instructions are full of misinformation about how to do this for Ubuntu)

How exactly did you go about configuring it?
(After you install the ndiswrapper-utils from the synaptic package manager, you need to run the executable called ndiswrapper to install a working set of windows drivers into your system)

Where did you get the windows driver file?
(There seem to be several drivers out there - I've had the best luck with the latest realtek 8180 drivers referenced from the wiki instead of the linksys drivers)

Of course, once you get the card working, you will then need to configure your networking to use it correctly, but it sounds like you're not loading the driver, or it's crashing immediately. Try the following command and post the result to find out if the driver is currently loaded:

lsmod | grep ndis

Also, have you searched the forum and ubuntu wiki for information about this card and ndiswrapper? It's been ENDLESSLY discussed before.

I've got one that works very well on my old 500 mhz Sony VAIO.

Mario

---

