---
title: "nm-applet errors"
date: 2010-11-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-11-30
get lot of warnings logged into xsession-errors:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/683108](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/683108)

*** vote: affect me too, if you have the same issue, please

---

### Post by MacUntu on 2010-11-30
Not to worry. ;)

> <htorque> cyphermox, are you aware of those messages from nm-applet (the indicator one from the PPA): [http://paste.ubuntu.com/538279/](http://paste.ubuntu.com/538279/) - i get those three 1000+ times per hour in my .xsession-errors
<cyphermox> htorque, yes, I am
<cyphermox> those actually don't come from nm-applet but from libappindicator :/
<htorque> cyphermox, is this related to the possible mem-leak bug you opened?
<cyphermox> htorque, might be
<cyphermox> I'm still working on fixing those through re-working the way the menus get built

---

### Post by dino99 on 2010-11-30
> **MacUntu said:**
> Not to worry. ;)

according to: [http://live.gnome.org/NetworkManager/SystemSettings](http://live.gnome.org/NetworkManager/SystemSettings)

" Configuration

By default, the system settings service is configured through the /etc/NetworkManager/nm-system-settings.conf (NM 0.7 and 0.8.0) or /etc/NetworkManager/NetworkManager.conf (NM 0.8.1 and later) file, which may be changed through use of the "--config=" argument for either nm-system-settings (NM 0.7) or NetworkManager (NM 0.8). This file must contain a "[main]" section that has at least one configuration option: "plugins". "

---

### Post by MacUntu on 2010-11-30
I'm afraid I don't understand what you're trying to tell me. :)

---

