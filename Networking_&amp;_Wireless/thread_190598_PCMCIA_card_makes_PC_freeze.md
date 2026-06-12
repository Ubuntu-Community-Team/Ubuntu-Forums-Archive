---
title: "PCMCIA card makes PC freeze"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Nonno Bassotto on 2006-06-06
I've used a US Robotics PCMCIA wireless card with ndiswrapper since Hoary without any problem. Now with Dapper I am not able to boot with the card in the slot: the system freezes at the "Configuring network interfaces" step and the only thing I can do is a manual shutdown (ctrl+c or even ctrl+alt+del won't do nothing). Otherwise my card works well. Since I sometimes forget the card in the slot and I'm not very happy to shutdown my laptop, I'm looking for a solution.
My /etc/network/interfaces looks like
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet dhcp
wireless-essid CASA

auto wlan0

```
My /etc/modules is
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod

```

Please note that:
1) If I add ndiswrapper in /etc/modules, the only result is that the system freezes at a preceding step.
2) My card is supposed to work with the acx driver, but since this does not happen I had to use ndiswrapper and add acx to the blacklist to prevent a conflict
3) Everything worked well in Breezy; I made a clean (CD) install of Dapper
4) A few hours before Dapper was final I had an upgrade of the pcmcia-cs package. Thinking that this would correct my issue, I immediately tried to reboot with the card inserted, and actually everything worked. :grin: But only that time: any later reboot failed. ](*,)
5) I have three different kernels installed (two generic 386 and a k7) and the problem happens with each one.

---

### Post by jacksonz123z on 2006-06-23
I have exactly the same problem in Dapper.   Breezy worked well.  I used ndiswrapper to install a windows driver for my Netgear WG511.v2 PCMCIA card (marvell driver).  The presence of the wireless card freezes the boot process at the Network Interface step.  I use my laptop with wireless and ethernet cable.  I discovered that if I disable eth0 with kde system settings then it all works very well!  I don't think that this will help much, but maybe the observation could throw some light on to the problem.  I will keep experimenting!

---

