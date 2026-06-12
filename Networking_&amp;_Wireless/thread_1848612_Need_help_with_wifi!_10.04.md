---
title: "Need help with wifi! 10.04"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by blake0812 on 2011-09-22
I need help getting wifi to work with Ubuntu! I tried to install the drivers, but it said I needed b43fwcutter. So I installed that, and i tried to install bcmwl-kernel-source but i get "Error: Dependency is not satisfiable: dkms"

Help please?

---

### Post by kooba on 2011-09-22
Try this.


[LIST=1]
[*]Removed the  Broadcom STA wireless Driver from Additional Drivers.
[*]type bcm in Ubuntu software center,
[*]Install "Installer Package for firmware for the b34 driver" (firmware-b43-installer)
[/LIST]
OR try this (worked for me)

[LIST=1]
[*]Install firmware-b43-installer (+ b43fwcutter automatically added in Synaptic)
[*]Uninstall the 'bcm-kernel-source' package using Synaptic
[*]Remove the original Wireless STA driver from Additional Drivers
[*]Reboot
[/LIST]

---

### Post by garvinrick4 on 2011-09-22
If that does not work just show us your bcm card installed so as to see what driver needed.
```
lspci -k
``````

sudo lshw -C network
```Just need the Wireless network card

---

