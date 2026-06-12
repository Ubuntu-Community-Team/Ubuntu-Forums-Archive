---
title: "Flash 10 Update not found by Firefox, works fine with Opera"
date: 2011-03-12
forum: Multimedia Software
---

### Post by ortenauer on 2011-03-12
Hello,

title says ist all: downloaded and installed the current FP-DEB from Adobe and installed it via GDebi.

Result: Firefox (3.6.15) doesn't play any videos anymore (shows "need to upgrade...")

But: the FP is installed properly, as seen by Opera using it just fine.
Any ideas how to tell Firefox where to find it?

I have found '/opt/firefox/plugins/flashplugin-alternative.so' 
and I have copied it as '/opt/firefox/plugins/libflashplayer.so' 
to no avail.

BTW: This is Ubuntu 8.10 ... so no using the repositories any more :-(

LG
Axel

---

### Post by lovinglinux on 2011-03-13
Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by ortenauer on 2011-03-13
> **lovinglinux said:**
> Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

Thanks a lot - I'm sure this will be useful in the future - this time I was impatient and tried the "universal solution" (Windows style...) - removed Firefox + Flashplayer and reinstalled both. Still don't know what was wrong, but it works now :-)

Thanks again
LG Axel

---

