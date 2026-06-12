---
title: "No internet connection after uninstall of apps"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by HpZ on 2010-12-20
I uninstalled consolekit and with it, it uninstalled a few other applications. Now my wireless or wired connections aren't working. I also tried to change the hostname, but it changed back after a restart.

---

### Post by HpZ on 2010-12-20
Okay, so I've got wired connection working, but I don't have gnome or much of it's features anymore (I never used gnome anyway, but I think I needed gnome-network-manager or something).

help?

---

### Post by wojox on 2010-12-20
Go to System>Administration>Synaptic Package Manager and hit the search button. Enter network-manager. There are a lot of selections available.

---

### Post by HpZ on 2010-12-20
As I said, I can't get into gnome (anyway to do it through the terminal), I'm used to using DWM.

Also, I've tried nm-applet and that doesnt work either.

---

### Post by wojox on 2010-12-21
In the terminal try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

