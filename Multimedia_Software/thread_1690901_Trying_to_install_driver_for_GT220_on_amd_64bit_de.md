---
title: "Trying to install driver for GT220 on amd 64bit desktop"
date: 2011-02-19
forum: Multimedia Software
---

### Post by grey1beard on 2011-02-19
I'm running 10.10 on an amd64 bit desktop which, until recent problems with the screen, had a RadeonX700 256 card.
The diagnosis of that problem was video ram going awol.

I have now purchased a gt220 1G card, plugged it in and as I expected, it only gave me a resolution of 800x600 or400x300, not good for the Flatron L225WS screen that is connected(only has a vga connection).
Looking for a driver and help with the installation, I found [http://andrei.fcns.eu/2009/08/geforce-gt220-linux/](http://andrei.fcns.eu/2009/08/geforce-gt220-linux/) page, with instructions which I tried following.
I ran update manager on the desktop, then followed the link to the nividea drivers at  [ftp://download.nvidia.com/XFree86/Linux-x86_64/190.42/](ftp://download.nvidia.com/XFree86/Linux-x86_64/190.42/) which gives several packages. 
I had a quick read through the Read Me file, and clicked on the first package to download it, but (and I spotted the clue in the extension - ".run") instead of downloading, it gave me a cl type page.

Being a newbie and still well down at the bottom of the learning curve, I'd be grateful for some help.

John

---

### Post by grey1beard on 2011-02-19
I just heard a quiet bell ring , and went to Additional drivers in the System/Admin menu, and found what might be the simplest route to follow.
At this moment the desktop is downloading and installing a driver, so I may have found my own path through the undergrowth.
John

EDIT
Well it seems I'm moving up the curve a bit.
I'd previously installed "Additional Drivers" from the Ubuntu Software Centre, which installs in the System/Admin menu.
Launching that allowed it to find what I needed, and the rest is recent history.:D
I now have a resolution that fits the screen !

---

### Post by grege on 2011-02-19
If you installed the ATI driver fglrx for the old card make sure you uninstall it through Synaptic. Fglrx creates all sorts of links you no longer need and could cause issues down the track.

---

### Post by grey1beard on 2011-02-19
> **grege said:**
> If you installed the ATI driver fglrx for the old card make sure you uninstall it through Synaptic. Fglrx creates all sorts of links you no longer need and could cause issues down the track.

Thanks for that grege, I didn't know that.
Presumably there will be a drivers folder somewhere for me to find, so I'll go looking.
John

---

