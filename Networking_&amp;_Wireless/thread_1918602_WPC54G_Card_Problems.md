---
title: "WPC54G Card Problems"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by romain.astie on 2012-02-01
Hello All,

I recently installed lubuntu on my computer, and tried installing ndiswrapper, but to no avail. When I run > ndiswrapper -l the computer says that ndiswrapper is recognizing the driver and associating it to the card, but ubuntu does not seem to want to connect to my network. It still shows the two arrows, up and down, and when I click on them the menu that shows up says that the firmware is still missing. I've also tried running > sudo depmod -a
sudo modprobe ndiswrapper to try and load the module into memory, but the computer does not post any output or redirect me to another input terminal line. The commands just sit there, seemingly not executing. How can I get this driver to work?

Romain

---

### Post by romain.astie on 2012-02-01
Also, tried reinstalling driver. Now, when i put > sudo depmod -a
sudo modprobe ndoswrapper It tells me : > WARNING: All config files need .conf: /etc/modprobe.d/blacklist will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'echo'

This appeared after I reinstalled the window driver and also tried diasbling the free drivers that come with ubuntu.

---

### Post by romain.astie on 2012-02-01
SOLVED. Firmware was blacklisted in blacklist.conf.... go figure....

---

