---
title: "Atheros AR5006EG suddenly stops working"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by missingno on 2010-12-19
After a while, my connection suddenly drops and I'm no longer able to see any networks or anything. The only way I can regain my connection is to reboot over time this happens, which is a pain. I've searched around and can't find any fix for this card.

---

### Post by missingno on 2010-12-19
bump, anyone?

---

### Post by missingno on 2010-12-19
Argh, this is getting incredibly frustrating. Does anyone know what the deal with this chipset is all of a sudden?

---

### Post by missingno on 2010-12-20
Sigh, bump.

---

### Post by missingno on 2010-12-21
Another day, another bump. The frequency with which I have to reboot is getting worse and worse.

---

### Post by zoniq on 2011-01-03
Same problem here. No solution, yet :-(

---

### Post by WthIteh on 2011-01-03
> **zoniq said:**
> Same problem here. No solution, yet :-(
I don't know that specific kind of hardware.
But you could reset it easier without rebooting whole of OS.
Instead use:
```
sudo /etc/init.d/networking restart
```

Also take a look at output of
```
dmesg
```
maybe there was some clues.

---

### Post by PatchesTheCaveman on 2011-01-03
Hey guys.  Go to Applications > Accessories > Terminal on your top panel, and type in each of these commands, pressing Enter after each one:
```
lspci -v
lshw -C network
sudo iwconfig
ifconfig -a
uname -r
```

Then, copy/paste what appears into a reply to this thread.  With that information, we should be able to see what's going on.

---

