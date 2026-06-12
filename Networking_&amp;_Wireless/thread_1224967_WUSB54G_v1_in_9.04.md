---
title: "WUSB54G v1 in 9.04"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by darkstarbenji77 on 2009-07-28
Im having a helluva time getting my v1 wusb54g working with 9.04. i have scoured the threads to no avail. ndiswrapper is not working. driver is installed but i dont even get the OPTION for wireless network. PLEEAASE HELP!!! thx

---

### Post by darkstarbenji77 on 2009-07-28
Help help help help

---

### Post by philcamlin on 2009-07-28
mine is detected automatically

its the silver linksys wireless usb i have it it works flawlesssly

post output of 

iwconfig:popcorn:

---

### Post by darkstarbenji77 on 2009-07-29
iwconfig gives me this
[EMAIL="benjamin@benjamin-desktop:~$"]benjamin@benjamin-desktop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
 
 
ndiswrapper -l gives me this
[EMAIL="benjamin@benjamin-desktop:~$"]benjamin@benjamin-desktop:~$[/EMAIL] ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wusb54g : driver installed
 device (1915:2234) present (alternate driver: ndiswrapper.conf)

---

