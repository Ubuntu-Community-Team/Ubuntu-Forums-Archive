---
title: "o2 Mobile Broadband Settings"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by lewisbrooks on 2010-12-12
Hello all,

I am currently running Ubuntu 10.04 with a Samsung N150 plus, which has a built in WWAN module.

Does anybody have a current o2 Mobile Broadband settings to share with me?

I need the settings to enable my Mobile Broadband.

Regards

Lewis

---

### Post by Hippytaff on 2010-12-12
Hi and welcome.

Is it a usb device? if so can you post the output of
```

lsusb | grep -i wire

```

with the device plugged in

---

### Post by alexfish on 2010-12-12
> **lewisbrooks said:**
> Hello all,

I am currently running Ubuntu 10.04 with a Samsung N150 plus, which has a built in WWAN module.

Does anybody have a current o2 Mobile Broadband settings to share with me?

I need the settings to enable my Mobile Broadband.

Regards

Lewis

Hi

Can have a look here if .  UK

[[SOLVED] ]("http://ubuntuforums.org/showthread.php?t=1629008&page=2")[o2 Dongle Set-up on Ubuntu]("http://ubuntuforums.org/showthread.php?t=1629008&highlight=%5BSOLVED%5D+o2+Dongle+Set-up+Ubuntu") ([IMG]http://1.2.3.11/bmi/ubuntuforums.org/images/misc/multipage.gif[/IMG] [1]("http://ubuntuforums.org/showthread.php?t=1629008&highlight=%5BSOLVED%5D+o2+Dongle+Set-up+Ubuntu") [2]("http://ubuntuforums.org/showthread.php?t=1629008&page=2&highlight=%5BSOLVED%5D+o2+Dongle+Set-up+Ubuntu"))
Try setting Network manager first with the settings :

APN: m-bb.o2.co.uk
user: o2bb
password: password

seems one device connected just by setting to the above

---

### Post by lewisbrooks on 2010-12-12
No its an embedded WWAN module

---

### Post by alexfish on 2010-12-12
your post says

which has a built in WWAN module.

how are you connecting to the computer

usb or bluetooth

also which settings are you after

Need more info as to the actual problem , which version of Ubuntu been used

alexfish

---

