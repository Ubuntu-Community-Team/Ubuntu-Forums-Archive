---
title: "wireless IntelPro 2200BG connectivity"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by tlbrueser on 2010-01-09
I recently formatted an old Dell D600 and installed 9.10 on a single partition.  It connects to my Airport just fine hardwired, but I have had no success getting the IntelPro/Wireless 2200BG card to talk wireless.  I've entered the SSID and WPA2 security ID with no success.  Any help and suggestions to get the wireless going would be greatly appreciated :-)

T

---

### Post by bkratz on 2010-01-10
> **tlbrueser said:**
> I recently formatted an old Dell D600 and installed 9.10 on a single partition.  It connects to my Airport just fine hardwired, but I have had no success getting the IntelPro/Wireless 2200BG card to talk wireless.  I've entered the SSID and WPA2 security ID with no success.  Any help and suggestions to get the wireless going would be greatly appreciated :-)

T

I believe the first thing I would try would be to temporarily remove encryption from the router and see whether you can connect or not.

if not,
You might just drop to the terminal
Applications>>Accessories>>Terminal and type in
sudo iwlist scan
(that is IWLIST in lowercase)

(this will require you to type in the password which will not echo to the screen-do it anyway and hit enter.
and see it you see any networks if not,

type in
sudo lshw -C network
(LSHW in lowercase--C is capitalized)
and copy/paste (using the code tabs # above) the output back here.

---

### Post by bkratz on 2010-01-10
Oh, and by the way are there any keys strokes or switches to turn on wireless?  Is it turned on in the bios?
You might also want to copy/paste the output from 
iwconfig too.

---

