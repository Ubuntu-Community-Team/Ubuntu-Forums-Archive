---
title: "Samsung N130 netbook with Realtek 8192e wireless card will not connect to any network"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by ThePieminister on 2011-01-27
Hi there, 

I recently installed ubuntu 10.10 netbook remix on a partition on my new netbook to run alongside windows 7. It worked perfectly for one day, but as soon as I applied all updates the wireless stopped working. Wireless networks will show up, however when attempting to connect to them, the wifi symbol just keeps flashing like it does when it's connecting until it times out and states "wireless networks disconnected" I've tried booting up both kernels from the GRUB, of which neither work however the wireless works absolutely fine on windows 7.

I'm aware this is a known problem to an extent, however I can't for the life of me find a fix! Hope you guys can help!



Just some added notes based on other solutions I have found that didn't work:
Yes, enable networking and enable wireless are both ticked, and yes, connect automatically is also ticked.

---

### Post by masonmouse on 2011-01-31
> **ThePieminister said:**
> 
I'm aware this is a known problem to an extent, however I can't for the life of me find a fix! Hope you guys can help!

On my computer I created a shell script containing the following:

```
#!/bin/sh
gksudo rmmod r8192se_pci && sudo rmmod r8192e_pci ; sleep 3s; sudo modprobe r8192e_pci && sleep 3s ; sudo modprobe r8192se_pci
```

and saved it as restart_network.sh into my home directory. Then I went to System > Keyboard Shortcuts and created a new shortcut to this script and associated it with Control-Alt-R so whenever my network doesn't want to connect, I just hit those keys, type my password and let it work. It usually takes a few tries to get it working but it eventually works.

My one year warranty is up this month and the day it is, I'm replacing this wireless card.

---

