---
title: "mythbuntu hard freezes"
date: 2011-10-16
forum: Mythbuntu
---

### Post by veehexx on 2011-10-16
i've been using mythbuntu 10.04 for a while, and every so often, it will hard freeze.

pings do not response, and i have to press the power off/reset button.

in the past, i know the 'network-manager' has caused this issue when it comes out of suspend, so i've added that to a sleep.d script.

however, the problem still seems to be present; every 20th resume, my install just locks up.
the 'every 20th resume' is an approximation wich equates to about once a week..

mythbuntu 10.04 is running the the iso-supplied kernel (due to TV Tuner card driver issues), however all other packages have been updated around 3weeks ago.

how should i proceed to work out where the issue lies now? is there some sort of log i can check. bear inmind that i need to check it after a reboot, so dmesg would be useless.

thanks for any help

---

### Post by azmyth on 2011-10-16
I'm running 10.04 and I was having the same issue. Mine was related to using a wireless USB device. Once I went hardwire to the router, it went away.

---

### Post by veehexx on 2011-10-17
thats not the issue - no wifi devices.
the only USB device is an 'MCEUSB' module.

just to be clear, it's only occurs within a few moments of resume. if it doesnt hard lock, then it can and will stay running for hours.

it just seems to be something not liking wakeup all the time.

is there something like dmesg that can show logs, other than the 'most recent' that dmesg shows?

---

### Post by nickrout on 2011-10-17
/var/log

---

