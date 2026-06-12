---
title: "Wireless USB Adapter help in Jaunty..."
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Jonesie on 2009-04-28
I have a desktop network card (Belkin Wireless G Network Card) which works out of the box with Jaunty. I'm wanting to swap it for a Belkin Wireless G+ USB Adapter (f5d7051) and its having none of it!

i've tried just plugging it in and using network-manager and wicd with no luck they didn't detect any devices. Tried ndiswrapper (found how to do it here [http://ubuntuforums.org/archive/index.php/t-978041.html](http://ubuntuforums.org/archive/index.php/t-978041.html)). Installed ndiswrapper-utils-1.9, ndiswrapper-common, and ndisgtk. 

Installed the driver

$ndiswrapper -l command gives[INDENT]WARNING: All config files need .conf: /etc/modprob.d/oss-compat, it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprob.d/ndiswrapper, it will be ignored in a future release.

bcmusbdhd : driver installed
device (4317:0711) present

[/INDENT]$iwconfig gives[INDENT]lo no wireless extensions.
eth0 no wireless extensions.
tap0 no wireless extensions.
vboxnet0 no wireless extensions.
pan0 no wireless extensions.

[/INDENT]$ ndiswrapper -m gives[INDENT]WARNING: All config files need .conf: /etc/modprob.d/oss-compat, it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprob.d/ndiswrapper, it will be ignored in a future release.

module configuration already contains alias directive

[/INDENT]$ sudo iwlist wlan0 scan gives[INDENT]wlan0        Interface doesn't support scanning. (guess because i'm trying a USB????)

[/INDENT]So i'm stuck here and don't know what to do.

If anyone can help me out that would be great. I'm need the extra speed and signal strength! 

Cheers,
Jonesie

---

### Post by pytheas22 on 2009-05-11
I'm trying to help another user get this device working in [this thread]("http://georgia.ubuntuforums.org/showthread.php?t=1141566") (see page 11).  If you've made any progress, I'd be interested to know.

---

