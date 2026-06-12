---
title: "Wireless broken after ndiswrapper uninstall"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2011-01-08
I recently installed ndiswrapper and decided to remove it after some kernel panics. The problem is that it overwrote something because I have the compat-wireless-backport driver installed but 'wlan0' doesn't show up anymore. I can see my wireless card when I type 'lsusb'. Any ideas on how to fix??

---

### Post by Bucky Ball on 2011-01-08
Wireless usb make and model please. ;)

---

### Post by espressobeanie on 2011-01-08
TRENDNET TEW-644UB Wireless N USB Dongle. I think it's just a line of code somewhere that needs to be added/changed. It works fine at a clean install.

---

### Post by Bucky Ball on 2011-01-08
Thought of upgrading to 10.04 LTS?

That seems to be a Ralink chipset and that shouldn't be a problem out of the box now but you need to get online with an ethernet cable. Try that now, get updates, plug in the USB dongle and see if you are offered any software (drivers, firmware) for it.

While online, go to  System >Administration >Synaptic Package Manager, search for and install 'ubuntu-restricted-extras'.

Then check System >Administration >Additional Drivers. Anything there that needs to be activated?

ps: ndiswrapper should be avoided at all costs. It is clunky, complicated, messy, and outdated. There are *very* few cards that need it now. ;)

---

### Post by espressobeanie on 2011-01-09
I have. I'm running Ubuntu 10.10 Maverick. I think I need to update my profile on that. My biggest issue is that I don't have access to ethernet at the moment. I get my wireless from a free wifi cafe next door to my place. Is there any easier way to download all of the ubuntu-restricted-extras without doing a package search and hunting and pecking thru it? I'm typing this on my unbroken Win7 partition and I am desperately trying to fix the Ubuntu wireless to get back to my Ubuntu system.

---

### Post by Bucky Ball on 2011-01-09
You don't need to hunt and peck through it. You search for ubuntu-restricted-extras, it finds that ONE package, you mark it, apply, and you're done. No needle in a haystack work required. Go to the cafe and ask if you can have half an hour on a wire.

---

### Post by espressobeanie on 2011-01-11
Ugh. It's a desktop. Yeah, it would be easy to just do a hookup to an ethernet. Gotta find a friend. But thanks. I didn't know about RALINK drivers being on ubuntu-restricted-extras.

---

