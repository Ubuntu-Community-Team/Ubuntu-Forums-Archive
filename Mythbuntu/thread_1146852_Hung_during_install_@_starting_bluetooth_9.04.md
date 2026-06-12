---
title: "Hung during install @ starting bluetooth 9.04"
date: 2009-05-03
forum: Mythbuntu
---

### Post by tech.jtb on 2009-05-03
I just downloaded Mythbuntu 64bit for my Shuttle SN95G5. After booting to the CD and choosing intstall, the Mythbuntu logo appears for a few minutes, then finally starts loading. The it appears like It gets to "Loading the saved state of the serial devices..." and when it gets to loading Bluetooth it hangs. Eventually I will get a bunch of errors basically saying its timedout. I tried booting live without making changes, I downloaded 32bit and get the same result.

I was going to try to dual boot and had a windowsXP partition, but I wiped that out with a  Gparted Livecd and tried again but no luck. I tried searching the forum but couldn't find anything similar. Thanks!

---

### Post by superm1 on 2009-05-03
This is probably caused by a faulty USB device on your bus.  Try removing *all* USB devices and starting up.  If things are fine, try to narrow it down to which one.

---

### Post by tech.jtb on 2009-05-03
That was it. I thought I had unplugged everything, but I left a Linksys wireless USB adapter (WUSB54G) plugged in. Thanks!

---

