---
title: "&quot;Watch TV&quot; does nothing w/o running setup first"
date: 2009-03-24
forum: Mythbuntu
---

### Post by AboveTheLogic on 2009-03-24
Hi all-

I recently configured my first mythbuntu box using a KWorld 120 tuner.

I'm using the [xc3028]("http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028") firmware, and if I go into the setup where I would configure my input devices, THEN run the front end, the card works just fine... but if I reboot, Watch TV does nothing until I go into setup again then load the front end again.

I'm not entirely sure what the problem is and am at the very beginning steps of troubleshooting. It could be as simple as how the front end and back end are starting up...that the back end needs to be started after other services or something....

If anyone has any input it would be greatly appreciated!

Thanks

---

### Post by AboveTheLogic on 2009-03-24
tried running just mythfilldatabase w/o the setup to no avail

still workin on it

---

### Post by AboveTheLogic on 2009-03-24
turns out killing and starting the back end makes it work, I found this...

[http://ubuntuforums.org/showthread.php?t=1101037](http://ubuntuforums.org/showthread.php?t=1101037)

---

### Post by AboveTheLogic on 2009-03-24
resolved thanks to mathog

---

