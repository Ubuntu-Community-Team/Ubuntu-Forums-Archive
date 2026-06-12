---
title: "Anyone..Got FULLY working MCE remote with 11.04 or higher"
date: 2011-10-28
forum: Mythbuntu
---

### Post by kismitt on 2011-10-28
When I used this setting below, the MCE remote would work fully then die after sleep.

REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
---------------------------------------

If I change the setting to used the kernel, then some of the buttons doesn't work and it also die after sleep

REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-Microsoft_Microsoft_IR_Transceiver_MS193YGT-event-if00"
REMOTE_LIRCD_CONF="lircd.conf"
---------------------------------------

Maybe it time to buy a new remote for mythtv.  Any suggesting?

---

