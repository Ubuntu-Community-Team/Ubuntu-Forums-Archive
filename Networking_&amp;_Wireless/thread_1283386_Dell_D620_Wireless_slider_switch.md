---
title: "Dell D620 Wireless slider switch"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by daevski on 2009-10-05
Hey all,

I'm installing 9.04 (jaunty) on my girlfriend's laptop, which is a Dell Latitude D620. First thing I want to make sure is working is the wireless, but it doesn't seem to be setup after OS install.

There is a hard switch on the side of this laptop, but sliding (and holding) the switch does nothing, it seems.

(sudo) lshw shows that it sees the card:

id:    
network
description:     Wireless interface
product:     PRO/Wireless 3945ABG [Golan] Network Connection
vendor:     Intel Corporation
physical id:     
0
bus info:     
pci@0000:0c:00.0
logical name:     
wmaster0
version:     02
serial:     00:18:de:29:4d:bc
width:     32 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    iwl3945
latency    =    0
module    =    iwl3945
multicast    =    yes
wireless    =    IEEE 802.11abg

Can anyone help me out with this, to get the wireless card working? :)

---

### Post by daevski on 2009-10-05
I'm an idiot. The wireless icon is up on the panel, it just wasn't connected because I'm in an encrypted network..... [slaps forhead]

---

