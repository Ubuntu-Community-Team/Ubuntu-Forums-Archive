---
title: "Samsung NP535U3C A01 wifi is disabled when coming from hibernation"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by blackwing0013 on 2012-07-20
Hi,

I have a problem with laptop, which is a Samsung NP535U3C A01. It has a Atheros AR9462 for wifi.

The problem is when I hibernate my laptop and turn it on again, the wifi is disabled when resuming from hibernate. Using rfkill, the wifi is hard blocked when resuming from hibernation. For some reason this only happens when I boot the laptop with Ubuntu. Doesn't happen on Windows.

Upon observation, it seems that during the process of putting the laptop into hibernation, there is something that causes the wifi to be hard blocked, likely switched off. Now the notebook doesn't have a switch/button for tuning on and off the wifi. It seems that the reason for this is that the BIOS remembers the state of the hardware, such as brightness levels, which hard ware was enabled or disabled, when resuming from hibernate. Somewhere during the the process of hibernating in Ubuntu 12.04 64-bit, the wifi hardware is switched off. I would like like some help to figure out how I can prevent this.  

For now, the only workaround that I know that will let me use the wifi when resuming Ubuntu is to boot another OS, like Windows 7, then reboot immediately to Ubuntu so that I can use the Wifi.

---

### Post by latitudehopper on 2012-08-29
Hi there, How else have you found Ubuntu to be on this lappy? I was thinking of getting one.  Does it run cool and quiet?

---

### Post by f0g on 2012-09-16
Hi,
I want instal xubuntu on this notebook. You have any problems, besides wi-fi?

---

### Post by michelangelog on 2013-01-22
Me too have trouble whith wireless / suspend but for me:
```
sudo rfkill unblock wifi
```
works.
So let's automate it.
```

cd /etc/pm/sleep.d
sudo vim wifix

(i, insert, then paste:)

#!/bin/sh

case "${1}" in
        thaw|resume)
                rfkill unblock wifi
                ;;
        *) exit $NA
                ;;
esac

(ESC, :wq => write and quit)

sudo chmod +x wifix

```

now on my NP535U3C, wifi is ok after suspend.

---

