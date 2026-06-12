---
title: "Bberry and Ubuntu w/bluetooth. How to install stuff needed without net connection?"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by poiuy on 2009-08-31
I have a desktop machine running Ubuntu Feisty Fawn. I currently use my Blackberry Curve as a modem on my laptop, and want to do this on the desktop as well. The desktop does not currently have an internet connection. I have a bluetooth dongle installed, and it's there if I run lsusb, but there's no icon and was no popup or anything.

```
sudo /etc/init.d/bluetooth start
``` starts bluetooth services up fine, ```
hcitool search
``` finds all bluetooth devices around, and ```
sudo hcitool cc mac-of-blackberry
``` tries to connect to my blackberry, but can't authenticate? I have tried the default '1234' passcode, no luck.

There is no Bluetooth item in System > Preferences, and no Bluetooth option when I right click Applications and click Edit Menu, and no Bluetooth icon near the clock.

I see other posters with this problem were advices to download Blueman, or Bluez. But bluez is already installed, correct? I could download packages and things on my laptop, and put them on a CD to bring over to my desktop, but I don't know what I should download.

---

### Post by poiuy on 2009-09-01
bump it.

---

