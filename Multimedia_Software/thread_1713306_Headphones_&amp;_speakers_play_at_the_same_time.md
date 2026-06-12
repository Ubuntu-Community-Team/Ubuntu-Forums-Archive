---
title: "Headphones &amp; speakers play at the same time"
date: 2011-03-23
forum: Multimedia Software
---

### Post by madisunnyd on 2011-03-23
I'm running 10.10 on a Thinkpad SL510 laptop.
I messed about with Sound Preferences to try to fix it, and I discovered that if the connector under the output tab is set to analogue output or analogue headphones, then sound will go through my headphones but the speakers won't work even when there are no headphones plugged in. If it's set to analogue speakers, then sound plays through both simultaneously.
Isn't there any way for it to sense when headphones are plugged in and reroute the sound accordingly?
I've googled a bit and seen the same question in other places, but none of the solutions worked. But I see that I'm probably going to be asked for this, so just to save time: [http://www.alsa-project.org/db/?f=81d0df68ab76a5497cfe32ce65fe5481a4019a52](http://www.alsa-project.org/db/?f=81d0df68ab76a5497cfe32ce65fe5481a4019a52)

Thanks in advance for any help. (:

---

### Post by Yellow Pasque on 2011-03-23
This was fixed in ALSA 1.0.24:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580006](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580006)
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by madisunnyd on 2011-03-23
Works fine now, thanks! C:

---

