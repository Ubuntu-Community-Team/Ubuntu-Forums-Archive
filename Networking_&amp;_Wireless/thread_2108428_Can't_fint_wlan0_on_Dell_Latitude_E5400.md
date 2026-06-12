---
title: "Can't fint wlan0 on Dell Latitude E5400"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by rommendie8 on 2013-01-24
Hi! I've god a Dell Latitude E5400, with BackTrack 5 R1. The computer has a dell wireless 1397 wlan mini-card.

So, when I type iwconfig, wlan0 does not show at all! I am new to this, but I've red and tried to disable Netword Manager without any good.

I am wondering wether this has to do with the fireware, but don't how to find and install the right version...

Or mabye it is something else?

Thanks for the help!:D

---

### Post by Yellow Pasque on 2013-01-24
First off, Backtrack isn't technically supported here. Please use their forums in the future. I'm going to take a wild guess that you're missing the firmware (looks like Backtrack is using recent enough kernel, but don't quote me on that). You may see messages complaining about firmware in:
```
dmesg
```

If so, download the firmware for the intel5100 wlan controller from: [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware), put it in /lib/firmware and run:
```
sudo depmod -a
```

Backtrack probably has a firmware package in their repo to make things easier, but if you don't have a net connection, that doesn't help...

---

### Post by rommendie8 on 2013-01-24
Unfortunately it did not work.. and I am sorry for posting wrong.. so I have now posted it in the right forum, i think;P
Thanks

---

