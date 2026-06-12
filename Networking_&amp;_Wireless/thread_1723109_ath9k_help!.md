---
title: "ath9k help!"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by hego555 on 2011-04-06
Hello, so im using a GUI for aircrack, the GUI is wepcrack, I like this because it is fast and easy, anyways
so, when i am attacking a wifi for packets, only broadcast works,
the 3 others 
ArpReplay
chopchop
fragmentation

don't work but each give this error


```
1:58:25 PM:Error:Could not retrieve channel of monitor interface!
Your probably have to patch your drivers.
See here: http://aircrack-ng.org/doku.php?id=compat-wireless&s#compat-wireless
```

So i searched on the internet, and i found that i have to update my wireless driver. I think I do.

So here is my wireless info

Interface	Chipset		Driver

wlan0		Atheros 	ath9k - [phy0]

i cant find a way to update the ath9k driver :(

Can someone give me a easy to follow tutorial, because a lot of places are saying kernel, and i have no idea how i do anything with the linux kernel!

So in conclusion do i have to patch, or update the driver.

Also can someone help me do it?

Thanks!

---

### Post by walt.smith1960 on 2011-04-07
Is this a USB device or PCI device?  If USB, you could try Vagrale13's deb package on source forge.  Myself and others have used it with success to install a Netgear WNA1100 which is ATH9K based. Using it is a 2 step process.  The first step is to install the .deb file using the gdebi installer or Ubuntu Software Center.  The second step is to click on Applications-system tools-Ath9k installer.  Be patient, it takes several minutes.  If your device is PCI, this won't work AFAIK.

ihttp://sourceforge.net/projects/ath9k-htc/files/

A caution--installing this may disable any other wireless adapters.  Removing the installer via synaptic or Ubuntu Software Center restored the other wireless adapters.  You may find that Natty supports your ath9K device from the install, no additional software or tweaks needed.

---

