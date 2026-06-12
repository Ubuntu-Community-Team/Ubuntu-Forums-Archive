---
title: "Speakers play only when headphones are plugged in"
date: 2015-01-05
forum: Multimedia Software
---

### Post by scott83 on 2015-01-05
Hey guys, I looked around but could not see a problem quite like mine.

I get no sound from the speakers unless I have headphones plugged. When they are plugged in, no sound comes from the headphones.

I checked under Sound Settings, under "Play sound through". When the headphones are plugged in, it says it's playing though the speakers. When the headphones are out, it says the headphones are plugged. So some how, these are switched around. How can I go about correcting this?

I'm using Ubuntu 14.04.

Thanks in advance.

---

### Post by mörgæs on 2015-01-06
Hi,welcome to the fora.

This and similar problems have haunted Buntu for some time. Have you tried if it's better in a live boot of 14.10?

---

### Post by Yellow Pasque on 2015-01-09
If it was me, I'd probably try the latest ALSA module/driver: [https://duckduckgo.com/l/?kh=-1&uddg=https%3A%2F%2Fwiki.ubuntu.com%2FAudio%2FUpgradingAlsa%2FDKMS](https://duckduckgo.com/l/?kh=-1&uddg=https%3A%2F%2Fwiki.ubuntu.com%2FAudio%2FUpgradingAlsa%2FDKMS)

If it's still not working after reboot, there's a utility you can try to see what's happening at a lower level (hda-jack-sense-test). It's available through this PPA: [https://launchpad.net/~diwic/+archive/ubuntu/hda](https://launchpad.net/~diwic/+archive/ubuntu/hda)

---

