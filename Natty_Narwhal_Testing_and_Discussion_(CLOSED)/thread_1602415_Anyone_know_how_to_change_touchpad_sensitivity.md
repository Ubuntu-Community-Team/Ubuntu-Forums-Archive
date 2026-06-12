---
title: "Anyone know how to change touchpad sensitivity?"
date: 2010-10-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by davideotape on 2010-10-21
Basically, I've got [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/416516"), which has been bugging me since I got my MacBook. I've searched high and low, but to no avail. Can anyone out there help?

I've already tried gsynaptics and pointing devices, and neither of them help.

---

### Post by ronacc on 2010-10-21
I think it under preferences>mouse , but its been awhile since I had to change sensitivity .

---

### Post by davideotape on 2010-10-23
> **ronacc said:**
> I think it under preferences>mouse , but its been awhile since I had to change sensitivity .

There is a sensitivity option under general, but it's not what I want. I want the touchpad to respond when I only press down lightly on it.

---

### Post by utilitytrack on 2010-10-23
> **davideotape said:**
> There is a sensitivity option under general, but it's not what I want.

If your touchpad uses Synaptics TouchPad driver then you must study the manual.

> [I]The sensitivity can be adjusted using the EdgeMotion parameters.
source: man synaptics(5) (shortened version) [http://linux.die.net/man/5/synaptics]("http://linux.die.net/man/5/synaptics")[/I]

---

### Post by davideotape on 2010-10-23
I've tried fiddling around with various vars in synclient, but nothing seems to change.

---

### Post by beernarrd on 2011-04-05
> **davideotape said:**
> I've tried fiddling around with various vars in synclient, but nothing seems to change.
sudo apt-get install gpointing-device-settings

---

