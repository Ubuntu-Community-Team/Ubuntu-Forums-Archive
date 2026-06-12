---
title: "Inspiron 1525 with Ubuntu 10.04"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by f00fyf00f3r on 2010-04-21
Inspiron 1525 with Ubuntu 10.04

Installed 10.04 on an inspiron 1525 and was taken aback when the wireless was not detected. Checked under hardware drivers and nothing was found. I haven't had a wireless issue in a LONG time and most (not all) of the time the driver just had to be enabled. Was surprised that I ran into it in a LTS release (and i think this may have been one of the Ubuntu Dell models?). Plugged in a lan cable and could only ping or access the modem. That was actually the cables fault. Swapped with a good one ran updates and still no wireless, still not showing up in hardware drivers.

Anyway, a post by Sam_Delta in a thread from 2 years ago helped me out. Check it out below, hopefully it works for you and you won't have to spend time searching.

> **sam_delta said:**
> broadcom should work under hardy if you activate hardware drivers under system > administration > hardware drivers.

if you find no drivers under hardware drivers, reinstall b43-fwcutter (broadcom drivers in hardy) using aptitude instead of synaptic

```
 sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter 
```
 
restart pc
 
and then go into system>adinistrator hardware drivers again, and see if they now appear

some threads about broadcom
[http://ubuntuforums.org/showthread.php?t=767143](http://ubuntuforums.org/showthread.php?t=767143)
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)
[http://ubuntuforums.org/showthread.php?t=762248](http://ubuntuforums.org/showthread.php?t=762248)

sam

original post at [http://ubuntuforums.org/showthread.php?t=772854](http://ubuntuforums.org/showthread.php?t=772854)

---

