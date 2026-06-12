---
title: "Internet Sometimes Doesn't Work When Booting/Logging In"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by alsamman on 2011-01-05
Sometimes when I boot up Ubuntu or log in, the internet doesn't connect and even when I try to reconnect it doesn't work.

My computer is connected directly to the D-Link WBR-2310 router.

In order to fix this I have to unplug my router and then plug it back in.

This only happens with Ubuntu because my Windows 7 internet works when I boot that up but then when I reboot back to Ubuntu I still get the problem.

So how come the internet doesn't work sometimes on Ubuntu?

---

### Post by PatchesTheCaveman on 2011-01-05
Do you use NetworkManager (the default), wicd, or did you manually configure your connection with /etc/interfaces?

Does unplugging and plugging back in your Ethernet cable fix it or do you have to reset the router?

---

### Post by alsamman on 2011-01-07
> **PatchesTheCaveman said:**
> Do you use NetworkManager (the default), wicd, or did you manually configure your connection with /etc/interfaces?

Does unplugging and plugging back in your Ethernet cable fix it or do you have to reset the router?

Im using the default NetworkManager

and it only works when I reset the router; simply unplugging the ethernet and plugging it back in does not solve the problem.

---

### Post by alsamman on 2011-01-07
bump

---

### Post by PatchesTheCaveman on 2011-01-07
Give *wicd* a shot.  It does the same thing as NetworkManager but many find it works better.  To install it, go to Applications > Accessories > Terminal and type each of the following commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

---

