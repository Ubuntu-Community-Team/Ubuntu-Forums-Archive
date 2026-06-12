---
title: "Disable internal wireless card to use external wireless card?"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by rom3lol on 2011-08-06
I would like to turn off the internal wireless card since my external wireless card has better signal. Problem is if I turn of the internal card the external card turns off as well.

*_My external card is an alfa awus036h 1000w. Laptop Gateway NV53_*

How would I disable the internal card and use only my external card?

---

### Post by phoenix1/4 on 2011-08-24
Hi rom3lol, sorry no info for you I'm afraid but I'm looking to do something similar if anyone knows how!

UPDATE: Once I had confirmed that both wireless cards were working, I found the module serving the onboard wireless card and added it to /etc/modprobe.d/blacklist.conf
 After rebooting the only card that appeared was the correct one! Not the most elegant solution I realise, but certainly effective, and easily reversible by removing the module from the blacklist.

---

### Post by praseodym on 2011-08-24
You can make a little script for that:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```
Insert the following:

```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for int. WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-Stick accepted, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf [COLOR="Red"]ipw2200[/COLOR]"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick plug-out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe [COLOR="Red"]ipw2200[/COLOR]"

LABEL="rules_end"
```
save, close, and reload udev:

```
sudo service udev reload
```
Substitute the "red" driver to the one of your internal card and remove this driver from your blacklist.

---

